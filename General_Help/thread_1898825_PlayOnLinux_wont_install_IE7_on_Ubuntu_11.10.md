---
title: "PlayOnLinux wont install IE7 on Ubuntu 11.10"
date: 2011-12-22
forum: General Help
---

### Post by fmmarzoa on 2011-12-22
Hello,

I'm facing problems to install IE7 on Ubuntu 11.10 using PlayOnLinux. It downloads IE and so, but IE installation hangs on "Installing Windows Internet Explorer Core Components...", while Installation Wizard waits on "Installation in Progress..." forever.

¿Has someone experienced similar problems?

BTW, ¿any easy and fast manner of having IE7, IE8 and IE9 on my Ubuntu? I need them for webpage layout and style testing.

I know I can use a virtual machine, but if I can avoid that...

Regards,

---

### Post by davethewave83 on 2011-12-22
> **fmmarzoa said:**
> Hello,

I'm facing problems to install IE7 on Ubuntu 11.10 using PlayOnLinux. It downloads IE and so, but IE installation hangs on "Installing Windows Internet Explorer Core Components...", while Installation Wizard waits on "Installation in Progress..." forever.

¿Has someone experienced similar problems?

BTW, ¿any easy and fast manner of having IE7, IE8 and IE9 on my Ubuntu? I need them for webpage layout and style testing.

I know I can use a virtual machine, but if I can avoid that...

Regards,

I just now tried installing PlayOnlinux 3.8 and then IE7, I get "The program update.,exe has encountered a serious problem and needs to close. We are sorry for the inconvenience." This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.com](http://appdb.winehq.com) for tips about running this application. If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org" 

so I tried getting the latest 4.0 version of PlayOnLinux
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -

sudo wget [http://deb.playonlinux.com/playonlinux_oneiric.list](http://deb.playonlinux.com/playonlinux_oneiric.list) -O /etc/apt/sources.list.d/playonlinux.list

sudo apt-get update

sudo apt-get install playonlinux

and then tried to install IE7 again. and it installed. 

are you running version 3.8 or 4.0?

---

### Post by mastablasta on 2011-12-22
> **fmmarzoa said:**
>  
BTW, ¿any easy and fast manner of having IE7, IE8 and IE9 on my Ubuntu? I need them for webpage layout and style testing.
 
,
 
no, they are problematic to install in linux and even/especially for testing. 
 
as i know there are internet sites that offer various browser views for this purpose.

---

### Post by fmmarzoa on 2011-12-22
@dave 

I'm using 3.8.8, that I think is the most updated within the Ubuntu 11.10 official packages. I'll try with 4.0, given your experience I'm sure that it will work then.

Thanks a lot.

@masta

I do a lot of trial-and-error and my productivity may be seriously affected with those sites, which renders are really slow even when they work.

Another problem is that I usually develop my webpages on a private webserver, making them public just when they are prepared to be deployed for both, security and development speed reasons, and every render sites that I know needs the page to be public so they can see it.

I will continue using a VirtualBox for this, since I see that IE8 is not ready for Ubuntu and IE9 is lightyears far from being...

Regards,

---

### Post by fmmarzoa on 2012-01-17
I tried installing latest version of playonlinux and the problem persists on my system.

I am about to do an aptitude purge playonlinux and reinstall to see if it works.

Regards,

---

### Post by fmmarzoa on 2012-01-17
It does not work neither. During the install it gives an error:

"Program Error

The program update.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been repported yet, you can report it at http://bugs.winehq.org."

---

### Post by fmmarzoa on 2012-01-17
I have tried again removing my ~/.PlayOnLinux folder, and also rebooting my system before, and I go the same error once again.

I desist.

---

### Post by Mark Phelps on 2012-01-17
> **fmmarzoa said:**
> BTW, ¿any easy and fast manner of having IE7, IE8 and IE9 on my Ubuntu? I need them for webpage layout and style testing.

As you have unfortunately discovered the HARD way -- the answer is NO.

If you really need to test using Internet Explorer, the best way on a Linux system would be to use VirtualBox and install Windows there.  You won't get accelerated video needed for 3D gaming that way, but for testing IE, it will work fine.

---

