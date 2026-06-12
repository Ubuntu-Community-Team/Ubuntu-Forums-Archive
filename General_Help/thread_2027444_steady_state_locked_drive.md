---
title: "steady state locked drive"
date: 2012-07-16
forum: General Help
---

### Post by gluckes on 2012-07-16
i've recently gotten a laptop from a friend of mine (dell latitude d620). he's been complaining not being able to change anything. he could make files, and change settings and all that on his win7, but after reboot, everything would just reset so a previous state. so i tried formatting the drive, i tried adjusting the policy settings and anything i could do, but it just resets again.. even when i try installing ubuntu on another partition, or run it from a live cd and then try to format, it still just boots into that win7. any ideas? it's some sort of steady state, but win7 doesn't support that anymore, and it's not some program on the computer. all i can think of is buying a new hd. but i'm not even sure that would work either.

---

### Post by movieman on 2012-07-17
Do you mean solid state?

This sounds like a problem others have reported where they appear to write to the SSD but it's dead and ignores the writes. The files are presumably still in the OS disk cache, so when you read them back they come from the cache and it looks like you've written them correctly, but after a reboot the cache is clear and you're reading from the disk so you read the old data again.

I guess it could happen with a bad hard drive too.

---

### Post by Bucky Ball on 2012-07-17
You could try on a Windows forum ...

But you never know, someone here might have a solution. ;)

---

### Post by gluckes on 2012-07-17
i don't mean solid state, windows had a feature called steady state, in which you could bring your computer in a zero touch state. so any changes you make would be forgotten when you reboot. Handy if you use it for testing etc.. not so handy if you try to reïnstall, or effectively make any changes at all.
and Bucky ball... there is no such thing as a "windows solution" :D

---

### Post by Bucky Ball on 2012-07-17
> **gluckes said:**
>  Bucky ball... there is no such thing as a "windows solution" :D

No, but there is are Windows Forums. I was assuming that this machine was once operational and now it's not. Therefore whatever went wrong with it happened in Windows - which your friend appears to have been using - although you are now trying to fix it with Ubuntu. 

Good luck with it. ;)

---

### Post by Grenage on 2012-07-17
As above, it sounds like either a HD issue/feature, or a UEFI/BIOS feature.  It's not a feature I've ever encountered, so I'd lean towards a HD problem.

It's obviously not a Windows (or security) problem.

---

### Post by matt_symes on 2012-07-17
Thread moved to "General Help"

---

### Post by gluckes on 2012-07-17
the "windows solution" thing was a joke, i'm not specifically trying to fix this in ubuntu. i'm also looking for answers in the windows forum, but i haven't gotten a reply yet. 
what grenage says maybe true, i think the issue may be bios related. but i know it's possible to do this in windows as wel as in the bios. could it be tpm related? i have found one tpm feature in the bios that looks like that could be the problem, but i can't turn it off anymore, i've tried flashing the bios too

---

