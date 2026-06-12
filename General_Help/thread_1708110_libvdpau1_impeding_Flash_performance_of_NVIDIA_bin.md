---
title: "libvdpau1 impeding Flash performance of NVIDIA binary driver?"
date: 2011-03-16
forum: General Help
---

### Post by topdownjimmy on 2011-03-16
Ubuntu Maverick 32-bit, NVIDIA GeForce 9500 GT, with binary driver 260.19.06-0ubuntu1

In the last couple days I started noticing that video in Flash was running very choppily, in Firefox and Chromium, in old and fresh profiles, with Compiz and Metacity, with YouTube and other sites, with Flash 10.2.r152 and 10.3.d180 (beta) -- pretty much under all circumstances.

I had been installing a lot of new packages, so I figured that had something to do with it.  Finally I went to ensure that libvdpau1 was installed, because I had read that that package improved Flash performance on NVIDIA cards by utilizing hardware acceleration.

I found that it was already installed, and also that it hadn't been installed until I installed RecordItNow a couple days earlier.  After removing the package (libvdpau1 0.4-5ubuntu1), Flash immediately began running smoothly again.

So, my question is, why did this happen?  Am I using hardware acceleration or aren't I? CPU and RAM usage appear to be pretty low when running Flash, so I think I am.

What's really troubling is that I installed RecordItNow from the official repositories through Ubuntu Software Center, it had libvdpau1 as a dependency, and installing it made Flash video unbearable system-wide.  It took me a long time to trace the source of the problem, and I'm sure other people who don't have the patience I do, and who (rightfully) feel confident installing anything from official repositories, would consider this a major oversight.

This doesn't feel like a "bug," so I'm not sure filing a report would be appropriate.  What package would I file it against, anyway?  For all I know, all these packages are working properly, they just have some kind of conflict.

Any info would be greatly appreciated, thanks.

---

### Post by pqwoerituytrueiwoq on 2011-03-16
it works better on come computers than others
it works fine on my 32bit lucid desktop
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
edit:
no issues on my 64bit lucid laptop
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
(the following applies to my laptop)
i did not see any improvement i think my gpu uses my processors
any hardware acceleration appears to be done on my cores i get over about 42 FPS on mozilla hardware acceleration test with firefox 4 and basedd on my cpu usage it is done on my cpu not the gpu

---

### Post by topdownjimmy on 2011-05-28
This problem seems to have disappeared in Natty, I am no longer experiencing Flash performance issues with libvdpau1 installed.

edit: I spoke too soon.  I'm still encountering this problem.

---

