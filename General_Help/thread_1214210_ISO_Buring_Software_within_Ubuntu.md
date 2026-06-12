---
title: "ISO Buring Software within Ubuntu?"
date: 2009-07-15
forum: General Help
---

### Post by Oizu on 2009-07-15
Just wandering if anyone could recomend a good one? Thanks

---

### Post by Ra-Hoor-Khuit on 2009-07-15
K3b

One of the VERY few KDE apps I'll install on my Gnome desktop.  

[http://k3b.plainblack.com/screenshots](http://k3b.plainblack.com/screenshots)

That or Gnomebaker.

---

### Post by coffeecat on 2009-07-15
> **Oizu said:**
> Just wandering if anyone could recomend a good one? Thanks

Have you already installed Ubuntu? If so, just go to Applications > Sound & Video > Brasero. It's already installed.

I used to use k3b before Brasero came along, but for burning ISOs, Brasero 'just works'.

---

### Post by SuperSonic4 on 2009-07-15
+1 for k3b, it never gets touched

In reality you'll find that all the GUI apps are frontends for a few CLI apps that do the grunt work, **wodim** is one and **makeisofs** is another I beleive

---

### Post by t4thfavor on 2009-07-15
Brasero is installed by default, I use it all the time. Also nautilus has its own burner, which I use too.

---

### Post by ajgreeny on 2009-07-15
And another vote for k3b even on a gnome desktop.

I was asked "why use k3b when brasero works so well?" on another thread recently, and it's mainly because I just do not like brasero and it seems to give me error messages and useless coaster sometimes when, for example, copying data CDs.  I have no idea why.

k3b has never let me down, so is always a must for me on my standard gnome system.

---

### Post by egalvan on 2009-07-15
> **ajgreeny said:**
> And another vote for k3b even on a gnome desktop.

I was asked "why use k3b when brasero works so well?" on another thread recently,
 and it's mainly because I just do not like brasero and it seems to give me error messages and useless coaster sometimes when, for example, copying data CDs.  I have no idea why.

k3b has never let me down, so is always a must for me on my standard gnome system.

**And another vote for k3b even on a gnome desktop.**

Yes to k3b

brasero on Hardy is problematic... I too get many error messages with it...

k3b works well...

and in the end, it's every person's choice...

install several (they're cheap) and try them...
use the one you like the most...

:guitar:

---

### Post by javyn999 on 2009-07-15
Brasero is completely broken for me in Jaunty, only makes coasters.  But I don't mind, I found K3b so I just hide the Brasero shortcut and go on w/ life.

---

### Post by CatKiller on 2009-07-15
Since Brasero is installed by default, I use that. It's always been fine for me. Right click on the image file, select Write to Disc... Simple.

---

### Post by ibutho on 2009-07-15
> **javyn999 said:**
> Brasero is completely broken for me in Jaunty, only makes coasters.  But I don't mind, I found K3b so I just hide the Brasero shortcut and go on w/ life.

Same here. I end up with error messages or coasters when using Brasero. Not a problem when I use K3b.

---

### Post by elliotn on 2009-07-15
For me Brasero does the job

---

### Post by rhchia on 2009-07-15
Brasero for me. but i tried to clone a copy of bootable disc, it does not work. everything else looks fine.

---

### Post by MG37221 on 2009-07-15
k3b has always been my CD/DVD tool of choice.

---

### Post by mjstelly on 2009-07-22
> **coffeecat said:**
> 
I used to use k3b before Brasero came along, but for burning ISOs, Brasero 'just works'.

I'm glad you received the "just works" grace from the Ubuntu gods. Some, like me, weren't so fortunate. I receive nothing but "overburning errors" regardless of the disc type I choose. That's why I'm visiting this thread.

For those like me, I'm gonna try the K3b that some have suggested. 

Thanks all.

---

### Post by Bartender on 2009-07-22
I wonder if this has something to do with the Pc's capabilities?  My budget Core2 Duo Acer laptop has burned several .iso's with Brasero.  No coasters yet.  I don't know if Brasero gives you the option to slow the burn down.  I don't see anything obvious in the Brasero GUI...

---

### Post by coffeecat on 2009-07-23
> **Bartender said:**
> I wonder if this has something to do with the Pc's capabilities?  

Interesting thought. The world seems to be divided between those (like me) who have absolutely no problems with Brasero, and those who have no end of trouble. Anyway...

> **Bartender said:**
> I don't know if Brasero gives you the option to slow the burn down.  I don't see anything obvious in the Brasero GUI...

For burning an ISO: open Brasero and click on "Burn image". In the smaller window that now opens you have to select your image first with the upper button. Then, under "Select a disc to which to write", you select which optical drive you want to use (if you have more than one) with the left button. Finally, with the right one - "Properties" - you can adjust the burning speed. The "Properties" button stays grayed out until you select an image. Perhaps that's why you didn't find it.

You get a similar little window in which you can adjust the burn speed if you select "Data Project" or one of the other choices.

---

### Post by iFuzo on 2009-07-23
Why dont you just mount the disc virtually using kiso?

Terminal and use the command "sudo apt-get install kiso"

Than you can open the application by either typing kiso in the terminal or going Applications > Accessories > Kiso

---

### Post by coffeecat on 2009-07-23
> **iFuzo said:**
> Why dont you just mount the disc virtually using kiso?

That's a nice little app for mounting and extracting ISOs, but this thread is about burning software.

Actually, it's about "buring" software, but let's not quibble. :)

---

### Post by coffeecat on 2009-07-23
> **coffeecat said:**
> That's a nice little app

No, I take that back. It's a horrible little app. It mounts an ISO to ~/.kisotmp/Mount which is owned by root. A root-owned folder in my home folder = BAD. Which means that the ISO-mount icon that appears on the desktop can't be unmounted with an ordinary right-click. You get a "you are not root" message. You have to sudo umount from a terminal and you have to work out the path. OK for an experienced user - baffling for a new user.

Bad design.

Yes, I know that this is just a frontend for the mount command, and that only root can invoke mount, but there must be a better way of doing it.

**Edit:** it gets worse. When I first installed and tried it about a half-hour ago, kiso just started up and mounted an ISO for me. Presumably as root and I thought it odd that it didn't prompt for my password. Perhaps I'd sudo'd within the previous few minutes, Anyway, now when I try to run it I get "Setup - You have to start Kiso as root first". No indication as to how - really off-putting to a Linux newcomer that. This app needs work.

**Edit 2:** Some interesting terminal errors when running 'sudo kiso'

> Error: "/tmp/kde-coffeecat" is owned by uid 1000 instead of uid 0.Well, yes it would be, wouldn't it? And..

> KCrash: Application 'kiso' crashing...Perhaps it works better in KDE. :lol:

Just noticed the "Burn Image" choice, but I think I'll stick with Brasero. :p

```
sudo apt-get purge kiso
```

:wink:

---

### Post by Arup on 2009-07-23
Brasero works fine here, I have one SATA and one IDE burner, have burnt loads of disto CDs with no issues.

---

