---
title: "Fresh install into bigger space and I want to move old home"
date: 2011-08-21
forum: General Help
---

### Post by L a r r y on 2011-08-21
Sorry, somehow I got posted before I got my message written.

I posted my complete question in the next post

---

### Post by L a r r y on 2011-08-21
> **L a r r y said:**
> Sorry, somehow I got posted before I got my message written.


I finally got an Ubuntu LiveCD to actually work, since my first install of 6.06, and was planning on migrating my filesystem over to a bigger partition, and migrating my /home to a bigger partition.  

I think my best bet now is to post a "reply" that contains the intended original post.

Somehow I slid the mouse across the screen and clicked on the save button in the process, sending a barely-started post to public view. :(

**[COLOR="DarkRed"]My intended Original Post[/COLOR]**

**My Computer:**

Ubuntu 10.04 from several upgrades beginning with Kiwi variant 6.06.
/dev/sda6 filesystem  14.xx GiB
/dev/sda7 /home, also 14.xx GiB
Swap partition on /dev/sdb4

Grub bootloader, and two cramped partitions on less than half of an 80 GiB drive, /dev/sda.

Ubuntu 10.04 fresh install from LiveCD
/dev/sdb1 Filesystem about 65GiB
/dev/sdb5 /home about 50GiB
/dev/sdb4 swap on about 2.2GiB


Initially my plan was to copy my sda filesystem over to a sdb partition, and sda /home to another sdb partition.  I was advised to log in as root to accomplish this, and further advised to do it from a LiveCD.

I have created plenty of target practice material trying to get an Ubuntu LiveCD that would work since I burnt a Kiwi 6.06 disc, but Lo and Behold, I got a 10.04 LiveCD!

So my plans changed.  I did a fresh install on /dev/sdb1 and 5.


[SIZE="3"]**I am running Firefox 6.0 on the old install, and Firefox 3.6 on the new.**  Can I just bring my old, relatively recently-created profile from FF 6 over here?[/SIZE]  

I want to stay with Firefox 3.6 and get a benchmark idea of performance on the big drive before I open up for Firefox 4 > 5 > 6.

My issues over there had a lot to do with insufficient space in reserve for the file system, or insufficient space to accomplish any work, take your pick.

Second Question, I will need to add my old installation to the new, never-before Grub 2.  I will have to go into sda6 and do some edits on fstab because the /tmp no longer exists on an sdb partition.  Swap was sdb5 and noiw I have it as sdb4.  Both installs are using the same swap partition.

There's some work I need to get back to on the old installation and keep it going while I migrate to the new, fresh.


Third Question, is it feasible for me to bring old Home over here, since there is a lot of software not yet in place over here on the new?

Thank you for input, and I apologize for the mess I caused opening this thread.

---

### Post by L a r r y on 2011-08-22
I backed-up my .mozilla folder and brought in my old .mozilla folder, everything is in good order.  I just wanted to get this thing running quick, so I asked the question first.

Thanks everyone.

---

