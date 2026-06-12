---
title: "HowTo: Install Ubuntu 10.04.3 LTS LAMP with PHP5.2.10 of Karmic"
date: 2011-11-27
forum: General Help
---

### Post by TeaCii on 2011-11-27
Hi,

The most important thing about this post is that I am writing it on 27 Nov. 2011
Written of LAMP

Problem:
Ubuntu ships with PHP5.3.x
I need to have PHP5.2.x
Karmic repositories have been relocated.

Pre-requisite:
I am doing a clean install.

Steps:
**Step 1**. Install Ubuntu. Do not install Apache yet. You can install Mysql before or after. It does not matter.

**Step 2**. Run the script. Courtesy of [Mr.Kandy]("http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/"). You can copy paste it on ssh shell.

-----------Start of script
php_installed=`dpkg -l | grep php| awk '{print $2}' |tr "\n" " "`

# remove all php packge
sudo aptitude purge $php_installed

# use karmic for php pakage
# pin-params:  a (archive), c (components), v (version), o (origin) and l (label).
echo -e "Package: php5\nPin: release a=karmic\nPin-Priority: 991\n"  | sudo tee /etc/apt/preferences.d/php > /dev/null
apt-cache search php5-|grep php5-|awk '{print "Package:", $1,"\nPin: release a=karmic\nPin-Priority: 991\n"}'|sudo tee -a /etc/apt/preferences.d/php > /dev/null
apt-cache search -n libapache2-mod-php5 |awk '{print "Package:", $1,"\nPin: release a=karmic\nPin-Priority: 991\n"}'| sudo tee -a /etc/apt/preferences.d/php > /dev/null
echo -e "Package: php-pear\nPin: release a=karmic\nPin-Priority: 991\n"  | sudo tee -a /etc/apt/preferences.d/php > /dev/null

# add karmic to source list
egrep '(main restricted|universe|multiverse)' /etc/apt/sources.list|grep -v "#"| sed s/`lsb_release -s -c`/karmic/g | sudo tee /etc/apt/sources.list.d/karmic.list > /dev/null

# update package database (use apt-get if aptitude crash)
sudo apt-get update

# install php
sudo apt-get install $php_installed
# or sudo aptitude install -t karmic php5-cli php5-cgi //for fcgi
# or  sudo apt-get install -t karmic  libapache2-mod-php5 //for apache module

sudo aptitude hold `dpkg -l | grep php5| awk '{print $2}' |tr "\n" " "`
#done
--------------------end of script

This script will prevent future updates of the php packages and point the system to repository.

**Step 3**:  got to /etc/apt/sources.list.d
Find the file karmic.list
replace the complete content of the file with the following content:
----------------Start of content
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
----------------End of content
This step points to the new location of the Karmic repository.

**Step 4:** Allot more cache to apt. I dont know how much. So I just used a big number.
locate the file /etc/apt/apt.conf.d/70debconf
append the following line at the end:
----------------Start of line
APT::Cache-Limit "200000000";
----------------End of line

**Step 5:** Execute "apt-get update" to update the settings.

Now you can happily install any package. It will automatically pull the right PHP package form PHP 5.2.10

Install apache any which way you like. Simplest is the command:
apt-get install apache2

I hope this was useful. It is my way of giving help, which I have been taking. Merry Xmas and Happy New Year 2012 !!! :popcorn:

---

