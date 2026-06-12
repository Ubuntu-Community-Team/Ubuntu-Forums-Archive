---
title: "xampp installation"
date: 2010-08-05
forum: General Help
---

### Post by grl on 2010-08-05
I am trying to install XAMPP 1.7.3a for quite a while now! I am getting always to see the following result:

gr@gr-laptop:~$ su
Password: 
root@gr-laptop:/home/gr# cd Desktop
root@gr-laptop:/home/gr/Desktop# ls
Target 3001! V14 discover.desktop  xampp-linux-1.7.3a.tar.gz
root@gr-laptop:/home/gr/Desktop# tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
root@gr-laptop:/home/gr/Desktop# 

I am turning in circles. Any help? Thank you!
GR

---

### Post by X.Cyclop on 2010-08-05
There is no such an **/opt** folder (i don't know why, there used to be :)).
So do this:
```

sudo mkdir /opt
sudo tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt

```

and then follow the instructions to get xampp installed.;)

---

### Post by grl on 2010-08-06
I made the /opt directory manually, but no success! Here are the results:

gr@gr-laptop:~$ su
Password: 
root@gr-laptop:/home/gr# tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
tar: xampp-linux-1.7.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@gr-laptop:/home/gr# 

I am about to give up!
GR

---

### Post by WorMzy on 2010-08-06
Why have you set a password for root, and why are you using su? And why are trying to use XAMPP instead of just using the easily installed LAMP?

If you have legitimate reasons for the above activities, then please disregard the following advice.

If you just need Apache/MySQL/PHP, then run

```
sudo tasksel install lamp-server
```

That should be all you need. If you want phpmyadmin, install with
```
sudo apt-get install phpmyadmin
```

If you want Perl/Python/Ruby Apache support, install the following modules (as required)

```
sudo apt-get install libapache2-mod-perl2 libapache2-mod-python libapache2-mod-python
```

---

### Post by Dai777 on 2010-08-06
After downloading simply type in the following commands:

   1. Go to a Linux shell and login as the system administrator root:

      su

   2. Extract the downloaded archive file to /opt:

	**sudo tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt**

That's all. XAMPP is now installed below the /opt/lampp directory.

=============================================

To start XAMPP simply call this command:

**/opt/lampp/lampp start**

You should now see something like this on your screen:

[B]Starting XAMPP 1.6.8a...
LAMPP: Starting Apache...
LAMPP: Starting MySQL...
LAMPP started.[/B]

=============================================

To stop XAMPP simply call this command:

**/opt/lampp/lampp stop**

You should now see:

[B]Stopping LAMPP 1.6.8a...
LAMPP: Stopping Apache...
LAMPP: Stopping MySQL...
LAMPP stopped.[/B]

And XAMPP for Linux is stopped. 

=============================================


To uninstall XAMPP just type in this command:

**rm -rf /opt/lampp**

The end. 

=============================================

[http://localhost](http://localhost)

=============================================

[http://www.apachefriends.org/en/xampp-linux.html#379](http://www.apachefriends.org/en/xampp-linux.html#379)

=============================================

To use the sweet gtk/python control panel:



Run in a terminal: 
**gedit ~/.local/share/applications/xampp-control-panel.desktop**


Paste the following into the open file and save and exit.

[B][Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg[/B]

---

### Post by X.Cyclop on 2010-08-07
wormzy, i think xampp is a bit easier to manage (at least for a newbie).:)

> **grl said:**
> I made the /opt directory manually, but no success! Here are the results:

gr@gr-laptop:~$ su
Password: 
root@gr-laptop:/home/gr# tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
tar: xampp-linux-1.7.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@gr-laptop:/home/gr# 

I am about to give up!
GR
are you in the same folder as the file? Don't give up, be patient it's just a couple of things you have to do!;)

---

### Post by WorMzy on 2010-08-07
> **X.Cyclop said:**
> wormzy, i think xampp is a bit easier to manage (at least for a newbie).:)

Could be, I've never used it. I just see so many topics asking for help with it that I always recommend LAMP. At least with LAMP[+PPR] problems, I can offer help. ;)

---

