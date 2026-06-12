---
title: "Slow machines"
date: 2011-01-16
forum: General Help
---

### Post by vv73 on 2011-01-16
Help me to choose distrib. 
I installed XUbuntu  to my Celeron 1,2 Ghz and 256 RAM and It works very slow. If I start more then three aplications it almost hangs. Will I have a change get fast OS if I install Lubuntu?

BTW Windows XP works fine on these machines...

Is that good idea to install LXDE (lubuntu-desktop) on Xubuntu and use that. Will it works faster&  

Is it important what programs to install? Can I install then Open Office to Lubuntu, is that make the system slower?

---

### Post by snowpine on 2011-01-16
Welcome to the forums!

256mb is not very much RAM, is it possible to get more?

If you want to try the LXDE desktop (used by Lubuntu), simply:

```
sudo apt-get update
sudo apt-get install lxde
```

Then, log out, and from the login screen, select Sessions, LXDE.

A couple other tips I can give you are: 1) don't open lots of apps at the same time, only use 1 or 2 at a time and close them when you're done; 2) try to use lightweight applications, for example Abiword or Mousepad instead of Openoffice.

---

### Post by vv73 on 2011-01-16
> **snowpine said:**
>  
256mb is not very much RAM, is it possible to get more?

 
It is school computer lab and RAM on computers is RIMM
We cannot buy this type of memory...
 
> **snowpine said:**
>  
If you want to try the LXDE desktop (used by Lubuntu), simply:
 
Thank you. The question is if I setup two DE if it use
only one when I start it, or it is much better to remove another DE
to make the system faster?
 
> **snowpine said:**
>  
applications, for example Abiword or Mousepad instead of Openoffice. 

If I remove XCFE, it remove OO too.
If I install OO again - if slow down the system or the problems with
memory will be only when I start OO?

---

### Post by kellemes on 2011-01-16
Software (including a window/desktop-manager) installed will not slowdown the system, unless you'r extremely low on diskspace.. so only when started it will make a difference, so OpenOffice-Write will only slowdown the system when started, you can leave it installed without trouble, just run Abiword (for example) instead.

---

### Post by snowpine on 2011-01-16
> **vv73 said:**
> Thank you. The question is if I setup two DE if it use
only one when I start it, or it is much better to remove another DE
to make the system faster?
 
You're welcome!

Software is only loaded in RAM when you use it. So if you start an LXDE session, the Xfce components will not be loaded. Therefore there is no harm to having multiple DE's installed (except for using a small amount of hard disk space).

> **vv73 said:**
> If I remove XCFE, it remove OO too.
If I install OO again - if slow down the system or the problems with
memory will be only when I start OO?

OO uses the same amount of RAM regardless of DE.

Therefore you need to calculate the amount of RAM you need for the core system (kernel, libraries, drivers) + RAM needed for the DE + RAM needed for applications. 

Various tools such as the terminal command 'top' or the system monitor can help you figure out what is using up your RAM.

---

### Post by 1clue on 2011-01-16
With that much RAM you'll be hitting swap constantly.

How much swap do you have?  How much are you using?

I would bet that doubling your swap would improve things in your case.  Getting 2G RAM on there would be better though.  Have you tried ebay?

---

### Post by ggarron on 2011-01-16
> **vv73 said:**
> Help me to choose distrib. 
I installed XUbuntu  to my Celeron 1,2 Ghz and 256 RAM and It works very slow. If I start more then three aplications it almost hangs. Will I have a change get fast OS if I install Lubuntu?

BTW Windows XP works fine on these machines...



Sorry, If I'm not suggesting an Ubuntu distribution, but I think Arch Linux is what you need, with OpenBox.

Maybe not OpenOffice, look for other options, xpdf instead of Okular, mpg123 instead of any graphical MP3 player.

hope it helps.

---

### Post by fabricator4 on 2011-01-16
> **vv73 said:**
> Help me to choose distrib. 
I installed XUbuntu  to my Celeron 1,2 Ghz and 256 RAM and It works very slow. If I start more then three aplications it almost hangs. Will I have a change get fast OS if I install Lubuntu?

In my experience XP SP3 is painfully slow on all older machines I've tried, and Xubuntu/Ubuntu is invariably faster.  The minimum configuration for Xu/Ubuntu is 256 Mb, and more memory does make a difference.

You need to look in System Monitor and see what's going on.  System monitor can graph resources such as memory usage and CPU usage for you, as well as showing which programs are eating up both.  On older machines it's a good idea to reduce the refresh rate reduce the overhead of system monitor itself.

I think you'll be able to see what's going on, and it may not be memory or swap file.  I have a feeling there is something else going on here.

You didn't say what release of Xubuntu you had installed.  I think it's fair to say that it might be better to recommend the LTS release (10.04 Lucid Lynx) as being the most stable and efficient on older machines.  The latest release (10.10) being the first release after an LTS seems to have more than it's share of problems, which might be expected really.

I normally recommend Ubuntu even for machines like yours, because it's more intuitive and easier to grasp for users who are used to XP.

Chris

---

### Post by fabricator4 on 2011-01-16
> **vv73 said:**
> Help me to choose distrib. 
I installed XUbuntu  to my Celeron 1,2 Ghz and 256 RAM and It works very slow. If I start more then three aplications it almost hangs. Will I have a change get fast OS if I install Lubuntu?

In my experience XP SP3 is painfully slow on all older machines I've tried, and Xubuntu/Ubuntu is invariably faster.  The minimum configuration for Xu/Ubuntu is 256 Mb, and more memory does make a difference.

You need to look in System Monitor and see what's going on.  System monitor can graph resources such as memory usage and CPU usage for you, as well as showing which programs are eating up both.  On older machines it's a good idea to reduce the refresh rate reduce the overhead of system monitor itself.

I think you'll be able to see what's going on, and it may not be memory or swap file.  I have a feeling there is something else going on here.

You didn't say what release of Xubuntu you had installed.  I think it's fair to say that it might be better to recommend the LTS release (10.04 Lucid Lynx) as being the most stable and efficient on older machines.  The latest release (10.10) being the first release after an LTS seems to have more than it's share of problems, which might be expected really.

I normally recommend Ubuntu even for machines like yours, because it's more intuitive and easier to grasp for users who are used to XP.

Chris

---

### Post by JGJones on 2011-01-16
I've just gotten a spare laptop with a similar spec to yours - Celeron 1.2GHz with 256Mb.

I installed Ubuntu on it, but I actually had a spare 512Mb SDRAM card so I installed that giving me 768Mb in total. Not big, but it made a massive difference. 

If you can't get at least 512MB RIMM off ebay, then it's a good idea to switch to a lightweight DE like LXDE as suggested above.

Also do the same for applications - for example, for word processing instead of using OpenOffice Writer, use Abiword - it use less RAM.

For browsers - try using Opera (install this manually from [www.opera.com](www.opera.com)) - in my experience I've found that Opera work better on low RAM systems - but this is only my experience.

---

