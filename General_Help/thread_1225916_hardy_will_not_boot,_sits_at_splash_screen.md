---
title: "hardy will not boot, sits at splash screen"
date: 2009-07-29
forum: General Help
---

### Post by DrMrHorse on 2009-07-29
I am running two ubuntu versions, jaunty and hardy, on the same system.  They were both working, but now hardy will not boot (jaunty is fine.)  Grub still shows an entry to it, but when booted, it stays on the splash screen forever.  Recovery mode stops on a line about the "generic cd-rom driver."  I am able read, write, and fsck the partition (clean.)  For the record, the cd-rom is a HL-DT-ST DVDRAM GSA-T20L.
Can I even fix this problem without being able to boot from hardy?

---

### Post by DrMrHorse on 2009-07-29
Someone suggested that I disable the cd-rom drive at the BIOS and try to boot, but this did not work either.  Ugh.

---

### Post by nacho32 on 2009-07-29
I have to ask why? why run 2 versions ? your setting your self up for problems while accomplishing nothing. If you your gonna do a dual boot or triple boot do winblows or Mac

---

### Post by DrMrHorse on 2009-07-29
> **nacho32 said:**
> I have to ask why? why run 2 versions ? your setting your self up for problems while accomplishing nothing. If you your gonna do a dual boot or triple boot do winblows or Mac

I am running also windows vista basically to run the sims.

I run hardy as well as jaunty because I have an ati graphics card that is no longer supported by a proper propriety driver, and the OS driver isn't complete yet.  Also, kubuntu hardy runs with kde3.5, which I like a lot, but the new one is kde4, which I like considerable less.
So I accomplish gaming with my hardy install that my jaunty will not.

PS: if i were not running two versions of ubuntu i would be out of luck when one broke down, like is happening right now.  Maybe you should have two installs as well.

---

### Post by nacho32 on 2009-07-29
> **DrMrHorse said:**
> I am running also windows vista basically to run the sims.

I run hardy as well as jaunty because I have an ati graphics card that is no longer supported by a proper propriety driver, and the OS driver isn't complete yet.  Also, kubuntu hardy runs with kde3.5, which I like a lot, but the new one is kde4, which I like considerable less.
So I accomplish gaming with my hardy install that my jaunty will not.

PS: if i were not running two versions of ubuntu i would be out of luck when one broke down, like is happening right now.  Maybe you should have two installs as well.

lol mine is  not broken. I do a dual boot, XP and 9.04 64 bit.
and had windows7 beta on here until it expired, so I had a triple boot, But the qestion is not about me back to your problem.

---

### Post by DrMrHorse on 2009-07-29
I do not believe that my problem stems from dual booting ubuntu versions, as it worked fine before, and I have heard of others doing it successfully.

Opinions aside, I am still looking to resolve this problem.

Failing a perfect fix, I was thinking of attempting to change the partition to one that mounts at /home in jaunty, and installing hardy to another partition.  I understand this would involve edit the grub menu.lst and maybe deleting hidden folders.  Does this sound feasible?

---

### Post by nacho32 on 2009-07-29
well honestly, I would work on the display driver, and partition all to the 9.04 release. As for your question anything is possible in open source.


Back to Guild Wars and GL with your propblem

---

