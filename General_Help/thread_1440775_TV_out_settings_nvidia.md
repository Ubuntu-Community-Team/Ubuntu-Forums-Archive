---
title: "TV out settings nvidia"
date: 2010-03-27
forum: General Help
---

### Post by toyoracer on 2010-03-27
Good day. I am trying to set nvidia x screen to play movie on tv via s-video. When switched to tv screen is white in twinview, I can move x server settings window but that is all. In separate x screen monitor goes black, tv does not change.
Also have installed Nvtv tv out. I have  GeForce4 MX420

 Found this article    [http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)
Terminal results

craig@craig-desktop:~$ sudo /etc/X11/xorg.conf
[sudo] password for craig: 
sudo: /etc/X11/xorg.conf: command not found
craig@craig-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg - reset X configuration
[sudo] password for craig: 
dpkg-query: --status needs at least one package name argument

Use --help for help about querying packages;
Use --license for copyright license and lack of warranty (GNU GPL).
/usr/sbin/dpkg-reconfigure: - is not installed
craig@craig-desktop:~$ C

Searched packages and found no matches.

I really like ubuntu but has quite the learning curve. Thank you for helping me learn;)

---

### Post by pbpersson on 2010-03-29
> **toyoracer said:**
> Good day. I am trying to set nvidia x screen to play movie on tv via s-video. When switched to tv screen is white in twinview, I can move x server settings window but that is all. In separate x screen monitor goes black, tv does not change.
Also have installed Nvtv tv out. I have  GeForce4 MX420

 Found this article    [http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)
Terminal results

craig@craig-desktop:~$ sudo /etc/X11/xorg.conf
[sudo] password for craig: 
sudo: /etc/X11/xorg.conf: command not found
craig@craig-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg - reset X configuration
[sudo] password for craig: 
dpkg-query: --status needs at least one package name argument

Use --help for help about querying packages;
Use --license for copyright license and lack of warranty (GNU GPL).
/usr/sbin/dpkg-reconfigure: - is not installed
craig@craig-desktop:~$ C

Searched packages and found no matches.

I really like ubuntu but has quite the learning curve. Thank you for helping me learn;)
[B]
Problem number one:[/B]  Why did you type:

sudo /etc/X11/xorg.conf

Where exactly did you see that in the instructions?  It told you to edit the file so typically you might type:

gksudo gedit /etc/X11/xorg.conf

**Problem number two:**  Why did you type:

sudo dpkg-reconfigure -phigh xserver-xorg - reset X configuration

I do not see that anywhere in the article

Years ago when I used to fool with this stuff, typing "sudo dpkg-reconfigure -phigh xserver-xorg" would totally re-create the xorg.conf file.  At least that is how I remember this process.....

These types of articles are terrible for newbies to follow because they assume you already know your way around Linux

---

### Post by toyoracer on 2010-03-29
Why is a very good question. I assumed on the first entry to initate file, I see that was wrong.
Part two I think came from a link in that forum or another one.

My latest thread is a blank terminal window, LOL not funny

---

