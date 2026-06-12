---
title: "apport-gpu-error-intel.py?"
date: 2012-05-07
forum: General Help
---

### Post by Zane Pepper on 2012-05-07
[I]I keep getting this error every time I log in.
apport-gpu-error-intel.py
[IMG]http://sadpanda.us/images/952713-R2YT5NU.png[/IMG]
[/I]

---

### Post by jedimasterk on 2012-05-07
Not sure. I've been getting internal errors for a variety of reasons, with 12.04. Both after fresh install, and when I was trying 12.04 out in virtualbox.

---

### Post by Zane Pepper on 2012-05-07
> **jedimasterk said:**
> Not sure. I've been getting internal errors for a variety of reasons, with 12.04. Both after fresh install, and when I was trying 12.04 out in virtualbox.

Maybe it has some bugs that still need squashing? If that is the case, they should be repaired in updates soon.

---

### Post by Bartender on 2012-05-08
Zane, you gotten anywhere with this?  What's your chipset?

I just installed 12.04 32-bit to a Dell GX520 this morning.  Getting the same error message on startup.  I tried 2D, 3D, a different video setting in BIOS, nothing.  The Dell is running the Intel 82945G chipset, and it seems the onboard video is what's causing this error?

EDIT: The GX520 has a Radeon 9250 low-profile video card inside.  Anyone know if there's a way to tell Ubuntu to just ignore the onboard GPU?  That might get me around this issue.

---

### Post by Zane Pepper on 2012-05-09
> **Bartender said:**
> Zane, you gotten anywhere with this?  What's your chipset?

I just installed 12.04 32-bit to a Dell GX520 this morning.  Getting the same error message on startup.  I tried 2D, 3D, a different video setting in BIOS, nothing.  The Dell is running the Intel 82945G chipset, and it seems the onboard video is what's causing this error?

EDIT: The GX520 has a Radeon 9250 low-profile video card inside.  Anyone know if there's a way to tell Ubuntu to just ignore the onboard GPU?  That might get me around this issue.

No, I have not. I believe this is my chipset [I am on a laptop] - [http://ark.intel.com/products/chipsets/26558?wapkw=gl960](http://ark.intel.com/products/chipsets/26558?wapkw=gl960).

---

### Post by yugn on 2013-03-07
Isn't there any solution for this error?

I'm using i3 (3225) GPU,H77 chipset,Gigabyte H77-N wifi motherboard,  ubuntu 12.10 server. I had this error all the time and kept coming back every 1 min. 

[IMG]http://users.tpg.com.au/gnyu80/ubuntu/Screenshot+from+2013-03-07+07_40_16.png[/IMG]

Have to try temporary solution to disable xdiagnose.

[http://askubuntu.com/questions/153016/apport-gpu-error-intel-py-crash](http://askubuntu.com/questions/153016/apport-gpu-error-intel-py-crash)

---

