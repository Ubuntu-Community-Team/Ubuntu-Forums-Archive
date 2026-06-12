---
title: "Clicking Sound From Hard Disk"
date: 2009-11-13
forum: General Help
---

### Post by multisystem on 2009-11-13
Firstly, I'm new to ubuntu. It looks a good OS except for some problems.

I have ubuntu 9.10 installed besides Windows XP SP2.

when I run windows there is no problem, but in ubunto there is a low clicking noise from my hard disk.

I searched in google and tested everything, but it's the same.

I downloaded a tool from Western Digital (my hard disk type) and did an extended scan. The final result is that my hard disk's health is good.

tried to disable management power as I read in an article, but it's the same.

Any help is appreciated.

Thanks a lot:)
and sorry for my bad English as I'm not native.

---

### Post by Mark Phelps on 2009-11-13
Unfortunately, just getting "clicking sounds" from a hard drive doesn't say much.  Some drives are noisier than others, to the degree that you can hear very quiet sounds when they're doing intense disk activity.

What you have done is EXACTLY what you should do in such circumstances -- run diagnostics from the drive manufacturer to detect any problems with the drive.

Since their diags passed, unless the noise bothers you, I wouldn't worry about it.

---

### Post by multisystem on 2009-11-13
Thanks for your answer. May be you're right.

But why do I hear this sound on ubuntu only? All things are ok on windows.

also it's not just a normal noise. It's periodic. One click per 2 seconds.

That's really annoying me, but I get tired. I'll not care any more.

Thanks again for your help :D

---

### Post by Mark Phelps on 2009-11-13
> **multisystem said:**
> But why do I hear this sound on ubuntu only? All things are ok on windows.

I'm having to guess, but since you wrote Ubuntu to it's own partition, that's a physically different area of the hard drive than the area that MS Windows is using -- and, for whatever reason, accessing the Linux-formatted area is noisier than accessing the MS Windows-formatted area.

To be safer, I would run fsck against the Ubuntu partition, booting from a LiveCD, to force a file check on the Linux-formatted partition to ensure that you're not getting any filesystem errors.

---

