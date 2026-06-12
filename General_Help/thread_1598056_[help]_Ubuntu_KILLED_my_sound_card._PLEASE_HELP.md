---
title: "[help] Ubuntu KILLED my sound card. PLEASE HELP"
date: 2010-10-16
forum: General Help
---

### Post by molunbun on 2010-10-16
I recently installed wubi 10.10 and after a while I booted back into Windows 7.
Now my sound on win7 stutters and is crazily loud even the volume is at 1 but the sound is normal on ubuntu.
Is there any chance that ubuntu altered my sound card and now it won't work on Windows?
Then how can I make it work again on Windows? I tried uninstalling wubi but no luck.

Specs:
wubi 10.10 on Windows 7 x86
ASUS Xonar DS
AMD 780G
AMD ATHLON II 250
2*2GB DDR2 RAM

Any help is appreciated.

---

### Post by zaphod777 on 2010-10-16
I highly doubt that Ubuntu caused problems with the Sound card. Did it work fine under Ubuntu? My guess is it is a problem with the Windows driver. I recommend uninstalling the Windows driver and install the latest version.

---

### Post by molunbun on 2010-10-16
> **zaphod777 said:**
> I highly doubt that Ubuntu caused problems with the Sound card. Did it work fine under Ubuntu? My guess is it is a problem with the Windows driver. I recommend uninstalling the Windows driver and install the latest version.
The sound card worked fine on Windows before I installed wubi. I've tried reinstalling the latest Windows driver, no luck.:(Now the sound card only works fine on ubuntu
Does it have anything to do with ALSA?

---

### Post by zaphod777 on 2010-10-16
> **molunbun said:**
> The sound card worked fine on Windows before I installed wubi. I've tried reinstalling the latest Windows driver, no luck.:(Now the sound card only works fine on ubuntu
Does it have anything to do with ALSA?

If it works fine in Ubuntu then it is some problem with Windows. If Ubuntu damaged the card then it wouldn't work in Ubuntu. When Windows is running Ubuntu is not running so there is no interference there. 

My guesses would be open task manager and see what your CPU and RAM usage is when it happens. Also check you disk space on C:/ and defragmenting your C:\ and doing a chkdsk on C:\ couldn't hurt either.

---

### Post by Elfy on 2010-10-16
This is not a windows forum. You might well be better off on one of those.

---

### Post by molunbun on 2010-10-16
> **forestpiskie said:**
> This is not a windows forum. You might well be better off on one of those.
No, it has something to do with ubuntu.
When my ubuntu volume is high, the windows volume will be extremely high even at 1
When my ubuntu volume is low, the windows volume will be extremely low and if I turn it to 100 I can hear some stuttering.

---

### Post by Elfy on 2010-10-16
> **molunbun said:**
> I recently installed wubi 10.10 ... I tried uninstalling wubi but no luck.


So is it installed or not? 

Also you might find that giving people a fighting chance with the type/model of sound card without having to go look will help.

If there is a known issue there will be more chance of finding it.

---

### Post by molunbun on 2010-10-16
some people have the same issue
[http://guide.ubuntuforums.org/showthread.php?t=1519109]("http://guide.ubuntuforums.org/showthread.php?t=1519109")

---

### Post by Elfy on 2010-10-16
So there are - which is what I was saying ;)

> post #5 Update: I contacted the author of the Xonar driver. He said that the windows driver doesn't properly reset the card when it loads. Nevertheless he will take a look at the issue. 

Looks liek there is a fix/patch of sorts in post #9 as well.

---

