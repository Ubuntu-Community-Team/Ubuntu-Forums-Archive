---
title: "Error with new ROR project"
date: 2011-05-29
forum: General Help
---

### Post by kyleouellette on 2011-05-29
Hello,

I am getting this error when trying to create a new rails project:

/home/kyle/.rvm/rubies/ruby-1.9.2-p180/lib/ruby/site_ruby/1.9.1/rubygems.rb:900:in `report_activate_error': Could not find RubyGem activesupport (>= 0) (Gem::LoadError)
	from /home/kyle/.rvm/rubies/ruby-1.9.2-p180/lib/ruby/site_ruby/1.9.1/rubygems.rb:248:in `activate'
	from /home/kyle/.rvm/rubies/ruby-1.9.2-p180/lib/ruby/site_ruby/1.9.1/rubygems.rb:1276:in `gem'
	from /usr/share/rails-ruby1.8/railties/lib/rails_generator.rb:31:in `rescue in <top (required)>'
	from /usr/share/rails-ruby1.8/railties/lib/rails_generator.rb:27:in `<top (required)>'
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from /usr/share/rails-ruby1.8/railties/bin/rails:14:in `<main>'




I am using RVM, ruby 1.9.2, rails3 on ubuntu 11.04

---

### Post by linuxinstalledfromhdd on 2011-05-29
Did you ever receive this specific kind of error using 10.10, or are you completely new to 11.04? :)

---

### Post by kyleouellette on 2011-05-30
New to ruby on ubuntu. New to Ruby completely actually. :)

---

### Post by linuxinstalledfromhdd on 2011-05-30
Well I don't use Ruby, and I wish I could help you with this.

We'll just keep bumping it until maybe someone knows.. :) 

BUMP

---

### Post by kyleouellette on 2011-05-30
I think it's an issue with rvm because when I'm not using rvm and revert back to 1.8.7 and rails 2, I can make a project no problem. Guess I'll just uninstall rvm and start over? We'll see!

BUMP :D

---

### Post by kyleouellette on 2011-05-31
So I removed RVM and reinstalled it. Once I did that I installed 1.9.2-p180. Once I did that I used "rvm gem install rails" and everything went through.

---

