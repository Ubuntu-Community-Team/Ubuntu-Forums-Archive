---
title: "Opera Disc Cache/Memory help"
date: 2009-10-04
forum: General Help
---

### Post by sports fan Matt on 2009-10-04
My machine has 3 gb ram and a 500 gb hard drive.  My question is where should the disc cache and memory cache be set in opera to give it maximum performance?  

Edit: I thought there were tweaks in opera:config as well I could use..no?

Machine is a:  Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop

---

### Post by sports fan Matt on 2009-10-08
Anyone have any ideas?

---

### Post by koftis on 2012-04-15
the solution is [here ]("http://ubuntuforums.org/showthread.php?t=1193567&page=79")

thx to "lovingubuntu"

>  Type *opera:config#UserPrefs|Cache Directory4* in Opera's address bar.
Replace the path with /dev/shm

There is also [B]opera:config#Cache|Application Cache Quota

[/B]If you are changing the disk cache directory to use RAM, then depends on how much RAM you have. The table at [http://www.webgapps.org/tutorials/fi...erences-tweaks]("http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks") might help. 

---

