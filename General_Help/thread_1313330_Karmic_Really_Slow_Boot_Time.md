---
title: "Karmic: Really Slow Boot Time"
date: 2009-11-03
forum: General Help
---

### Post by punkdrummer09 on 2009-11-03
I'm getting really slow boot times on Karmic. Using bootchart, times average around 1:45ish. Can anyone give me suggestions on how to make it faster? I really don't feel like doing a clean install. Any help would be appreciated.

---

### Post by Praxicoide on 2009-11-03
There's an ubuntu-boot ppa which installs a new kernel and readahead. Install at your own risk, obviously, because it could potentially break your system.

sudo add-apt-repository ppa:ubuntu-boot/ppa

A less drastic solution would be to check what services are being brought up at start up (under system, preferences). 

You can also compile your kernel (again, at your own risk), to customize it for your computer.

---

### Post by punkdrummer09 on 2009-11-04
Well I managed to take off two applications(using the less drastic solution), and I still got a 1:49 boot time..so that didn't help...Thanks for the suggestion though.

---

### Post by Praxicoide on 2009-11-04
You could try the PPA then. If you can't get Ubuntu to work correctly after adding and upgrading, you can hit ESC when grub loads, choose the previous kernel, delete this PPA, update sources and reinstall the two packages it installed (linux and ureadahead).

---

### Post by punkdrummer09 on 2009-11-04
Alright, well I might try it. I don't want to break anything lol Thanks for the help.

---

### Post by punkdrummer09 on 2009-11-04
Does any one else have other suggestions? Thanks.

---

### Post by dsnettleton on 2009-11-05
Are you booting from two hard drives by any chance?
Apparently [there's a bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933") that makes GRUB load slowly.  I've been having the same problem.

--D. Scott Nettleton

---

### Post by punkdrummer09 on 2009-11-05
No, I'm using my laptop, so it's only one hard drive.

---

### Post by bach on 2009-11-08
My boot time went down to 33 secs after I started using the readahead kernel. However, my login time (after gdm) is still pretty high: 

51 seconds for a **cold login**
8 seconds for a **warm login** (when I logout and then login again)

I am running Ubuntu 9.10 64 bits (upgraded from 9.04) on a DELL D630 notebook (graphics card: intel). My bootchart is at 

[http://sites.google.com/cribari/linux/](http://sites.google.com/cribari/linux/)

Is there anything I could try to reduce the cold login time? Thanks. 

PS. I am attaching my ~/.xsession-errors file.

---

### Post by punkdrummer09 on 2009-11-13
I did a fresh install and it made things better. Thanks for the help.

---

### Post by irate.turtle on 2009-11-28
[http://arstechnica.com/open-source/reviews/2009/11/good-karma-ars-reviews-ubuntu-910.ars/2](http://arstechnica.com/open-source/reviews/2009/11/good-karma-ars-reviews-ubuntu-910.ars/2)

"Users who do not have solid-state drives can potentially improve their startup performance by disabling sreadahead or replacing it with ureadahead, a new version that is optimized for both solid-state and conventional magnetic hard drives. Unfortunately, ureadahead was not ready in time to be included in the default Karmic installation. It will be rolled out soon as an update in Karmic, but users who want it now can install it from a Personal Package Archive (PPA). Remnant provides instructions on how to set up the PPA in a comment posted on Launchpad."

---

