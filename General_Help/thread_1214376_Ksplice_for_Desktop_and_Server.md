---
title: "Ksplice for Desktop and Server"
date: 2009-07-15
forum: General Help
---

### Post by JoshuaRL on 2009-07-15
Ksplice is a new kernel updating application that can allow you to apply kernel updates without rebooting.  According to researchers 88% of the most recent x86 critical security kernel patches were installable without any extra coding or tweaking through Ksplice and all were installable with some level of work.  How long does it take?  It will disrupt system operation for 0.7 milliseconds, and the system state will remain intact so you will not be able to notice anything.  For more information, see the [Ars Technica article](http://arstechnica.com/open-source/news/2009/07/ksplice-is-like-viagra-for-linux-server-uptime.ars) and [Ksplice Inc.'s website.](http://www.ksplice.com/)

And there's even better news.  If you're running Jaunty Jackalope (9.04) you can have rebootless system updates running without any custom code having to be written on your side at all.  Ksplice Uptrack is the name of the application, and they're making it freely available.  And this works for Desktops and Servers.  For either one, you'll need to get the [installer .deb from here.](http://www.ksplice.com/uptrack/)  Also check out the [Ksplice Uptrack "How To Use It" page](http://www.ksplice.com/uptrack/using)

**Desktops**
Install using Gdebi, and you're off.  But for me, I had some dependencies I had to go apt-get before it would install properly.  If you run into any issues, run
```
sudo aptitude update
```
in the terminal and see what packages it depends on.  Then install those and try again.  For my laptop, it took only one try like that for it to work.  

From there, Ksplice will run in your system tray and alert you when you have updates available.  Really simple, the equal of PackageKit or Update Manager.

**Servers**
My server was a little harder to get installed than my laptop.  You'll need to "cd" to the directory you saved it in, and run
```
sudo dpkg -i ksplice-uptrack.deb
```
My server is set up for just SSH and Samba, so it needed some dependencies installed to get through that.  Not that difficult, just had to go get what was listed in dpkg.  Specifically, I needed python-yaml, kerneloops, and librsvg2-common.  But there were some other dependencies that branched off of those.  After getting those, installation worked perfectly.

For managing Ksplice Uptrack from the command-line, you can look at "man uptrack" or at the aforementioned "How To Use It" page at the bottom for CLI info.  But typically, you'll be using the following commands the most.
```
sudo uptrack-upgrade
```
This will query the Uptrack server, download any updates, and install them on your system.
```
sudo uptrack-show
```
This will show any currently installed updates installed through Ksplice Uptrack.  After installing, here is my commandline:
```

joshua@servinator3:~$ sudo uptrack-show
[sudo] password for joshua: 
Installed updates:
None
joshua@servinator3:~$ sudo uptrack-upgrade
The following steps will be taken:
Install [82dkzlzv] Multiple bugs in filesystem core.
Install [2995a653] Possible erroneous memory overcommit in program start.
Install [48ektn2c] Performance regression in filesystem buffer code.

Go ahead [y/N]? y
Installing [82dkzlzv] Multiple bugs in filesystem core.
Installing [2995a653] Possible erroneous memory overcommit in program start.
Installing [48ektn2c] Performance regression in filesystem buffer code.
joshua@servinator3:~$ sudo uptrack-show
Installed updates:
[48ektn2c] Performance regression in filesystem buffer code.
[2995a653] Possible erroneous memory overcommit in program start.
[82dkzlzv] Multiple bugs in filesystem core.
joshua@servinator3:~$ 

```

Overall, Ksplice Uptrack has worked extremely well in my limited testing and seems to be just what's needed for production environments or other sytems that need extended uptime and security patches at the same time.  Even though those don't specifically apply to me, I'm sure I'll be installing Kspice Uptrack on all of my Ubuntu computers from now on.

---

### Post by theApokalypsis on 2009-07-17
Woot,

great post. Was searching for any posts regarding Ksplice because I wanted to relay it if not. Going to check it out on my system, your post will help!

First GNU/Linux pwns for not having to reboot in comparison to Windows, now even more so!

---

### Post by forestwalkerjoe on 2009-09-02
i have it now on my Jaunty.. wubi.. and it seems to be working just FINE. 
A good friend uses Kubuntu.. and says it fails to install for him. ANY one have ANY idea how to go about getting the Kubuntu to allow the install? it gives a strange error.. some thing about invalid or some thing.

---

### Post by SuperBaby on 2009-09-02
Ksplice is working fine in my Ubuntu Netbook Remix 9.04. There is one thing I don’t like…. every time when I boot up my netbook, some text will appear showing the loading sequence of Ksplice. It shows up after the usplash screen and the text is annoying. It seems that there is no way to turn it off.

---

### Post by Down8ve on 2009-11-23
> **forestwalkerjoe said:**
> i have it now on my Jaunty.. wubi.. and it seems to be working just FINE. 
A good friend uses Kubuntu.. and says it fails to install for him. ANY one have ANY idea how to go about getting the Kubuntu to allow the install? it gives a strange error.. some thing about invalid or some thing.

I'm on Kubuntu, just did a Ksplice update.

Since Kubuntu uses Kpackage, the terms of use dialog does not appear.   He should open a terminal cd to the directory (as noted above) and paste:

sudo dpkg -i ksplice-uptrack.deb

Answer the dialogs and you're done.

---

