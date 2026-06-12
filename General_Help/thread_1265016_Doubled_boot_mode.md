---
title: "Doubled boot mode"
date: 2009-09-12
forum: General Help
---

### Post by sopadeajo on 2009-09-12
I have a dual boot with Vista
When i boot i can see the following options:

Ubuntu 9.04 kernel 2.6.28-15 generic
Ubuntu 9.04 kernel 2.6.28-15 generic (recovery mode)
Ubuntu 9.04 kernel 2.6.28-11 generic
Ubuntu 9.04 kernel 2.6.28-11 generic (recovery mode)
ubuntu 9.04 memtest 86+
Windows Vista (loader)

I reinstalled Ubuntu two times.

My question is: why do i have twice options? does that mean that i have two installed Ubuntus in hard disk?
Can this be fixed?
What is the difference between kernel 2.6.28-11 and kernel 2.6.28-15?

PS: I do not have any problem now and i can boot with Vista or with Ubuntu but i am afraid i am using two times more disk space than should be necessary.

PS1: Where can i find a free web page to upload snaps to be shown here?

---

### Post by metalf8801 on 2009-09-12
Because you have 2 kernels installed
Linux kernel 2.6.28-15 and Linux kernel 2.6.28.11 
do you want to remove one of the kernels or change grub so that it only shows the newest kernel? 
> **sopadeajo said:**
> I have a dual boot with Vista
When i boot i can see the following options:

Ubuntu 9.04 kernel 2.6.28-15 generic
Ubuntu 9.04 kernel 2.6.28-15 generic (recovery mode)
Ubuntu 9.04 kernel 2.6.28-11 generic
Ubuntu 9.04 kernel 2.6.28-15 generic (recovery mode)
ubuntu 9.04 memtest 86+
Windows Vista (loader)

I reinstalled Ubuntu two times.

My question is: why do i have twice options? does that mean that i have two installed Ubuntus in hard disk?
Can this be fixed?
What is the difference between kernel 2.6.28-15 and kernel 2.6.28-15?

PS: I do not have any problem now and i can boot with Vista or with Ubuntu but i am afraid i am using two times more disk space than should be necessary.

PS1: Where can i find a free web page to upload snaps to be shown here?

---

### Post by akakingess on 2009-09-12
You just have (2) different versions of the Kernel that run with Juanty (9.04) and that is perfectly normal, in case you have a problem, you can choose the older kernel and see if it boots up and that helps with troubleshooting. You will have a normal version of the kernel and generic, which is like booting up without any options turned on (I beleive), if it is too distracting to you, you could install startupmanager by entering " sudo apt-get install startupmanager " (without the quotes) into the terminal and within the startup manager there is an option as to how many versions of the kernel to display, but everything is perfectly normal with your system at first glance.

---

### Post by synapsys on 2009-09-12
> **sopadeajo said:**
> 
PS: I do not have any problem now and i can boot with Vista or with Ubuntu but i am afraid i am using two times more disk space than should be necessary.


Not a problem, kernels hardly take up any hard drive space.

> **sopadeajo said:**
> 
PS1: Where can i find a free web page to upload snaps to be shown here?

[http://imageshack.us/](http://imageshack.us/)
[http://tinypic.com/](http://tinypic.com/)
[http://photobucket.com/](http://photobucket.com/)

---

### Post by sopadeajo on 2009-09-12
Thanks to all, you have been helpful!

---

### Post by sopadeajo on 2009-09-12
[IMG]http://img190.yfrog.com/i/screenshotstartupmanage.png/[/IMG][IMG]http://img190.yfrog.com/i/screenshotstartupmanage.png/[/IMG][IMG]http://http://img190.yfrog.com/i/screenshotstartupmanage.png/[/IMG]
I have downloaded Start Up Manager, here is the snap of it uploaded.

I see that in StartUp Manager/Advanced there is an option to limit the number of kernels; so OK, i won't use it for now.

Just a qestion:

 Every time you reinstall (with the Canonical CD) will you get a new kernel installed?



I uploaded the snap to:
[http://tinypic.com/view.php?pic=zxnwr5&s=3](http://tinypic.com/view.php?pic=zxnwr5&s=3)
But the (Insert Image) feature of this forum is not working for me.[IMG]http://tinypic.com/view.php?pic=zxnwr5&s=3[/IMG]
[IMG]http://tinypic.com/view.php?pic=zxnwr5&s=3[/IMG]

---

### Post by synapsys on 2009-09-13
[IMG]http://i29.tinypic.com/zxnwr5.jpg[/IMG]

At that link you posted, you click on the image, select 'view raw image' (on bottom left) which gives you a url of the pic by itself. Paste that url into the insert image box.

---

### Post by akakingess on 2009-09-13
> **sopadeajo said:**
> [IMG]http://img190.yfrog.com/i/screenshotstartupmanage.png/[/IMG][IMG]http://img190.yfrog.com/i/screenshotstartupmanage.png/[/IMG][IMG]http://http://img190.yfrog.com/i/screenshotstartupmanage.png/[/IMG]
I have downloaded Start Up Manager, here is the snap of it uploaded.

I see that in StartUp Manager/Advanced there is an option to limit the number of kernels; so OK, i won't use it for now.

Just a qestion:

 Every time you reinstall (with the Canonical CD) will you get a new kernel installed?



I uploaded the snap to:
[http://tinypic.com/view.php?pic=zxnwr5&s=3](http://tinypic.com/view.php?pic=zxnwr5&s=3)
But the (Insert Image) feature of this forum is not working for me.[IMG]http://tinypic.com/view.php?pic=zxnwr5&s=3[/IMG]
[IMG]http://tinypic.com/view.php?pic=zxnwr5&s=3[/IMG]

The kernels update all of the time regardless of whether you are changing versions of Ubuntu or not.  This is a good thing, cuz each new kernel has more or better stuff built into it that may not have been there before. That's why there are more than one listed when you boot up, if your kernel upgrades and causes problems, then you can just go back to the last one!!

---

### Post by sopadeajo on 2009-09-13
[IMG]http://i29.tinypic.com/zxnwr5.jpg[/IMG]


OK, all works right now.

---

