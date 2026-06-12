---
title: "Everything freezes for 5-10 minutes randomly"
date: 2009-11-07
forum: General Help
---

### Post by kelcey_s on 2009-11-07
Hi,

I have searched everywhere and had no success. Every version of Ubuntu since dapper freezes randomly for 5 to 10 minutes, no keyboard (not even caps lock and num lock lights), no mouse movement, no ssh login, and the sound seems to play the last half second of buffer on repeat for the duration. I just installed a fresh version of karmic in the hope it would help, but it does not (after installing the nvidia drivers which I cannot live without).

I have read on some threads that it is likely to be a conflict between my nVidia card and CPU scaling, so I set powernowd to stop on login. That didn't work. I set /etc/init.d/powernowd to exit 0 after the first line. Didn't work.

Ubuntu has worked perfectly on my laptop for years but I have had to resort to windows on my desktop for a long time now because of this problem so I would really appreciate any help. Also, I have not been able to find anything in the logs firstly because I am not sure what I am looking for and secondly because when my computer does decide to carry on it pretends like nothing has happened and continues with whatever it was doing before the freeze.

I have saved an hwinfo and a lshw if it helps, but my video card is a GeForce 7600 GS and my motherboard claims to be RC4107MA-RS2H

I really hope someone can help me.

---

