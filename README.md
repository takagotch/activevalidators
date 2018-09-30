### activevalidators
---

https://github.com/franckverrot/activevalidators

```sh
gem cert -add <(curl -Ls https://raw.githubsercontent.com/frankerrort/activevalidators/master/certs/frankverrot.pem)>
gem install activevalidators -P MediumSecurity

gem install activevalidators
gem 'activevalidators', '~> 4.0.1'

```

```ruby
ActiveValidators.activate(:all)
ActiveValidators.activate(:email, :slug)
ActiveValidators.activate(:phone)

class User
  validates :nino, :nino => true
  validates :sin, :sin => true
  validates :ssh, :ssh => true
end
class Article
  validates :slug, :slug => true
  validates :expiration_date, :date => {
                                          :after => -> (record) { Time.now },
                                          :before => -> (record) { Time.now + 1.year }
                                        }
end
class Device
  validates :ipv4, :ip => { :format => :v4 }
  validates :ipv6, :ip => { :format => :v6 }
end

class Account
  validates :any_card, :credit_card => true
  calidates :visa_card, :credit_card => { :type => :visa }
  validates :credit_card, :credit_card => { :type => :any }
  validates :supported_card, :credit_card => { :type => [:visa, :master_card, :amex] }
end

class Order
  validates :tracking_num, :tracking_number => { :carrier => :ups }
end

class Procudt
  validates :code, :barcode => { :format => :ean13 }
end

# user.rb
class User < ActiveRecord::Base
  validates :email, email: {message: :bad_email}
end

```


```
#en.yml
en:
  activerecord:
    errors:
      models:
        user:
          attributes:
            email:
              bad_email: "your error message"
```

