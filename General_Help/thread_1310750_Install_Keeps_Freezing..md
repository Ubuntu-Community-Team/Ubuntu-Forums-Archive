---
title: "Install Keeps Freezing."
date: 2009-11-02
forum: General Help
---

### Post by hexbomber on 2009-11-02
After the unresolved issues I was having [here]("http://ubuntuforums.org/showthread.php?t=1309062") I decided to backup my /home/ dir, and try a fresh install, as painful as that would be...

I have now run into another odd error when I try to do a fresh install, no matter what I try, my install fails and freezes at:

-| Finishing the Installation |-
---> 26% "Setting users and passwords...".

I am using the alternate install disk, due to encrypted LVM being required.

I have tried both the 64 bit, and 32 bit CD's, both freeze at this point. I have tried not setting user passwords, and setting passwords, to still no avail. I have burned 5 or 6 copies of each version, on different types of DVD media, and still doesn't help.

Has anyone else had this issue?

Some enlightenment would be much appreciated if anyone knows :).

---

### Post by Logan 1229 on 2009-11-06
> **hexbomber said:**
> After the unresolved issues I was having [here]("http://ubuntuforums.org/showthread.php?t=1309062") I decided to backup my /home/ dir, and try a fresh install, as painful as that would be...

I have now run into another odd error when I try to do a fresh install, no matter what I try, my install fails and freezes at:

-| Finishing the Installation |-
---> 26% "Setting users and passwords...".

I am using the alternate install disk, due to encrypted LVM being required.

I have tried both the 64 bit, and 32 bit CD's, both freeze at this point. I have tried not setting user passwords, and setting passwords, to still no avail. 

EXACT same problem here on one of my machines.  Have also tried the regular versions as well as alternate (& have verified discs are 100% OK before install attempts).

Anyone?

---

### Post by GCoffee on 2009-11-06
If you are dual-booting windows, make sure you shutdown the PC correctly, but I would have thought that would have given a error installing the OS itsef.

---

### Post by Logan 1229 on 2009-11-06
> **GCoffee said:**
> If you are dual-booting windows, make sure you shutdown the PC correctly, but I would have thought that would have given a error installing the OS itsef.

No dual boot here. Fresh install with Karmic only on HD.

-----------------------------------------------------------------------------------------
Found this thread (thanks to original poster) which seems to have solved the problem:
[http://ubuntuforums.org/showthread.php?t=1307399](http://ubuntuforums.org/showthread.php?t=1307399)

Basically, when froze at 26%, I forced a reboot (CTRL+ALT+DEL), & removed disc.  Let restart from HD & next thing I know 9.10 booted up.  Seemed to work fine but I decided to re-install to see what would happen (note: at this point I also removed the LVM encryption setup option - which I had tried before with no success).  This time it installed [I]without freezing[I].  Now to test out to see if all works...

---

### Post by D_Wahl on 2009-11-10
I came across this same error while setting up in a VM.  I restarted the setup several time to narrow down the error, and it seems that it only occurs when you select to encrypt the home folder of the admin account during setup.

---

### Post by darkksyde on 2009-11-10
It could be a problem with your graphics or wireless card, they usually cause lockups

---

### Post by Jyx on 2009-11-17
I opened another terminal (ctrl+f1, f2 ...) and then did ```
ps a
``` and killed the process that was named something with "setting up users". I don't really remember the name, but after that the installation finalized. I haven't noticed any problem at all after this.

---

### Post by ZeroEx on 2010-01-05
thanks jyx that fixed it

---

### Post by RJARRRPCGP on 2010-02-21
> **hexbomber said:**
> After the unresolved issues I was having [here]("http://ubuntuforums.org/showthread.php?t=1309062") I decided to backup my /home/ dir, and try a fresh install, as painful as that would be...

I have now run into another odd error when I try to do a fresh install, no matter what I try, my install fails and freezes at:

-| Finishing the Installation |-
---> 26% "Setting users and passwords...".



I think I had the same thing, even though I dunno if it was at "26%". 

It locked up with a Karmic Koala alternate CD I made. It locked up, even when the CD burned fine.

---

