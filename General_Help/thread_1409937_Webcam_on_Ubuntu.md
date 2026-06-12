---
title: "Webcam on Ubuntu"
date: 2010-02-18
forum: General Help
---

### Post by cancer10 on 2010-02-18
Hi

I was wondering if Ubuntu supports webcams, I mean I want to buy a webcam (for example logitec or intex) but their specifications tells me that the drivers are only supported on Windows platform.


Can anyone put some light on this please?



Thanks

---

### Post by nixclusive on 2010-02-18
If its a generic capture device it should work anyway. i.e. if it works on Windows XP without any supporting drivers it *should* work on Linux as well.

---

### Post by cancer10 on 2010-02-18
> **nixclusive said:**
> If its a generic capture device it should work anyway. i.e. if it works on Windows XP without any supporting drivers it *should* work on Linux as well.

Are you using webcam on your ubuntu system?


I am using ubuntu v 9.04

---

### Post by anaconda on 2010-02-18
some work very well out-of-the-box some dont.
eg. I have a logitech, which is 1,3Mpix in windows, but in ubuntu it works with a resolution of 640x480. It might be possible to get it to work better, but the main thing is it works..

---

### Post by cancer10 on 2010-02-19
ok so I bought a webcam, **Zebronics New Eagle's Eye**, now ubuntu 9.04 wont recognize it. The driver that came with it just supports Windows.

Can canyone here help me please?


Thanks

---

### Post by smaw0351 on 2010-02-19
Microsoft Lifecam VX-3000 is working with 9.10

---

### Post by manoriax on 2010-02-19
> **cancer10 said:**
> ok so I bought a webcam, **Zebronics New Eagle's Eye**, now ubuntu 9.04 wont recognize it. The driver that came with it just supports Windows.

Can canyone here help me please?


Thanks

  Have you tried this one: [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) ?

---

### Post by Wiley_Linux on 2010-02-19
Creative VF0350 works fine in Ubuntu 9.10

---

### Post by HermanAB on 2010-02-19
Bad luck...

I have not encountered a web cam that doesn't work yet - and I have tried many.

---

### Post by cancer10 on 2010-02-19
> **manoriax said:**
> Have you tried this one: [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) ?

Yes, but for some reason it does not allow me to download/install it


```
pompa@White-Rabbit:~$ gksudo 'python /usr/share/EasyCam2/core.py --gtk'
pompa@White-Rabbit:~$ gksudo 'python /usr/share/EasyCam2/core.py --gtk'
python: can't open file '/usr/share/EasyCam2/core.py': [Errno 2] No such file or directorypompa@White-Rabbit:~$ sudo apt-get install easycam2-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
E: Broken packages
pompa@White-Rabbit:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_IN
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_IN
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Hit http://ubuntu.oss.eznetsols.org jaunty Release.gpg                         
Ign http://ubuntu.oss.eznetsols.org jaunty/main Translation-en_IN              
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://ubuntu.oss.eznetsols.org jaunty/restricted Translation-en_IN        
Ign http://ubuntu.oss.eznetsols.org jaunty/universe Translation-en_IN
Ign http://ubuntu.oss.eznetsols.org jaunty/multiverse Translation-en_IN
Hit http://ubuntu.oss.eznetsols.org jaunty Release                             
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_IN                     
Get:2 http://dl.google.com stable Release [2540B]                              
Ign http://blognux.free.fr hardy Release.gpg                                   
Hit http://ubuntu.oss.eznetsols.org jaunty/main Sources              
Get:3 http://dl.google.com stable/main Packages [868B]               
Hit http://deb.opera.com stable Release        
Hit http://ubuntu.oss.eznetsols.org jaunty/restricted Sources     
Hit http://ubuntu.oss.eznetsols.org jaunty/main Packages          
Hit http://ubuntu.oss.eznetsols.org jaunty/restricted Packages    
Hit http://ubuntu.oss.eznetsols.org jaunty/multiverse Sources     
Hit http://ubuntu.oss.eznetsols.org jaunty/universe Sources       
Hit http://ubuntu.oss.eznetsols.org jaunty/universe Packages
Hit http://ubuntu.oss.eznetsols.org jaunty/multiverse Packages    
Ign http://deb.opera.com stable/non-free Packages                 
Hit http://deb.opera.com stable/non-free Packages  
Ign http://blognux.free.fr hardy/main Translation-en_IN
Ign http://blognux.free.fr hardy Release           
Ign http://blognux.free.fr hardy/main Packages     
Ign http://blognux.free.fr hardy/main Sources      
Hit http://blognux.free.fr hardy/main Packages     
Hit http://blognux.free.fr hardy/main Sources      
Fetched 3597B in 5s (604B/s)
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
pompa@White-Rabbit:~$ 



```

---

### Post by Neezer on 2010-02-19
I know you've already bought one, but I would recommend returning it and getting a logitech quickcam pro 9000. I have used it with 8.04, 9.04, and 9.10. it was plug and play for each version.

I use it for skype as well.

Just my 2 cents. If you start having problems with things and aren't a HUGE nerd, returning and getting something that will work out of the box might be the best bet...


good luck

---

### Post by manoriax on 2010-02-20
Okay then try this:
```
wget http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-core.deb
``````
wget http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-qt.deb
``````
sudo dpkg -i easycam2-core.deb
``````
sudo dpkg -i easycam2-qt.deb
```It should install properly - we just use the qt-version of the program, because since the release if Jaunty, the gtk-version does not work anymore.
Perhaps it is necessary to install cheese before that, so just type ```
sudo apt-get install cheese
```
if your computer says that it needs cheese.

---

### Post by argos3016 on 2010-02-20
install cheese...
apt-get install cheese

---

### Post by 3rdalbum on 2010-02-20
The advice in this thread said to buy one that works WITHOUT having to install any drivers in Windows. I strongly advise returning it and finding one that says it works "plug 'n' play, no drivers needed".

Such webcams use a standard form of communication called UVC, that works with Linux, Windows and Mac OS without having to install drivers. Just like a USB flash drive.

---

### Post by manoriax on 2010-02-20
> **3rdalbum said:**
> Such webcams use a standard form of communication called UVC, that works with Linux, Windows and Mac OS without having to install drivers. Just like a USB flash drive.

On the other hand, people with (yet) incompatible webcams can help to improve the compatibility.

---

### Post by 3rdalbum on 2010-02-20
> **manoriax said:**
> On the other hand, people with (yet) incompatible webcams can help to improve the compatibility.

But if people keep buying non-UVC webcams, where's the incentive for manufacturers to start shipping UVC webcams?

Once all new webcams are UVC-based, we no longer have to spend any reverse-engineering effort on webcams, and nobody who wants to buy a webcam for Linux will buy a dud. I've bought a dud barely-Linux-supported webcam before - that's $40 I'll never see again.

---

### Post by nightspider on 2010-02-23
Since it was mentioned to buy a webcam what specifications would a person look for? I have 2 old webcams, so I wouldn't even know what to look for today.

---

