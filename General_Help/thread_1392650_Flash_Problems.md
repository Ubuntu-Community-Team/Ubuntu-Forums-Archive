---
title: "Flash Problems"
date: 2010-01-28
forum: General Help
---

### Post by BarefootSoul83 on 2010-01-28
I have Adobe Flash player 10 installed but it does not seem to be working in firefox... what do I do?

---

### Post by llawwehttam on 2010-01-28
Have a look at this.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you use 64 bit ubuntu adobe flash 10.1 works great though.

---

### Post by BarefootSoul83 on 2010-01-28
So are you saying I need an older version of Flash?

---

### Post by t4thfavor on 2010-01-28
I just posted this to a thread 5 seconds ago.
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html) That x64 flash.

Do this
[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)

If it doesn't work, you have another problem.

---

### Post by BarefootSoul83 on 2010-01-28
uhhhmmm....  I'm running 32bit in Jaunty...(not 64 bit in KK)

---

### Post by t4thfavor on 2010-01-28
Same thing, just don't dl the 64 bit file.

---

### Post by BarefootSoul83 on 2010-01-28
yeah..I already have Flash in that folder...still dont work :(

---

### Post by t4thfavor on 2010-01-28
You have to make sure you don't have other flash plugins installed. So google how to remove flash from ubuntu ${yourversion} and start over from downloading the libflasplayer.so from adobe.

Here is what I have in my folder
/usr/lib/mozilla/plugins$ ls -lah
total 9.5M
drwxr-xr-x 2 root root 4.0K 2010-01-28 08:15 .
drwxr-xr-x 4 root root 4.0K 2009-10-27 14:06 ..
-rwxr-xr-x 1 root root 9.2M 2010-01-28 11:29 libflashplayer.so
-rw-r--r-- 1 root root 6.0K 2010-01-16 11:32 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root 100K 2009-11-11 04:15 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 104K 2009-11-11 04:15 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  72K 2009-11-11 04:15 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  80K 2009-11-11 04:15 libtotem-narrowspace-plugin.so
/usr/lib/mozilla/plugins$ 



Oh, did you restart the browser first?

---

### Post by BarefootSoul83 on 2010-01-28
I only have one Flash installed

---

### Post by JK3mp on 2010-01-28
Is there any symptom in the browser or is it acting as if its not installed at all?

---

### Post by BarefootSoul83 on 2010-01-28
sometimes it does and sometimes it doesnt... sometimes it stays completely blank.... other times it will give you that gray box with the "play arrow" in it

---

### Post by t4thfavor on 2010-01-28
you have flashplugin-alternative.so installed, you just want libflashplugin.so from adobe. there's your issue.


Also see 
[http://ubuntuforums.org/showthread.php?t=1392606&page=3](http://ubuntuforums.org/showthread.php?t=1392606&page=3)

---

### Post by BarefootSoul83 on 2010-01-28
is that the package name if I just want to download it from the terminal? I'm having trouble w/ adobe's site

---

### Post by t4thfavor on 2010-01-28
There is no package for libflashplayer.so, except on adobe.com.

---

### Post by philinux on 2010-01-28
> **BarefootSoul83 said:**
> I only have one Flash installed

Open a terminal.

```
sudo updatedb

then

locate libflashplayer.so
```

Post back the output of the locate command. The updatedb just updates the locate database, no output will result.

---

### Post by Linuxman. on 2010-01-28
[http://forum.donanimhaber.com](http://forum.donanimhaber.com) I can't visit this site.I think,the worst part of Ubuntu is Flash player..

---

