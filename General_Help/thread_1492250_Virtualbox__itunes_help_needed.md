---
title: "Virtualbox / itunes help needed"
date: 2010-05-24
forum: General Help
---

### Post by Quiane on 2010-05-24
Okay, i'm not sure if i'm posting in the right place, if not, sorry!

I have had virtualbox running with an up to date copy of winxp and itunes running without a hitch (for updating my iphone etc).  

I wanted to update to itunes 9.1 and rejailbreak my iphone with the upgraded firmware

i updated to itunes 9.1, and now upon launching itunes it says: **itunes has encountered a problem and must close**

I have tried multiple fixes including - removing all apple folders / registry note / all trace of apple from the xp machine, then restart and reinstall; i have even installed a full new virtual machine running the same xp install (but obviously a clean install) and downloaded 9.1.1 directly from apple, this did not fix this issue. 

So, i'm not sure what to do....there is obviously something throwing the error, but i have no way to troubleshoot this if it's on the ubuntu operating system side....(and not even sure how that could be the case..) 

any help or suggestions would be appreciated.

---

### Post by Joe of loath on 2010-05-24
Sounds like a windows problem. VM's are completely isolated from the host machine, except from things like networking and USB.

---

### Post by MC_Sketch on 2010-05-24
have you tried messing with Songbird? apparently they now have iPhone support.
[http://www.readwriteweb.com/start/2009/06/songbird-releases-iphone-sync.php](http://www.readwriteweb.com/start/2009/06/songbird-releases-iphone-sync.php)

however, Songbird no longer will be updated for Linux, and updated versions will only be available in Windows and Mac from now on. so you might have to download it like iTunes through Wine if you want to continue updating. :P

---

### Post by Joe of loath on 2010-05-24
Doesn't lucid lynx support iphone/itouch etc natively?

---

### Post by Quiane on 2010-05-24
it does to a point, but there were some issues with updating podcasts and i wanted to update the phone OS through itunes.

Hmm..so as far as anyone knows there is no reason that ubuntu would be influencing the itunes install on my VM? 

Back to the drawing board!

---

### Post by Quiane on 2010-05-24
could a network problem be causing the issue?  I have never seen this before....and never not been able to fix it.  I'm wondering because it's occoured in seperate installs of itunes, both in different VM's....? hmm..

---

### Post by Quiane on 2010-05-24
For the record, i have fixed the issue.  I appreciate all the comments and suggestions! :)

It appears that anything above 9.0 won't work on my VM, and so i have installed 8.2...that runs the iphone fine with no issues.

So...tldr: Itunes 8.2 works, 9.0 and up dont for some reason (i think it might have to do with quicktime, but now that i have a working itunes, i'm not into troublshooting it anymore..)

Cheers!

---

### Post by jallain on 2010-06-24
From what I have googled on this problem it appears to be a problem with virutalbox itself and the native virtualization of the host cpu.

---

### Post by birdmanuk on 2010-06-30
I had exactly this problem, along with hundreds of others. I had to enable processor virtualisation in the BIOS. All then will work.

---

