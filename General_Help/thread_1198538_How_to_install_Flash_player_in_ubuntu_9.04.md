---
title: "How to install Flash player in ubuntu 9.04"
date: 2009-06-27
forum: General Help
---

### Post by brad_pitt on 2009-06-27
I just upgraded my OS from Ubuntu 8.10 to Ubuntu 9.04 since then Flash in firefox is not working.

I unistalled flash player and tried reinstalling but still not working.

tried of googling but still no luck

Any help is highly appreciated.

Regards
Brad

---

### Post by kokkus on 2009-06-27
FIrst of all. Which flash plugin did you install?
You should install the one thats recommanded by ubuntu.
Run this in terminal
sudo apt-get install ubuntu-restricted-extras

This little thing includes all video, flash, audio and java codecs and plugins you need.

---

### Post by brad_pitt on 2009-06-27
> sudo apt-get install ubuntu-restricted-extras

This little thing includes all video, flash, audio and java codecs and plugins you need. 	

I dont think this is a little thing because it is 107MB in size and it took 45 min for my internet speed to install..But that did not solve my problem?

Can any body out there help me?

Regards
Brad

---

### Post by Ayuthia on 2009-06-27
Are you using 32 or 64 bit?

---

### Post by brad_pitt on 2009-06-27
> Are you using 32 or 64 bit? 	

I am using 64 bit..

I just downloaded flashplayer directly from adobe site(.deb) but it is showing wrong architecture i386.

Please help me..

Regards
Brad

---

### Post by entr3p on 2009-06-27
> **brad_pitt said:**
> I am using 64 bit..

I just downloaded flashplayer directly from adobe site(.deb) but it is showing wrong architecture i386.

Please help me..

Regards
Brad

Type this in your terminal:
```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo bash ./flash10_en.sh
```

---

### Post by del_diablo on 2009-06-27
Oh that :P
Flash alpah of 10 in 64-bit is Linux only, that is the good news. The bad news is that i suck at searching the download page up <.<

---

### Post by brad_pitt on 2009-06-27
> Code:
     wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo bash ./flash10_en.sh[FONT=monospace]
[/FONT]This solved directly my problem.

Thanks Buddy

Brad

---

### Post by USFMD82 on 2009-07-28
> wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo bash ./flash10_en.sh

This worked for me but only for a few minutes :(

---

