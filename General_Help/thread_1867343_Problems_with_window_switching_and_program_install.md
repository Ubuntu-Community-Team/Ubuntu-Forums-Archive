---
title: "Problems with window switching and program installing"
date: 2011-10-22
forum: General Help
---

### Post by bpward on 2011-10-22
Hey I'm using ubuntu 11.10, just installed it because I have to use it with a molecular simulation package for work.

I am having trouble with a number of things.  Is there a quick guide showing how to navigate between windows or other navigation differences between Windows/Mac?

I see 'Tab' lets me switch through boxes in a single window, but I can't figure out how to always get back to the top of a window to close it.  It seems I can use one window at a time and cannot find the secret buttons to press to let me switch between windows, or click the downsize/close buttons at the top.  Sometimes I hit 'Esc' (I think that's what I hit at least, after I press many random buttons) and I can get back to another window but this is very frustrating.

Also I cannot figure out how to get the java runtime and java developers kit installed, which are required for the simulation software.  I downloaded the .tar.gz files to a USB key but don't know what to do from there.  I cannot find this "Add/Remove Programs" mystery box, wizard, applet, whatever it is as this was said elsewhere to be the easiest way to get the installation going.

Unfortunately I'm also having the wireless network card error many people are having too so I can't just open up the synaptic package manager and find it in there.  Ugh... ubuntu wins, I am defeated.  :cry:

---

### Post by ikt on 2011-10-22
> **bpward said:**
> Is there a quick guide showing how to navigate between windows or other navigation differences between Windows/Mac?

That's a time thing, the more you use ubuntu the easier it becomes, to the point that it's easier to use than windows or mac.

> **bpward said:**
> 
It seems I can use one window at a time and cannot find the secret buttons to press to let me switch between windows, or click the downsize/close buttons at the top.  Sometimes I hit 'Esc' (I think that's what I hit at least, after I press many random buttons) and I can get back to another window but this is very frustrating.

The launcher is on the left, just use it, it's very similar to OSX dockbar, open programs from it and minimise programs to it. The ubuntu software centre is the one that looks like a bag.

> **bpward said:**
> 
Also I cannot figure out how to get the java runtime and java developers kit installed, 

Java run time is easy, just open Ubuntu software centre and search for java.

> **bpward said:**
> 
Unfortunately I'm also having the wireless network card error many people are having too so I can't just open up the synaptic package manager and find it in there.  Ugh... ubuntu wins, I am defeated.  :cry:

I don't understand many of your issues, you are to quick to give up, unless there is something wrong with your system.

Here is what my system looks like:

[http://ikt.id.au/blog/wp-content/uploads/2011/10/wallpaper-at-2011-10-16-034053.png](http://ikt.id.au/blog/wp-content/uploads/2011/10/wallpaper-at-2011-10-16-034053.png)

Does yours look similar?

---

### Post by bpward on 2011-10-23
Well I don't have the toolbar on the left that you have.  I was using my new desktop falcon NW PC to run ubuntu 11.10, but I also have this slightly older gateway laptop here that I could try installing it on.  I might just reinstall on the laptop and see if the wifi card works which would help a lot.

I was reading I needed to have a hard drive partition to get ubuntu going on one page, but the desktop I am using does not have any partitioning.  I just used the ubuntu autoinstaller or whatever it is that sets it up to run behind windows... but that is seemingly at odds with what I was reading about ubuntu requiring a partition?

Anyways thanks for the help, I'm going to install ubuntu to this laptop, which actually has a partition already, to see if I can get the internet going without resorting to fixes.  Oh and I am not quick to give up, I am just trying to finish my PhD in the next 6 months here and things are a bit stressful.  I was not expecting to have to learn a new OS to get this simulation program running!  ;P

---

### Post by gandaran on 2011-10-23
>  I might just reinstall on the laptop and see if the wifi card works which would help a lot.
if you have problems with wifi post the wireless card chipset brand and model in another thread, someone will help if you have to choose and install drivers.
this command shows the internal hardware info
```
lspci
```

---

### Post by 3rdalbum on 2011-10-23
This is non-obvious, but in a maximised window the window management buttons are in the bar along the top of the screen, on the left. They appear when you mouse-over that bar. You also use the top bar to access the menus of the current window.

---

### Post by ikt on 2011-10-23
> **bpward said:**
> I just used the ubuntu autoinstaller or whatever it is that sets it up to run behind windows... but that is seemingly at odds with what I was reading about ubuntu requiring a partition?

Ah! Is that WUBI? And yeah installing on a computer is much better than using WUBI.

> **bpward said:**
> 
I was not expecting to have to learn a new OS to get this simulation program running!  ;P

Think of it as for the best! :D

---

### Post by bpward on 2011-10-24
Yeah I did the install behind windows option.  I'll do a USB key install this time, or should I just put it on my second hard disk that is separated into two partitions?  It probably doesn't even matter that it is partitioned... It doesn't have any OS on it currently, or is the USB key install always the best option?

Will the installation automatically wipe the hard drive clean as well?  Should I clear an entire partition beforehand for it to use?

I just don't have a 2+ GB USB key right now, but I can buy one if it is the best choice for some reason.

---

### Post by oldtimer7777 on 2011-10-24
USB Flash Drive install is the only way to fly..

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **bpward said:**
> Yeah I did the install behind windows option.  I'll do a USB key install this time, or should I just put it on my second hard disk that is separated into two partitions?  It probably doesn't even matter that it is partitioned... It doesn't have any OS on it currently, or is the USB key install always the best option?

Will the installation automatically wipe the hard drive clean as well?  Should I clear an entire partition beforehand for it to use?

I just don't have a 2+ GB USB key right now, but I can buy one if it is the best choice for some reason.

---

