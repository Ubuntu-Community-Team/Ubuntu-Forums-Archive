---
title: "Can't Suspend or Hibernate"
date: 2010-04-13
forum: General Help
---

### Post by TheCosmicFrog on 2010-04-13
Hi guys. I recently installed Ubuntu 10.04 Lucid Lynx. When I partitioned my HDD, I ran  out of available partitions and so couldn't make a Swap Partition. I  pushed on anyway, because I read [here]("http://www.techmetica.com/howto/add-a-swap-file-or-expand-existing-swap-space-in-ubuntu/")  that you can create a Swap File instead of a partition that does the  same thing. I've made the Swap File and it's activated (I know because  during shutdown there's a message that flashes very quickly that says  "Deactivating Swap [OK]".


But here's the real problem. My  Ubuntu refuses to Suspend or Hibernate. The screen just goes black and  the backlight stays on. Since one of the main functions of the swap file  is to facilitate Suspend and Hibernate, I can only assume this is the  issue. I upgraded from 9.10 Karmic Koala, which suspended and hibernated normally. I'm just hoping someone can help me out?
 


Thanks,
Aaron.

---

### Post by wilee-nilee on 2010-04-13
I suspect a swap file and swap partition do the same thing while the computer is running, but the shut down would  seem to need a script to save ram to a file on the same partition. I am not sure here just a shot in the dark. 

I assume your swap file is at least equal or larger then your ram size.

---

### Post by TheCosmicFrog on 2010-04-13
> **wilee-nilee said:**
> I suspect a swap file and swap partition do the same thing while the computer is running, but the shut down would  seem to need a script to save ram to a file on the same partition. I am not sure here just a shot in the dark. 

I assume your swap file is at least equal or larger then your ram size.

Yeah, it's 3GB - plenty :)

---

### Post by wilee-nilee on 2010-04-13
> **TheCosmicFrog said:**
> Yeah, it's 3GB - plenty :)

The only other thing I notice is that the setup for fstab is for mounting on boot, with suspend /hibernate neither are booting. This may not be the problem though.

Hope you get it figured out to work I had never heard of this.

---

### Post by TheCosmicFrog on 2010-04-13
> **wilee-nilee said:**
> The only other thing I notice is that the setup for fstab is for mounting on boot, with suspend /hibernate neither are booting. This may not be the problem though.

Hope you get it figured out to work I had never heard of this.

Yeah, I'm hoping someone can help me because this is really bothering me.

---

### Post by TheCosmicFrog on 2010-04-14
Can anyone help?

---

### Post by Bungler on 2010-04-14
During installation have you selected the "encrypt home folder" function because this also causes either the suspend or hibernate not to work. I don't recall why, but I know in 9.10 it still had to be fixed.

---

### Post by TheCosmicFrog on 2010-04-14
> **Bungler said:**
> During installation have you selected the "encrypt home folder" function because this also causes either the suspend or hibernate not to work. I don't recall why, but I know in 9.10 it still had to be fixed.

I honestly can't remember. Is it default?

---

### Post by TheCosmicFrog on 2010-04-14
I hate to bump this, but I still really need help with this. I need to be able to use the Suspend feature.

---

### Post by Bungler on 2010-04-15
No, home folder encryption is not default.
Does your swap file work? Can you see it at the system monitor?
Is just a proper re-installation not a solution, with SWAP file? I know suspend hibernate is already tricky by default. You didn't have to do any fixes on previous versions of ubuntu?It might be a new bug see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554695](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554695)

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560966](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560966)

You can try to update to the new kernel. Which is suggested in the bug reports

---

### Post by TheCosmicFrog on 2010-04-15
> **Bungler said:**
> No, home folder encryption is not default.
Does your swap file work? Can you see it at the system monitor?
Is just a proper re-installation not a solution, with SWAP file? I know suspend hibernate is already tricky by default. You didn't have to do any fixes on previous versions of ubuntu?It might be a new bug see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554695](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554695)

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560966](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560966)

You can try to update to the new kernel. Which is suggested in the bug reports

My swap file works, yes. And yes, it's on the System Monitor.

I already have updated to a newer kernel, but no luck. I never had an issue with this before.

---

### Post by TheCosmicFrog on 2010-04-17
Updated to another kernel since and still no luck. Anyone have any other ideas?

---

### Post by TheCosmicFrog on 2010-04-29
I really don't want to have to reinstall. Is there anything I can try?

---

