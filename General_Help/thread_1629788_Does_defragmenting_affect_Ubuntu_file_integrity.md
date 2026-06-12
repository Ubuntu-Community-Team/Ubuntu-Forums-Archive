---
title: "Does defragmenting affect Ubuntu file integrity?"
date: 2010-11-24
forum: General Help
---

### Post by TheCosmicFrog on 2010-11-24
Hi everyone,

I dual-boot Ubuntu and Windows 7. Ever since I've started using Ubuntu, Windows 7 has become incredibly slow. I have no idea why. Even browsing the Internet is a painfully slow experience, the few times that I actually *need to* on Windows.

I symlink all my Windows documents, pictures, music etc. to my Ubuntu home folder. When I first started dual-booting, I turned off my auto-defragmenter (IOBit Smart Defrag) because I feared that if Windows started messing with file locations, Ubuntu might lose track of them. 

Is this an unwarranted fear? Is it safe to go defragmenting Windows if both Operating Systems rely on the same files?

Also - if anyone could offer any insight to why Windows performance has hit the deck since I began dual-booting you get triple-super-bonus-points ;)

---

### Post by pawhtiobo on 2010-11-24
What partition format are you using in the Windows and Ubuntu partitions?

---

### Post by a-user on 2010-11-24
> **TheCosmicFrog said:**
> Hi everyone,

I dual-boot Ubuntu and Windows 7. Ever since I've started using Ubuntu, Windows 7 has become incredibly slow. I have no idea why. Even browsing the Internet is a painfully slow experience, the few times that I actually *need to* on Windows.

I symlink all my Windows documents, pictures, music etc. to my Ubuntu home folder. When I first started dual-booting, I turned off my auto-defragmenter (IOBit Smart Defrag) because I feared that if Windows started messing with file locations, Ubuntu might lose track of them. 

Is this an unwarranted fear?
yes
>  Is it safe to go defragmenting Windows if both Operating Systems rely on the same files?
it is as safe as it would be not dual booting.
> 
Also - if anyone could offer any insight to why Windows performance has hit the deck since I began dual-booting you get triple-super-bonus-points ;)
could be coincidence. but it could also be that if you changed files in ubuntu that are cached in windows, windows detects this and loses its cached speed. so what you see is windows "normal" speed.
but this is only a theory.

---

### Post by TheCosmicFrog on 2010-11-24
> **pawhtiobo said:**
> What partition format are you using in the Windows and Ubuntu partitions?

Both are Primary, with Windows being NTFS and Ubuntu being Ext4.

> **a-user said:**
> yes
it could also be that if you changed files in  ubuntu that are cached in windows, windows detects this and loses its  cached speed. so what you see is windows "normal" speed.
but this is only a theory.

That's interesting. I've never heard that before. But it does appear to be very, very slow compared to the way it once was.

---

### Post by oldfred on 2010-11-24
How much did you shrink your windows partition? All systems need some room to work well but windows needs about 30% free with NTFS or it starts to slow down.

---

### Post by TheCosmicFrog on 2010-11-24
> **oldfred said:**
> How much did you shrink your windows partition? All systems need some room to work well but windows needs about 30% free with NTFS or it starts to slow down.

Back when I had just Windows installed, I had two partitions - "OS" (47GB) and "Data" (270GB). I opted to shrink the Data partition and create a 32GB Ext4 partition for Ubuntu.

I currently only have 2GB left in the OS partition. Do you think that could be making all the difference?

---

### Post by oldfred on 2010-11-24
With only 2GB out of 47GB your windows has not space to work. Since it tends to fragment you will have bits of a file all over. And then it takes forever to load anything. If you try to defrag with that little room it may take forever. 

Even in Linux, if you had that little extra room you would be having issues.

---

### Post by TheCosmicFrog on 2010-11-24
> **oldfred said:**
> With only 2GB out of 47GB your windows has not space to work. Since it tends to fragment you will have bits of a file all over. And then it takes forever to load anything. If you try to defrag with that little room it may take forever. 

Even in Linux, if you had that little extra room you would be having issues.

Thanks oldfred. I'll attempt to do some spring cleaning.

This may also explain some recent Ubuntu performance issues...

Many thanks!

---

### Post by WorMzy on 2010-11-24
Windows shouldn't affect Ubuntu's performance and vice versa (more or less*). Although they are on the same disk, they are on *separate* partitions.


*Ubuntu may cause some fragmentation if you mount the NTFS partition and use it to store files, but that can be fixed with a defrag from the Windows side. It'd take a long time with no defragmentation before there was any significant fragmentation.

---

