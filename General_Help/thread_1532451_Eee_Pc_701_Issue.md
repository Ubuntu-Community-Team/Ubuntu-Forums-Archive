---
title: "Eee Pc 701 Issue"
date: 2010-07-16
forum: General Help
---

### Post by XenoGuard on 2010-07-16
Hello,
 
I am wondering if anyone can help me with an issue I have on the Asus eee Pc 701 with Ubuntu Netbook 10.4
 
The installation went fine and at first I never had this issue but over the last few days I am unable to shut down or re-start the system without it hanging on the Ubuntu Splash Screen.
 
I have searched for this problem and found some things to try but so far, unless I am doing them wrong they have not helped
 
So far I have tried:
 
Editing /etc/init.d/halt & adding rmmod snd-hda-intel after do_stop
 
This did not work, I also tried adding rmmod snd-hda-intel in the same place TNA.
 
I have also tried adding rmmod snd-hda-intel to the end of the halt file in /etc/default and this did not help either.
 
Is their something I am doing wrong or missing? Or something else I can try.
 
Thanks.
 
P.S - I am fairly new to Linux.

---

