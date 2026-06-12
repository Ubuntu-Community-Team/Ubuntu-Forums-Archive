---
title: "wordperfect 8 (again)"
date: 2010-03-19
forum: General Help
---

### Post by Shigoki-linux on 2010-03-19
hi, im trying to install wp8, and i have the files from the corel linux disc on my computer. but when i try to load the file "ldso_1.9.10-1" it gets an error. i uploaded a pic. thanx :)!

---

### Post by bpalone on 2010-03-19
I had wanted to install it some time back, but after research I allowed that it might not be worth effort.  Some of the articles I read indicated that some of the dependancies on older libraries, etc. might cause problems.

If you have the Windows version, it works great in a Virtual Machine.  I even saw some WP-8 new cd sets for sale on ebay here a while back for a very reasonable price.  I have made myself switch to OOo, but sometimes I prefer to use my old WordPerfect and keep it on a VM or three.  And, Yes, I still think it is superior to Office or OOo.

Good luck on getting it installed.  But I would really consider the VM route.

---

### Post by Shigoki-linux on 2010-03-19
ya, that is basically what my fallback is. but i might as well try :). thanx tho!

---

### Post by srs5694 on 2010-03-19
My last install of WP8 for Linux was on an Ubuntu 8.04 system, but even that was very flaky -- I had problems with the file dialog boxes and it would freeze up frequently. My latest desktop Linux installation is a current Gentoo, and I haven't gotten WP8 to run on it at all, although admittedly I've not tried all that hard.

A variant on the VM idea is to run an old version of Linux in a VM -- something from about ten years ago, when WP8 was current. This way, you'd at least be able to SSH into the VM and run WP8 seamlessly next to other applications, enabling easy cut-and-past operations and eliminating some of the (admittedly minor) hassles of switching focus between your main desktop and the VM.

It might also be possible to get it to run by setting up a chroot environment based on an old Linux installation. This is just speculative, though; I've not tried it. I think it'd be more likely to work if your main system is 32-bit rather than 64-bit.

---

### Post by Shigoki-linux on 2010-03-19
yea. that sucks that corel hasnt been active with the linux stuff. thanks for the ideas tho! ill prob go with the VM. unless some other lucky linux guru person gets wp8 running native! what does that "broken pipe" mean tho? just curious.

---

### Post by Shigoki-linux on 2010-04-13
dang. my relatives have hundreds of pages in documents that use wordperfect. i still have little hope for it to work natively on linux. if i knew what broken pipe meant it might help :)

---

### Post by GerryB on 2010-04-13
> **Shigoki-linux said:**
> dang. my relatives have hundreds of pages in documents that use wordperfect. i still have little hope for it to work natively on linux. if i knew what broken pipe meant it might help :)

Hi! If you want Wordperfect just to open files, install OpenOffice - the latest one is very good. It will open any Wordperfect file. Hope this helps.

---

### Post by Mark Phelps on 2010-04-14
According to the WineHQ site page linked below, you've hit upon the sole version of WordPerfect that will NOT work in Ubuntu:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=530]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=530")

---

### Post by srs5694 on 2010-04-14
The OP was asking about the *Linux version* of WP8. Yes, there is (or was) a Linux version of WP8, which was released about a decade ago. Unfortunately, that's old enough that it's become very hard to get it working with modern distributions.

Running a Windows version in WINE might work. My own attempts at this have come frustratingly close to success, but they've always fallen short. (I've tried several versions of WP for Windows, up to WP11.) That said, the last time I tried was at least half a year ago; it's conceivable that the situation has improved recently.

---

### Post by Shigoki-linux on 2010-04-15
thanks Gerry, ill prob just use that. i forgot that it did do that. but just for the heck of it ill try to install WP8 Linux, it like a challenge and as a choleric, i wana finish it lol. thanks for the replies tho!

---

### Post by Shigoki-linux on 2010-04-16
uh...i think i have made progress. :confused:. i have in /usr/lib a few wp8.1 folders. so i THINK i have something installed. i used "dpkg -i --force-depends" and the deb package. i just wana see if i can get it working, just for the heck of it.

---

