---
title: "When can we expect a graphical editor for grub2 ???"
date: 2010-07-23
forum: General Help
---

### Post by linuxyogi on 2010-07-23
Hi, does anyone of you known anything about when an application like Qgrubeditor will be released for Grub2 ?

Qgrubeditor was really easy to use. I used to change the background image, the colour of the text and now everything is in black & white.

The most important feature of Qgrubeditor was editing the entries.
After a kernel update/upgrade, simply deleting the old entries was sufficient but now one needs to actually uninstall the old kernel 
in order to get it removed from the grub menu.

It may be possible to accomplish the above mentioned tasks using the Terminal but as a personal preference I always prefer the GUI way. 

Please reply.

---

### Post by linuxyogi on 2010-07-27
Nobody ?:roll:

---

### Post by Bachstelze on 2010-07-27
> **linuxyogi said:**
> Hi, does anyone of you known anything about when an application like Qgrubeditor will be released for Grub2 ?

When someone will 1) be interested in having one; and 2) write it.  You seem to be interested, why not get at it?

---

### Post by clhsharky on 2010-07-27
linuxyogi


Configure a file - copy/past save, delete.
copy/past enter - in terminal.

Basic stuff.
[https://help.ubuntu.com/community/GRUB2](https://help.ubuntu.com/community/GRUB2)

Sharky

---

### Post by linuxyogi on 2010-07-27
> **clhsharky said:**
> linuxyogi


Configure a file - copy/past save, delete.
copy/past enter - in terminal.

Basic stuff.
[https://help.ubuntu.com/community/GRUB2](https://help.ubuntu.com/community/GRUB2)

Sharky

Thanks a lot for your reply.

I just changed the grub menu background image. :D Success !!!


Alt+F2 ------gksu gedit /etc/grub.d/05_debian_theme

WALLPAPER="path to image"

That did it.

After changing text colour I will try grub2 theming. 

I asked about a gui editor because I used Qgrubeditor since hardy but as you said this is really easy too.

Thanks again.

---

### Post by deepredblood on 2010-12-26
> **Bachstelze said:**
> When someone will 1) be interested in having one; and 2) write it.  You seem to be interested, why not get at it?

Because not everyone's a programming nerd.

Maybe you should use that same answer and attitude the next time you see a need for something or invention that you yourself aren't able to make happen.

Otherwise very ignorant answer.

---

### Post by rage28 on 2011-01-13
Check this..
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by wkulecz on 2011-01-13
Am I the only one that thinks having a graphical configuration editor and a bunch of eye candy in a boot loader is counter productive?

I want the dam thing to boot quickly as possible and have a reasonable way to edit/offer boot options, if any.  IMHO anything more is a waste of effort -- I only care about the boot loader if it doesn't work, which is way too often since the switch from grub to grub2!

Multiboot systems are a PITA to maintain, but I need them for lack of physical space, but I'd rather have one box per system and an N port KVMA switch if I could.

---

### Post by Rubi1200 on 2011-01-13
There is a new graphical application for GRUB2:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

drs305 explains the basics in the thread.

---

### Post by linuxyogi on 2011-01-14
> **Rubi1200 said:**
> There is a new graphical application for GRUB2:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

drs305 explains the basics in the thread.


> **rage28 said:**
> Check this..
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thanks for the info.

I will install it as soon as it is included in the ubuntu repos.

Personally I rarely install anything other than apps offered in the Ubuntu repos. 

Again, very useful info.

---

### Post by Rajiev on 2011-03-29
> **deepredblood said:**
> Because not everyone's a programming nerd.

Maybe you should use that same answer and attitude the next time you see a need for something or invention that you yourself aren't able to make happen.

Otherwise very ignorant answer.

Amen to that.
With the complexity of modern world, NO BODY can do everything they want by themselves. That's why we have different professions. :p ( I wonder he/she operate himself, make his car himself :D)

Aw, IMHO, these kind of command line editing that stems from old Ubuntu projects is the only thing that keep newbies away from Ubuntu :( In this case, Ubuntu CAN learn from windows :p

---

