# README

This ReadMe File tells how to install Devise and use it on Rails for authentication.
Reference:
https://hackernoon.com/using-devise-in-your-ruby-on-rails-application-a-step-by-step-guide-m92i3y5s

Here are the steps:

* Add devise to your Gemfile:
gem 'devise'

* Run Bundle Install
bundle install

* Install devise
rails generate devise:install
You can see some instruction after running the command above.

* The first instruction 
The first instruction is referring to the mailer settings. For a dev
environment, you need to specify the default URL. This won't give you
any trouble if you are not going to send mail to your users, but let's
copy and paste the line on the config/environments/development.rb:

config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

* The Second Instruction
this instructs us to define a root_url to something. Leave it for later

* The Third Instruction
This instructs us to ensure we have flash messages on our app/views/layouts/application.html.erb .
This will let the user know what they did wrong. Default messages are already
included on the devise gem so you don't have to write them. Just copy paste
and show it wherever you want.

 <p class="notice"><%= notice %></p>
 <p class="alert"><%= alert %></p>

* The Fourth Instruction
Here it's telling us to generate the views of the devise for customization.
We will run the command now and modify later:

rails generate devise:views

Great, now it's time to generate the model. Here I will name it "User"

rails generate devise User

Before do the migration, let's check the migrate file first. Here you can
uncomment the line that you want in the database. For example if you enable
the confirmable part, it will make user confirm the email first before
account activation.

Okay here is how to add new field for the devise. For example we will add
first and last name for the user. We will use the same model devise created
to add any fields you wish but we will modify it later.
Run this migrate command to do that:

rails generate migration add_name_to_users name:string surname:string

Let's check again the migration file before migrate it. If everything seems good,
run either of this command to migrate it:

rails db:migrate

or

rake db:migrate