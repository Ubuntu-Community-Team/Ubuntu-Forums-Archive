---
title: "need help with aircrack"
date: 2009-10-29
forum: General Help
---

### Post by into9rod on 2009-10-29
Hello im new to [linux[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://forums.techguy.org/#") and  i just cant install aircrack i already installed libraries and essence but i just cant install it can anyone help?this is what im getting when i try
*****into9rod@into9rod-desktop:~$ sudo apt-get install aircrack-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack-ng*******
i already download aircrack is in the desktop plz dont send me to another website or thread just explain me in a noob way thanks

---

### Post by michy99 on 2009-10-29
Did you download a .deb package? If so, you should just double-click on it.

---

### Post by vahnx on 2009-10-29
Stop trying to get into your neighbors wifi -_-

Since you do not wan't links, here's an answer taken from a site:

> 1) Install dependences

# sudo apt-get install build-essential libssl-dev libsqlite3-dev sqlite3 subversion iw

2) Grab the latest snapshot of Aircrack-ng

# sudo svn co [http://trac.aircrack-ng.org/svn/trunk/](http://trac.aircrack-ng.org/svn/trunk/) aircrack-ng

3) Change to the Aircrack-ng folder

# cd aircrack-ng

4) Build Aircrack-ng with sqlite for airolib-ng support

# sudo make sqlite=true

# sudo make sqlite=true install

5) Test injection capability on your wireless card

(Note: Your wireless interface may be something other than wlan0, type iwconfig to confirm)

# aireplay-ng -9 wlan0

You should see something like:

16:29:41 wlan0 channel: 4 
16:29:41 Trying broadcast probe requests... 
16:29:41 Injection is working!

If you dont see the above, you need to go patch your wireless driver to support injection.

---

### Post by into9rod on 2009-10-29
thanks for the reply this what im getting

into9rod@into9rod-desktop:~$ sudo apt-get install build-essential libssl-dev libsqlite3-dev sqlite3 subversion iw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
sqlite3 is already the newest version.
sqlite3 set to manually installed.
E: Couldn't find package iw

Then this:
into9rod@into9rod-desktop:~$ sudo svn co [http://trac.aircrack-ng.org/svn/trunk/](http://trac.aircrack-ng.org/svn/trunk/) aircrack-ng
sudo: svn: command not found

Some help will be cool thanks and well im studying cisco rightnow and im just wanna learn for ethical purposes only tks again.


Also yes i have a .deb package with this installed adduser, alsa-base, ca-certificates, net-tools, passwd, python2.5-minimal, python-minimal, sgml-data, ucf.

---

### Post by elreteipos on 2010-05-22
> You should see something like:

16:29:41 wlan0 channel: 4 
16:29:41 Trying broadcast probe requests... 
16:29:41 Injection is working!


This is what I get:

> 

pdedecker@betabuntu:~/wireless$ sudo aireplay-ng --test eth1 -b *(the Mac address of my own WiFi network goes here)*
10:28:43  Trying broadcast probe requests...
10:28:45  No Answer...
10:28:45  Found 1 AP 

10:28:45  Trying directed probe requests...
10:28:45  *(the Mac address of my own WiFi network goes here)* - channel: 1 - '*(my network's SSID)*'
10:28:51   0/30:   0%


---

