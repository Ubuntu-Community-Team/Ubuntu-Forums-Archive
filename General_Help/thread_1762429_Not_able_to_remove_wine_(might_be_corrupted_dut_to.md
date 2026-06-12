---
title: "Not able to remove wine (might be corrupted dut to immproper installation)"
date: 2011-05-19
forum: General Help
---

### Post by amit.neo2000 on 2011-05-19
Help Needed...
some Hours ago I was running my PC in UBUNTU 11.04 when suddenly power failure occurred and my pc just switch off without proper shutdown (My power backup device was not working)...
just B4 The power failure i was downloading wine software...
but now when i again starts my PC i figured out that there's some problem with that so i think that i should remove and reinstall it. but now I'm unable to uninstall it... please help...
the error is in the attachment...

---

### Post by jerrrys on 2011-05-19
in terminal enter **sudo apt-get update** 

at the bottom of the printout it may give you errors and maybe instructions on how to fix.

no errors?  ok, try

**sudo apt-get upgrade** and again look at the bottom

---

### Post by amit.neo2000 on 2011-05-20
> **jerrrys said:**
> in terminal enter **sudo apt-get update** 

at the bottom of the printout it may give you errors and maybe instructions on how to fix.

no errors?  ok, try

**sudo apt-get upgrade** and again look at the bottom
thanks... it worked...!!!

---

