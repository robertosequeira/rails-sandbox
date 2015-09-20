# rails-sandbox

Purpose of this repo is to track changes added while doing some experiments related to rails features and tools regularly used at the Rails ecosystem.

~~By now the site is hosted at a $5/mo DigitalOcean VPS and can be accessed at [rails.roberto-sequeira.com](http://rails.roberto-sequeira.com)~~

By now the site is hosted at a Heroku free Dyno and can be accessed at [rails.roberto-sequeira.com](http://rails.roberto-sequeira.com) or at [rails-sandbox-app.heroku.com](https://rails-sandbox-app.herokuapp.com/)


## Contents

* [Tools](#tools)
* [DigitalOcean server configuration](#digitalocean-server-configuration)
* [Moving to heroku](#moving-to-heroku)
* [TODO](#todo)


## Tools

1. Puma (https://github.com/puma/puma)
2. [Capistrano](#capistrano) (https://github.com/capistrano/capistrano)
3. [Dotenv](#dotenv) (https://github.com/bkeepers/dotenv)
4. [Devise](#devise) (https://github.com/plataformatec/devise)
5. [MailCatcher](#mailcatcher) (http://mailcatcher.me/)
6. [mailgunner](#mailgunner) (https://github.com/timcraft/mailgunner)

### Capistrano

The initial objective of this repo was to get a rails app deployed by using Capistrano. Once I achieved that objective I decided to move the app to heroku since there I don't have to pay for the hosting service so I can keep the app alive to test some other tools.
All Capistrano configuration was done following a DigitalOcean tutorial which can be found at [DigitalOcean server configuration](#digitalocean-server-configuration).

### Dotenv

I added this gem because I wanted a easy way to manage environment variables at my VPS.
After I moved the app to Heroku it's not used at the server but I keep using at my dev environment.

Variables declared at `.env` file are initialized when the application starts ant then any variable and can be accessed by `ENV["VAR_NAME"]`. 
Example file [.env.example](.env.example)

### Devise

All the authentication magic.

* User registration
* User authentication
* Password reset

### MailCatcher

What a surprise when I found this gem. I took me a couple of minutes to have a local SMTP server which catches all messages sent by the app and even gives me a UI to check sent emails.

To start the service:

```
$ mailcatcher
```

### mailgunner

This gem as it's author says is:

> A Ruby wrapper for the Mailgun API.

I use mailgun as delivery method at the production server
```
config.action_mailer.delivery_method = :mailgun
```

## DigitalOcean server configuration

Initialy this application was hosted at a DigitalOcean VPS where I configured a empty Ubuntu server up to the point where it was able to execute the application and receive Capistrano deploys.

Some of the server features and tools:
* SSH access by using a non root user with sudo access
* Puma
* Postgres
* Capistrano

**Server configuration tutorials**

  1. [Initial Server Setup with Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04)
  2. [Additional Recommended Steps for New Ubuntu 14.04 Servers](https://www.digitalocean.com/community/tutorials/additional-recommended-steps-for-new-ubuntu-14-04-servers)
  3. [Deploying a Rails App on Ubuntu 14.04 with Capistrano, Nginx, and Puma](https://www.digitalocean.com/community/tutorials/deploying-a-rails-app-on-ubuntu-14-04-with-capistrano-nginx-and-puma)
  4. [How To Use Roles and Manage Grant Permissions in PostgreSQL on a VPS](https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2)
  5. [How To Add Swap on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)

## Moving to Heroku

I decided to move the app to Heroku mainly because after I was able to configure Capistrano to deploy to a VPS there is no point on keeping that server alive. 
I found Heroku provides a really convenient service for what I want from now on for this app.

## TODO:

1. OAuth - Omniauth
2. Authorization - https://www.ruby-toolbox.com/categories/rails_authorization
  * CanCanCan - https://github.com/CanCanCommunity/cancancan
  * Pundit - https://github.com/elabs/pundit
3. Better Errors - https://github.com/charliesome/better_errors
4. We'll see

### Review

* https://www.ruby-toolbox.com/
* https://infinum.co/the-capsized-eight/articles/a-gem-for-every-occasion-11-great-ruby-libraries-we-use-on-every-project
