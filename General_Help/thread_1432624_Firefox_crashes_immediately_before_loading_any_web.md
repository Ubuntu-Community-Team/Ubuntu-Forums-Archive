---
title: "Firefox crashes immediately before loading any website"
date: 2010-03-18
forum: General Help
---

### Post by ldp_frog on 2010-03-18
Hi everyone,
I'm Dual-booting XP with Ubuntu Karmic Koala, heres my other specs:

CPU: Intel Pentium D 3.0Ghz family(15) model(4) stepping(4)
GFX: Geforce 7800 GT (had problems with GFX when I first installed Ubuntu, I had to update my drivers)
2 GB RAM

This is a nearly fresh install of Karmic Koala, I've only installed whatever updates I needed, graphics card drivers, KPlayer, and Google Chrome. Because I prefer Chrome over Firefox I immediately went to download Chrome, and Firefox would get to the Chrome page and then crash. I then got the Chrome install file from another computer and installed it. Chrome will not even launch, so I go to search the problem in Firefox and it crashes on ANY link I click in Google Search. I also tried to directly type websites into the URL box: it loads the pages title (Ex. "Yahoo! Mail"), and crashes before displaying the page at all.

This is a very odd problem to me as I used the same disc to install dual-boot with Win7 and Ubuntu on my laptop which works perfectly, and now this happens to my desktop.

Your help is much appreciated, I've described this as best I can.

Matt

---

### Post by wjm on 2010-03-18
invoke Firefox from a terminal window and upon crash, attach the output of the crash to this thread.  That might help people figure out what is happening.  I suspect it's flash or will be a GLIB error though since those are the two most popular.

---

### Post by ldp_frog on 2010-03-18
When I launch firefox from the terminal it says:
```
(firefox:2002): GLib-WARNING **:g_set_prgname() called multiple times
```
When I try to go to a website, Firefox crashes and the terminal says:
```
bus error
```

---

### Post by wojox on 2010-03-18
Try this: [http://lovinglinux.megabyet.net/?page_id=220#Firefox-can%27t-connect-to-any-sites,-but-other-browsers-work-2](http://lovinglinux.megabyet.net/?page_id=220#Firefox-can%27t-connect-to-any-sites,-but-other-browsers-work-2)

---

### Post by ldp_frog on 2010-03-18
Didn't work =(

---

### Post by ldp_frog on 2010-05-13
bump.

Been almost 2 months and still no ubuntu on my deskop :(

---

### Post by 1doRa on 2010-05-13
Before I continue,I must say im an absolute beginner to ubuntu.

Anyways, from what I know, a bus error is caused when the cpu can't access memory. So my guess is that there must be some hardware compatibility issues of some sort.

You can use this command
```
lspci
```If it lists something as "unknown" then you have an issue. So you will have to search for your drivers and install it.

do forgive me if it does not work :D

---

