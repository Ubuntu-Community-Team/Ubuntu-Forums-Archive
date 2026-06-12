---
title: "Oh no! I have to reinstall windows?!"
date: 2011-09-16
forum: General Help
---

### Post by nslegacy163 on 2011-09-16
I have lived without Windows for about a year but now that I'm back in school I need it just for ease of transfer for programs and assignments I can do at home. The ONLY reason I'm entertaining the idea of reinstalling Windows is because we get Win7 free. So here's the run down:

 I have a Win7 DVD I burned the ISO to. I need to partition my internal drive for Ubuntu, Win7, and some swap space. I know how to do that all, I have gparted LiveCD on a USB drive but here is my problem: When I'm rebooting, I hit f11 to select my boot device and I am greeted with "Enter CURRENT password:" 
 O_o? I don't have one...? I tried live, root, toor, none, admin, default, and my local log in password with no luck. I booted into recovery as well and can get into my root command line so is there a way I can (re)boot from the cmd lind from my USB? 
 All my data/files I don't want wiped are on an external so I'm good for back up. 

 Thanks in advance for the help. 



[http://ubuntuforums.org/showthread.php?t=1844871&referrerid=1246731](http://ubuntuforums.org/showthread.php?t=1844871&referrerid=1246731)

---

### Post by Vaphell on 2011-09-16
most likely that request for CURRENT password comes from BIOS. Check bios settings if it can be disabled.

---

### Post by nslegacy163 on 2011-09-16
> **Vaphell said:**
> most likely that request for CURRENT password comes from BIOS. Check bios settings if it can be disabled.

 Hmmm...don't remember ever setting one and if I did, it was in 2006 so needless to say I have forgotten it. I can't get into the BIOS without it so....suggestions?

---

### Post by TeoBigusGeekus on 2011-09-16
If I understand correctly, this must be the bios password.
Turn off your pc, open your pc case, unplug the motherboard from power, wait for 5~10min, plug it again and give it one more go.
Hopefully this should reset the bios password.

Also, after the bios is reset, go into it and select "Choose optimized settings" (or something).

---

### Post by nslegacy163 on 2011-09-16
> **TeoBigusGeekus said:**
> If I understand correctly, this must be the bios password.
Turn off your pc, open your pc case, unplug the motherboard from power, wait for 5~10min, plug it again and give it one more go.
Hopefully this should reset the bios password.

Also, after the bios is reset, go into it and select "Choose optimized settings" (or something).

I will try this when I'm back at home. But I will say it's difficult to take advice from one with trollface as their avatar. I like the IE Troll though. Do it for the lulz.

---

### Post by Vaphell on 2011-09-16
nah, he's legit :-)

---

### Post by nslegacy163 on 2011-09-16
> **Vaphell said:**
> nah, he's legit :-)

Obligatory: Seems legit.

---

### Post by TeoBigusGeekus on 2011-09-16
> **nslegacy163 said:**
> I will try this when I'm back at home. But I will say it's difficult to take advice from one with trollface as their avatar. I like the IE Troll though. Do it for the lulz.

Also, when you install windows, delete the C:\system32 folder. Your machine will speed up phenomenally...

(Just kidding :biggrin:)

---

### Post by nslegacy163 on 2011-09-16
> **TeoBigusGeekus said:**
> Also, when you install windows, delete the C:\system32 folder. Your machine will speed up phenomenally...

(Just kidding :biggrin:)

Obvious troll is obvious! :lolflag:

---

### Post by TeoBigusGeekus on 2011-09-16
Trolling is a art!

---

### Post by nslegacy163 on 2011-09-16
> **TeoBigusGeekus said:**
> Trolling is a art!

Was that an artoftrolling.com pun? 

Can't tell if coincidence... or just really punny... (Fry face)

---

### Post by nslegacy163 on 2011-09-17
Thanks for the tip! I unplugged the mobo and removed the backup watch battery from it for the night. Just woke up, plugged it all back, booted and BAM into the boot menu! Now time to gpart and get win7 on this piece all before bacon. 

 ):P

---

### Post by TeoBigusGeekus on 2011-09-17
Excellent news!!! Good luck with windows and don't forget to delete the system32 folder :lolflag:

---

### Post by nslegacy163 on 2011-09-17
Will do! Also, maybe you can shed light on my new "issues" I just posted: [http://ubuntuforums.org/showthread.php?p=11259903#post11259903](http://ubuntuforums.org/showthread.php?p=11259903#post11259903)

---

