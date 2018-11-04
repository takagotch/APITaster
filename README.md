### APITaster
---
https://github.com/fredwu/api_taster

```
gem 'api_taster'

```

```ruby
Rails.application.routes.draw do
  mount ApiTaster::Engine => "/api_taster" if Rails.env.development?
end

# lib/api_tasters/routes.rb
if Rails.env.development?
  ApiTaster.routes do
    desc 'Get a __list__ of users'
    get '/users'
    post '/users', {
      :user => {
        :name => 'Fred'
      }
    }
    get '/users/:id', {
      :id => 1
    }
    put '/users/;id', {
      :id => 1, :users => {
        :name => 'Awesome'
      }
    }
    delete '/users/:id', {
      :id => 1
    }
  end
end

ApiTaster.route_path = Rails.root.to_s + "/app/api_tasters"

ApiTaster.global_headers = {
  'Authorization' => 'Token token=XXXXXXXXXXXXX'
}
ApiTaster.routes do
end

ApiTaster.global_params = {
  :version => 1,
  :auth_token => 'XXXXXXXXXX',
}
ApiTaster.routes do
end
```

```
desc 'Get a __list__ of users'
get '/users'
get '/users', {}, { :meta => 'data' }
```
