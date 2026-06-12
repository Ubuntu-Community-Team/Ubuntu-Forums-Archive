---
title: "Wine + Winecfg"
date: 2006-06-10
forum: General Help
---

### Post by krak on 2006-06-10
When i run winecfg and i click on "Audio" winecfg hangs and i get that error

krak@hal:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c06ea60 ***
wine: Assertion failed at address 0xffffe410 (thread 0033), starting debugger...

i have an audigy card

---

### Post by Patrick-Ruff on 2006-06-10
perhaps a reinstallation?  appollogies if this is a useless post :(

---

### Post by kripkenstein on 2006-06-10
I had this exact problem, different sound card. I believe it was a bug in winecfg, not an issue with your card. I say 'was', because the last update from them seems to have fixed it; it works ok now.

I have wine 0.9.14 (latest, I believe), if you don't have it yet then I suggest upgrading. Otherwise, I can only suggest a reinstall, as Patrick-Ruff says.

---

### Post by =Kevin= on 2006-06-10
Hey I got exactly the same problem as you and the same error.
I got the newest Wine and don't know what to do also..

Any help will be appreciated, and if I happen to come across I'll share it 
ofcourse ;)

---

### Post by krak on 2006-06-11
i have wine 0.9.15 i have reinstall it few times but still error appears. I have not tried older versions.
I think thats the problem "ALSA lib seq_hw.c:456snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory" ahh and i have not installed any drivers for sound i run default Darke drivers.

---

### Post by keithjr on 2006-06-18
I found this post that seems to work:
[http://www.ubuntuforums.org/showthread.php?t=153509&highlight=wine%3A+Assertion+failed](http://www.ubuntuforums.org/showthread.php?t=153509&highlight=wine%3A+Assertion+failed)

The solution is to simple rename the file wine looks for to get ARTS info, as far as I can tell

so you can do something like this:

```

cd /usr/lib/wine
sudo mv winearts.drv.so winearts.drv.so.whatever
```

And then run the audio tab to select a different audio driver.  I went with ALSA, I love ALSA.

---

### Post by krak on 2006-06-19
THX this solution works!
```
cd /usr/lib/wine
sudo mv winearts.drv.so winearts.drv.so.whatever
```

---

### Post by rushseeker on 2007-09-29
Hi
this is my first post!:smile:
I have ubuntu 6.06 dapper

i do : rename winearts.drv.so winearts.drv.so.old
but ubuntu says: 
Bareword "winearts" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "drv" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "so" not allowed while "strict subs" in use at (eval 1) line 1.

I'm noob... 
sorry

---

### Post by rushseeker on 2007-09-29
Resolve 
with
command : move etc.. etc..

---

