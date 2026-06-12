---
title: "Ruby On Rails Installation Haphazardly leads me to Apache Not working on my XAMPP"
date: 2012-10-11
forum: General Help
---

### Post by jason328 on 2012-10-11
SOLUTION: **sudo /etc/init.d/apache2 stop**

I decided I wanted to install ror on my system and did so. Following the Ubuntu Rails Community Guidelines, I installed Ruby, Gems, Rails, and added some features to my Apache. Before all this I had a running XAMPP server with PHP5 and now whenever I start my XAMPP Apache does not execute. I played with uninstalling some of the things I installed but quickly realized it's better to stop and just ask someone who know's what the problem could be. I saved the list of commands I made in the terminal. There are several commands missing at the beginning, but they were the installations for Gems and Ruby.

UPDATE: I started lampp from the terminal and it said that another web server daemon was running. I ran this line of code

sudo netstat -pant | egrep ":80 .* LISTEN"

and was returned with this 1129/apache2. So I sudo-get remove apache2, but when I run the netstat code again it still says 1129/apach2. What's going on here?

jason@Jason-Ubuntu:~$ export PATH=/var/lib/gems/1.8/bin:$PATH 

jason@Jason-Ubuntu:~$ sudo apt-get install rubygems 

jason@Jason-Ubuntu:~$ sudo apt-get install rails 

jason@Jason-Ubuntu:~$ rails /home/jason/www/rudius -d mysql 

jason@Jason-Ubuntu:~$ rails /home/jason/www/rudius -D mysql 

jason@Jason-Ubuntu:~$ rails /home/myuser/www/mynewapp -D mysql 

jason@Jason-Ubuntu:~$     sudo apt-get install apache2 

jason@Jason-Ubuntu:~$     sudo apt-get install php5 

jason@Jason-Ubuntu:~$     sudo apt-get install apache2 

jason@Jason-Ubuntu:~$     sudo apt-get install php5 

jason@Jason-Ubuntu:~$ sudo apt-get install php5 

jason@Jason-Ubuntu:~$ sudo apt-get install libapache2-mod-php5 

jason@Jason-Ubuntu:~$ sudo /etc/init.d/apache2 restart 

jason@Jason-Ubuntu:~$ apt-get autoremove libapache2-mod-passenger 

jason@Jason-Ubuntu:~$ sudo apt-get autoremove libapache2-mod-passenger 

jason@Jason-Ubuntu:~$ sudo apt-get install libapache2-mod-php5 

jason@Jason-Ubuntu:~$ sudo apt-get install apache2 

jason@Jason-Ubuntu:~$ sudo apt-get install php5 

jason@Jason-Ubuntu:~$ sudo apt-get autoremove apache2 apache2-mpm-prefork apache2-prefork-dev 

jason@Jason-Ubuntu:~$ sudo apt-get autoremove ruby-full build-essential 

jason@Jason-Ubuntu:~$ sudo apt-get install apache2 

jason@Jason-Ubuntu:~$ sudo apt-get install php5 

jason@Jason-Ubuntu:~$ sudo apt-get install libapache2-mod-php5 

jason@Jason-Ubuntu:~$ sudo /etc/init.d/apache2 restart

---

