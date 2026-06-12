---
title: "Install Ruby on Rails - Lucid Lynx"
date: 2010-04-20
forum: General Help
---

### Post by vcool on 2010-04-20
[B]Install Ruby on Rails - Lucid Lynx 10.04

[/B]**Step 1 &#8211; System update**
```
sudo apt-get update
sudo apt-get dist-upgrade
```  **Step 2 &#8211; Install Ruby and friends**
```
 sudo apt-get install ruby  ruby-dev  libopenssl-ruby1.8 irb ri rdoc
``` Now we have ruby installed on our system, next we&#8217;re going to install  the database server.
 [B]
Step 3 &#8211; Install Mysql / SQLite[/B]
 You can skip this step if you have Mysql or sqlite installed on your  system.
```
 sudo apt-get install mysql-server  sqlite3 libmysql-ruby
```  **Step 4 &#8211; Install Development Header**
 Before you can install ruby gems, you will need to install  development headers. Some of gems (like mysql) needs development header  when building native extension process.
 ```
 sudo apt-get install build-essential  libmysqlclient-dev libmysql-ruby libsqlite3-ruby libsqlite3-dev
```  **Step 5 &#8211; Install Ruby gem**
 We&#8217;re going to use rubygems from [http://rubygems.org](http://rubygems.org)
```
 wget  [http://production.cf.rubygems.org/rubygems/rubygems-1.3.6.zip](http://production.cf.rubygems.org/rubygems/rubygems-1.3.6.zip)
unzip rubygems-1.3.6.zip
cd rubygems-1.3.6
sudo ruby setup.rb

``` in just fews seconds you should see this output :
```

RubyGems installed the following executables:

/usr/bin/gem1.8
``` next, create symlink 
 
```
sudo ln -s /usr/bin/gem1.8 /usr/local/bin/gem
```  **Step 6 &#8211; Install Rails with MySQL support**
```
 sudo gem install rails  mysql sqlite3-ruby mongrel
```  **Step 7 &#8211; Test drive your Rails installation**
```
rails my_blog

cd my_blog

rake db:create

rake db:migrate

script/server

browse to [http://localhost:3000]("http://localhost:3000/")

```DONE

reference :

[LIST]
[*][http://ignitedtutorials.com/2010/04/how-to-install-ruby-on-rails-on-ubuntu-lucid-lynx-10-04-lts/](http://ignitedtutorials.com/2010/04/how-to-install-ruby-on-rails-on-ubuntu-lucid-lynx-10-04-lts/)
[*][http://guides.rubyonrails.org/](http://guides.rubyonrails.org/)
[/LIST]

---

### Post by nbv4 on 2010-05-11
thanks for this

one question though, why compile rubygems from source? Why not use the one in the repos?

---

### Post by vcool on 2010-05-11
to make sure that you have the latest ruby gem version

---

### Post by DRainCode on 2010-05-12
thanks it's worked dude!!!

---

### Post by lvnilesh on 2010-06-05
Thank you for clear instructions that work without fail.

---

### Post by bubuzzz on 2010-06-11
i got a lot of "No definition... " on terminal during installation. Is it still ok ?:confused:

---

### Post by vcool on 2010-06-23
> **bubuzzz said:**
> i got a lot of "No definition... " on terminal during installation. Is it still ok ?:confused:

its ok .. thats documentation stuff 
try to install ri and rdoc

```
sudo gem install ri rdoc
```

---

### Post by AlexHamilton on 2010-07-04
I am trying to uninstall ruby, so that I can start again following the instructions above.  I've tried:
> sudo apt-get remove ruby
and manually removing the relevant parts, but when I do a:

> sudo apt-get install ruby

It fails to install and I get an error message when I try ruby -v

What do I need to do to make sure that I have removed ruby, rails and rubygems so that I can start again?

Thanks

Alex

---

### Post by vcool on 2010-07-04
maybe you should purge your ruby installation, update, and then reinstall

```

sudo apt-get purge ruby
sudo apt-get update
sudo apt-get install ruby

```

---

### Post by AlexHamilton on 2010-07-05
Thanks for the suggestion, but it hasn't solved the problem.  Still getting a suggestion to apt-get install ruby when I check the version : (

Update:  using Synaptic got me there, with a complete removal of installed Ruby packages

---

### Post by WorMzy on 2010-07-05
What message do you get when you run 'sudo apt-get install ruby'?

---

### Post by AlexHamilton on 2010-07-05
It seems to have been solved using Synaptic, thanks.

For some reason I got a 403 error from step 5 above, but the following worked (and got a more recent version of rubygems:
> $ cd ~
$ wget [http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz](http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz)
$ tar xzvf rubygems-1.3.7.tgz
$ cd rubygems-1.3.7
$ sudo ruby setup.rb
$ sudo ln -s /usr/bin/gem1.8 /usr/bin/gem


Update:  I see the problem.  The url seems to be being shrunk by the forum's software.  Copying and pasting either example will not work for the wget

---

### Post by mencio on 2010-07-08
Hi guys!

If  anyone of you have a problem like: "[BUG] gc_sweep(): unknown data type" after installing Ruby and Rails using this tutorial, you need to install older Ruby: ruby1.8_1.8.7.174.orig.tar.gz from source (not apt).

I have written a tutorial (it is in Polish language but it is pretty simple): [http://dev.mensfeld.pl/?p=328](http://dev.mensfeld.pl/?p=328) - it is about installing Ruby and Rails 2.3.5 without this ( [BUG]  gc_sweep(): unknown data type) error.

---

### Post by purvez on 2010-07-24
I'm just starting out with ubuntu and ruby on rails so should I be loading the desktop version on my laptop or the server version?

thanks in advance

---

### Post by bluepicaso on 2010-09-09
i have sql yog installed with wine. as i use it with php.
how can i use sqlyog with ruby ?

---

### Post by bluepicaso on 2010-09-10
Help me.
I installed it succesfully.
But when i started my system today [http://localhost:3000/](http://localhost:3000/) showed nothing.
How do i restart my ruby on rails.
Also my apache is always running since i use it all the time. i work on php.
so why not Ruby working ?
please help me

---

### Post by bluepicaso on 2010-09-10
> **vcool said:**
> [B]Install Ruby on Rails - Lucid Lynx 10.04

[/B]**Step 1 – System update**
```
sudo apt-get update
sudo apt-get dist-upgrade
```  **Step 2 – Install Ruby and friends**
```
 sudo apt-get install ruby  ruby-dev  libopenssl-ruby1.8 irb ri rdoc
``` Now we have ruby installed on our system, next we’re going to install  the database server.
 [B]
Step 3 – Install Mysql / SQLite[/B]
 You can skip this step if you have Mysql or sqlite installed on your  system.
```
 sudo apt-get install mysql-server  sqlite3 libmysql-ruby
```  **Step 4 – Install Development Header**
 Before you can install ruby gems, you will need to install  development headers. Some of gems (like mysql) needs development header  when building native extension process.
 ```
 sudo apt-get install build-essential  libmysqlclient-dev libmysql-ruby libsqlite3-ruby libsqlite3-dev
```  **Step 5 – Install Ruby gem**
 We’re going to use rubygems from [http://rubygems.org](http://rubygems.org)
```
 wget  [http://production.cf.rubygems.org/rubygems/rubygems-1.3.6.zip](http://production.cf.rubygems.org/rubygems/rubygems-1.3.6.zip)
unzip rubygems-1.3.6.zip
cd rubygems-1.3.6
sudo ruby setup.rb

``` in just fews seconds you should see this output :
```

RubyGems installed the following executables:

/usr/bin/gem1.8
``` next, create symlink 
 
```
sudo ln -s /usr/bin/gem1.8 /usr/local/bin/gem
```  **Step 6 – Install Rails with MySQL support**
```
 sudo gem install rails  mysql sqlite3-ruby mongrel
```  **Step 7 – Test drive your Rails installation**
```
rails my_blog

cd my_blog

rake db:create

rake db:migrate

script/server

browse to [http://localhost:3000]("http://localhost:3000/")

```DONE

reference :

[LIST]
[*][http://ignitedtutorials.com/2010/04/how-to-install-ruby-on-rails-on-ubuntu-lucid-lynx-10-04-lts/](http://ignitedtutorials.com/2010/04/how-to-install-ruby-on-rails-on-ubuntu-lucid-lynx-10-04-lts/)
[*][http://guides.rubyonrails.org/](http://guides.rubyonrails.org/)
[/LIST]



I'm screwed up.
my [http://localhost:3000](http://localhost:3000) did not work after system restart.
also i use sqlyog (mysql) installed via wine. I uninstalled the ruby. but i still have the folder in my /usr/lib/ruby . whay is that?? Please help me I'm kinda new to ruby and ubuntu as well.. :frown:

---

