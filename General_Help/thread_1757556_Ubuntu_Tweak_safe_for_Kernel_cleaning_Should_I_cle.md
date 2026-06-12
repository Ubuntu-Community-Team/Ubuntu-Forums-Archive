---
title: "Ubuntu Tweak safe for Kernel cleaning? Should I clean?"
date: 2011-05-13
forum: General Help
---

### Post by nrundy on 2011-05-13
Every time the Kernel updates, my boot menu grows. It's getting crazy. Why do I need so many "old" kernel versions listed?

Should I "clean" the mess up? Is it safe? 

I've read it's not safe to use "cleaners" cause it can mess stuff up, but I don't see why all those "old" kernel versions need to keep accumulating in my boot menu. should I just let them keep piling up?

Can i get some advice?

---

### Post by drs305 on 2011-05-13
Yes, Ubuntu Tweak does a very good job of cleaning kernels, and will also remove them from you menu. I'd keep at least one older kernel that you know works in case the current one fails when some package is updated.

Of note, in Grub 1.99 (Natty), older kernels are placed in a submenu so your main menu list will not grow as new kernels are added.

I wrote something about removing older kernels. It includes how to install/use Ubuntu Tweak if you aren't familiar with it:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by nrundy on 2011-05-13
Thanks for this info.

Do you recommend using Tweak to periodically clean any other areas of the computer? or just the old kernels?

---

### Post by lithopsian on 2011-05-13
If you don't want a particular old kernel, just uninstall it and it will disappear from Grub.  Each kernel version is a separate package.  **Keep at least one** or you won't be able to boot.

---

### Post by nrundy on 2011-05-13
> **lithopsian said:**
> If you don't want a particular old kernel, just uninstall it and it will disappear from Grub.  Each kernel version is a separate package.  **Keep at least one** or you won't be able to boot.

type "kernel" in software center or synaptic? then select old ones for uninstall?

---

### Post by drs305 on 2011-05-13
> **nrundy said:**
> Thanks for this info.

Do you recommend using Tweak to periodically clean any other areas of the computer? or just the old kernels?

I use UT to clean up all four of the options and haven't had a problem with any of them.

One of the good things about cleaning the kernels with UT is that it won't allow you to remove the currently-running kernel. It does this by not displaying the active kernel in the 'remove' list. (Note that it's always a good idea to know the current kernel you are running.)

---

### Post by jerrrys on 2011-05-13
UT is great for kernel removal and best part all the toys it comes with :)

---

### Post by nrundy on 2011-05-13
Is cleaning the four options with UT primarily to reclaim disk space or does it serve a maintenance/performance upkeep purpose? Basically, if there's plenty of disk space, should users still clean?

---

### Post by drs305 on 2011-05-13
> **nrundy said:**
> Is cleaning the four options with UT primarily to reclaim disk space or does it serve a maintenance/performance upkeep purpose? Basically, if there's plenty of disk space, should users still clean?

To be honest, other than the the menu list issue with the kernels, I don't think you are going to notice a lot of difference unless you are really limited on disk space. 

The 'Clean Packages' feature is the same as 'sudo apt-get clean', which empties downloaded packages from the /var/cache/apt/archives folder. And even if you don't clean it yourself, APT's default settings will eventually limit how much is stored.

---

### Post by demilord on 2011-05-13
sudo apt-get autoremove

---

### Post by lithopsian on 2011-05-13
> **demilord said:**
> sudo apt-get autoremove
This won't remove old kernels.  Old kernels are perfectly valid standalone packages.

autoremove is for removing library packages that are no longer required by any other packages.  I also suggest that when you do autoremove you also use the --purge option, which is equivalent to using purge instead of remove.  Otherwise the package will remain listed in apt but not actually installed, and in most cases this just causes confusion and takes up space.

---

### Post by nrundy on 2011-05-14
> **drs305 said:**
> 
I wrote something about removing older kernels. It includes how to install/use Ubuntu Tweak if you aren't familiar with it:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

hey thanks for this. Great article. thanks for writing it.

Question: I read that when doing a new install with disk encryption that a default install will put 500MB down for the /boot partition. I looked at the kernels piling up on my box and each one is like 99MB. What happens to the /boot partition that has 500MB when more than 5 kernels land on the system?

---

### Post by drs305 on 2011-05-14
> **nrundy said:**
> Question: I read that when doing a new install with disk encryption that a default install will put 500MB down for the /boot partition. I looked at the kernels piling up on my box and each one is like 99MB. What happens to the /boot partition that has 500MB when more than 5 kernels land on the system?

I recall years ago users having problems with full /boot partitions. There was a time that 50MB were recommended. As the kernels got larger, the /boot partition filled up. 

From what I remember, the users started getting error and disk space messages when trying to perform upgrades. In some cases I think the messages even specified there wasn't enough room in /boot, but others were more general in nature.

As much as we can laugh today at the 50MB recommendation, the Grub 2 folder (within /boot) now has lots of module files and more and more seems to be placed there. So some day soon (if not already) we will be laughing at ourselves about recommending 500 MB /boot partitions.

---

### Post by nrundy on 2011-05-14
> **drs305 said:**
> I recall years ago users having problems with full /boot partitions. There was a time that 50MB were recommended. As the kernels got larger, the /boot partition filled up. 

From what I remember, the users started getting error and disk space messages when trying to perform upgrades. In some cases I think the messages even specified there wasn't enough room in /boot, but others were more general in nature.

As much as we can laugh today at the 50MB recommendation, the Grub 2 folder (within /boot) now has lots of module files and more and more seems to be placed there. So some day soon (if not already) we will be laughing at ourselves about recommending 500 MB /boot partitions.

What size do you recommend I make /boot on a new Natty install with encryption? 1GB?

---

### Post by drs305 on 2011-05-14
> **nrundy said:**
> What size do you recommend I make /boot on a new Natty install with encryption? 1GB?

I don't know much about encryption. I know a month or two ago I recommended a 1GB partition for someone with a very large drive and got laughed out of the thread. :p 

But without knowing what's going to be shoved into the /boot or /boot/grub folder in the future, and if you have lots of disk space to spare, I don't think at least 500MB is unreasonable.

---

### Post by nrundy on 2011-05-14
The only thing unique with the encryption is that /boot is its own partition. Same stuff gets put there as on a non-encrypted system far as I know.

I guess when people speak of creating a small /boot partition, they assume the user is regularly going to stay on top of cleaning old kernels. But I've been using Ubuntu for about 5 months now. I just recently learned that I can do this to reclaim space. I can easily see a new user with /boot paritition running into error messages cuase they didn't knwo to clean old kernels.

---

