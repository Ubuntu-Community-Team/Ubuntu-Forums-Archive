---
title: "Upgrade from 10.04 to 10.10 (to go to 11.10) Issue"
date: 2012-01-13
forum: General Help
---

### Post by hax3 on 2012-01-13
I'm not very familiar with Linux but have been trying to learn and play around..

I installed Ubuntu 10.04 on my laptop and it's been fine until I realized (while trying to replace OpenOffice) that Ubuntu 11.xx has LibreOffice as standard.  So I started to upgrade to 10.10 (since I read you can't upgrade direct to 11 but have to go through each small update).

After the upgrade, the laptop rebooted and now all it does is bring me to the dos-like login screen "Ubuntu 10.10 PCName tty1".  I tried my username and password that I KNOW is correct but it keeps saying LOGIN INCORRECT.  I know i'm typing the right password because it's the same password I use 100x a day to unlock the screen when it goes to screensaver..  As for the username, I'm pretty sure it's the same as the PCName

Anyway, now I have to way to access my data on my laptop.

I tried booting off Ubuntu Live 11.10 CD, mounting the hard drive and use CHROOT to change the password but it game me /bin/bash error..

I also, tried installing Ubuntu 11.10 side by side with the Ubuntu 10.10 hoping to get access to the filesystem and take ownership (thinking it would be the same as windows) so I can get access to files but when I browse to the PCName home folder, it just shows me 2 "broken" text files.  If i show hidden files there's a .ecryptfs hidden folder.   So it looks like I might have encrypted my home folder when I installed 10.04 (or actually maybe all the way back from lucid - can't even remember encrypting the folder???)

Anyway - I hope someone can help me... i just need access to my data files back...

Thanks in advance!

---

### Post by hax3 on 2012-01-13
I came across dustin kirkland's blog about ecryptfs-recover-private but it looks like this tool is not available in 11.10??  i get "command not found"..  I tried sudo apt-get install ecryptfs-utils but I get "no installation candidate"..

I tried to get 11.04 liveCD but looks like it's not available anymore...

Any help would be greatly appreciated..  whether getting me access to 10.10 or to the encrypted files

Thanks in advance..

---

### Post by hax3 on 2012-01-13
ok.. some progress... tried username as ALL LOWERCASE and finally I got in... now to figure out how to get back to the gui..

---

### Post by JRV on 2012-01-13
> **hax3 said:**
> 
I tried to get 11.04 liveCD but looks like it's not available anymore...


11.04 DVD is available here:

[http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)

The CD can be found on various bittorrent sites.

---

### Post by Double.J on 2012-01-13
Hi there! 

you could attempt to start the gui with 
```

startx

```

But to be honest as you can see, upgrading your release can often go wrong. going all the way through from 10.04 to 11.10 and then on to 12.04 in three months, although doable, I wouldn't really recommend it.

As you have access, I'd recommend copying the contents of your /home directory... and any other directory you may have stored data in and then do a fresh install of 11.10 - a lot has changed from 10.04 to 11.10!

All the best :)

---

### Post by Karys on 2012-01-13
Hello,
This is my first post. I have a similar problem. I have installed ubuntu 10.04 in a Web Server that have php 5.2.8 I upgrade php but I still see (using a file phpinfo() ) that I still have php 5.2.8. I want to have php 5.3.

I'm not sure why I cant upgarde this version. Thanks a lot for your help.

---

### Post by hax3 on 2012-01-13
First.. Thank you both for taking the time to reply... much appreciated.

Re: startx

I tried to run this command but got 

Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so
Failed to load module "fglrx

Found from another forum, I tried following the uninstall of fglrx... after reboot went back to just term login and tried startx again and got something totally different error now..

xinit:  no such file or directory (errno 2): unable to connect to X server
xinit:  no such process (errno 3): server error


back to google!

---

### Post by Double.J on 2012-01-13
> **Karys said:**
> Hello,
This is my first post. I have a similar problem. I have installed ubuntu 10.04 in a Web Server that have php 5.2.8 I upgrade php but I still see (using a file phpinfo() ) that I still have php 5.2.8. I want to have php 5.3.

I'm not sure why I cant upgarde this version. Thanks a lot for your help.

Hi there and welcome to the forums! 

I may be wrong, but I thought 10.04 came with 5.3... have you tried 
```

sudo apt-get update && sudo apt-get upgrade

```

hope it helps?

:)

---

### Post by holycow131415 on 2012-01-13
I cannt help with your problem, but i just wanted to point out that you could have avoided this by just uninstalling openoffice (so that you didnt have to upgrade) and then you could have installed libre office from ppa.

[http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html](http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html)

---

### Post by hax3 on 2012-01-13
I realize I could have just uninstalled openoffice and installed libreoffice and kept with 10.04 but I figured time to update anyway and see what's new...

Oh well...   I think this video driver issue keeps biting me in the butt every time I do an upgrade...  maybe i'll remember next time...

anyway.. just an update.. since being able to login to the 10.10 shell only and couldn't get xorg to start, I figured I'll just continue with upgrade path to 11.04... we'll see where that takes me...

---

### Post by Karys on 2012-01-13
Hi gnu/mirrow, Thanks for reply.
I was reading about that and I think it's true that ubuntu 10.04 came with php 5.3 But I have php 5.2.10 version. 

When I made this commands: sudo apt-get upgrade
I have 184 packets to upgrade, but  I'm afraid if this changes could affect my moodle installation.

Also with this command: apt-cache show libapache2-mod-php5 php5-cgi
I can see that all files have 5.3 version except this one: 
Package: **libapache2-mod-php5**
Status: install ok installed
Priority: optional
Section: httpd
Source: php5
Version: **5.2.10.dfsg.1-2ubuntu6.4**

I&#8217;m not sure if this is the problem.
Thanks

---

### Post by mörgæs on 2012-01-13
Karys, please stop multiposting. I have deleted your duplicate threads.

---

