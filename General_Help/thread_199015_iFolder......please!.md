---
title: "iFolder......please!"
date: 2006-06-18
forum: General Help
---

### Post by viciouslime on 2006-06-18
[https://lists.ubuntu.com/archives/dapper-changes/2006-May/011594.html]("https://lists.ubuntu.com/archives/dapper-changes/2006-May/011594.html")

I found a link to this in another thread from about 3 weeks ago. Does anyone know when iFolder will actually appear in the repositories? I looks like it would be the perfect solution to my syncing problems. :D

---

### Post by viciouslime on 2006-06-20
<bump> :)

---

### Post by aysiu on 2006-06-20
No idea, but have you tried using *alien* to install it? ```
wget -c http://forgeftp.novell.com/ifolder/client/released/3.2.5347.1/linux/ifolder3-3.2.5347.1-1.i686.rpm
sudo aptitude update
sudo aptitude install alien
sudo alien -i ifolder3-3.2.5347.1-1.i686.rpm
```

---

### Post by wzzrd on 2006-06-23
You can grab all of the iFolder rpm packages from this location: [http://forgeftp.novell.com/ifolder/client/3.5/20060329-1135/linux/SUSE10.1-i586/rpms/]("http://forgeftp.novell.com/ifolder/client/3.5/20060329-1135/linux/SUSE10.1-i586/rpms/")

Convert them to debs and install using ```
fakeroot alien --fixperms *.rpm
sudo dpkg -i *.deb 
```

Important: when using Dapper, you cannot install mDNSresponder from a repository. It's no longer there. I used the libdns_sd.so from my OpenSuse10.1 install, which seems to work fine. Just drop it in /usr/lib. I added my libdns_sd.so for your convenience, but you'll have to trust me not having messed with it.

There is some useful information here: [http://ubuntuforums.org/showthread.php?t=158315&highlight=ifolder](http://ubuntuforums.org/showthread.php?t=158315&highlight=ifolder)

The version I link to above is a version _with_ workgroup / p2p support! This is cool, but alpha! Keep this in mind.
 
If someone get's the nautilus extension to work, please drop me a line!

Update:I get a ```

*** glibc detected *** free(): invalid next size (fast): 0x084828b0 ***
``` error when I add an iFolder and it is scanned for changes. End of the line for me.

---

### Post by itguy614 on 2006-06-23
[QUOTE=aysiu]No idea, but have you tried using *alien* to install it? ```
wget -c http://forgeftp.novell.com/ifolder/client/released/3.2.5347.1/linux/ifolder3-3.2.5347.1-1.i686.rpm
sudo aptitude update
sudo aptitude install alien
sudo alien -i ifolder3-3.2.5347.1-1.i686.rpm
```[/QUOTE]

Even easier, edit your /etc/apt/sources.list to include:

deb [http://trunks.whiprush.org/~jorge/ifolder](http://trunks.whiprush.org/~jorge/ifolder) dapper main

Then:

sudo apt-get update
sudo apt-get install ifolder3

Then you are all set to go.  iFolder is the first app I install on my systems.  After that, sync to get my files from my personal iFolder server.  Life is oh so good.

---

### Post by KillerKiwi on 2006-06-23
Got it from the repo, Sweet it works!!! I like the 'new' interface too.  Any body know what new features the new server offers?

---

### Post by PizzAp on 2006-06-24
I still have trouble with 6088 from:

[http://forgeftp.novell.com/ifolder/client/3.5/current/linux/SUSE10.1-i586/rpms/](http://forgeftp.novell.com/ifolder/client/3.5/current/linux/SUSE10.1-i586/rpms/)
[http://forgeftp.novell.com/ifolder/server/3.5/current/linux/SLES10-i586/RPMS/i586/](http://forgeftp.novell.com/ifolder/server/3.5/current/linux/SLES10-i586/RPMS/i586/)

---

### Post by viciouslime on 2006-06-24
Didn't work from repo for me :( Thanks for trying to help though :D

---

### Post by PizzAp on 2006-06-24
I did a checkout of their svn repositories. It's a lot of code, but maybe i'll try to build ubuntu packages next week. I let you know if it works out.. ;)

---

### Post by naked on 2006-06-25
I too would LOVE to have some packages for the ifolder server.  I've tried compiling it several times, but something new always goes wrong.

This link might be of some help to someone: [http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Dapper](http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Dapper)

Let me know if you get it working!

I got a .deb built using checkinstall, but it when I run simiasserver, it was a program called simias-server-setup, which i don't have?

L

---

### Post by regeya on 2006-11-10
Taking a moment to throw in my AOL METOO moment.  Heh.

iFolder seems like a great idea; it's a pain in the caboose when one is stuck with analog dialup to download iFolder Server only to bash one's head against the wall.  :D 

If any friendly people out there would care to package this, that would be excellent!  This is an awesome concept, and I would love to replace Unison with iFolder.  Looooove it.

---

### Post by viciouslime on 2006-11-12
Maybe they can get it into feisty :D

---

### Post by flickerfly on 2007-02-22
I posted a bug asking about getting this in Ubuntu:
[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

---

