---
title: "CD/DVD Drive freezing Ubuntu 10.10"
date: 2010-10-10
forum: General Help
---

### Post by petrasflorin on 2010-10-10
Whenever I put a cd or a dvd into my cd/dvd drive, waiting half a minute, my system completely freezes (like a screenshot) needing a hard reset. I have looked into the matter and found that a lot of people are having this problem. Like them:

[http://ubuntuforums.org/showthread.php?p=8500673](http://ubuntuforums.org/showthread.php?p=8500673)

[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

[http://ubuntuforums.org/showthread.php?t=670943](http://ubuntuforums.org/showthread.php?t=670943)

and many more.
however, nobody knows how to fix this instead of replacing the dvd drive, which is not 100% guaranteed to work.

Can someone please help ?

I just installed a fresh 10.10 on my whole hard drive, gave up Windows completely and here I am, not being able to access my dvds with my work.

---

### Post by petrasflorin on 2010-10-10
OK I've managed to read my DVDS by disabling polling with hal-disable-polling --devie /dev/sr0

However: I can only read one DVD - if I try to change them while in ubuntu: system freeze

I cannot boot ubuntu with a dvd inside the dvd-rom because as soon as it boots, it freezes.

I've had it.

---

### Post by petrasflorin on 2010-10-12
Well computer still freezes from time to time, I can however change (SOMETIMES) DVD/CD by selecting Eject from nautilus menu and not popping them out by hand.

I can't however burn any CD or DVD. I insert a blank one, Ubuntu sees it (and names it Blank CD/DVD etc) but when I try burning them both Brasero and CD/DVD Burning utility behave like there's no cd inside (they burn .iso images instead of the dvd, cd-dvd creator actually warns me that if I want to burn a cd I must insert a blank one into the cd-rom).

I mean WTH it's Ubuntu's problem with my CD/DVD-rom ? I booted up into Windows and burned that CD I wanted with absolutely no problem so the CD/DVD-ROM is fine.

---

### Post by petrasflorin on 2010-10-13
bump. help. I can't burn any CD/DVD - what the hell.

---

