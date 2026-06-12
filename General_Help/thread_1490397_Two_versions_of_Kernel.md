---
title: "Two versions of Kernel???"
date: 2010-05-22
forum: General Help
---

### Post by oxf on 2010-05-22
I was just looking at my Grub menu. I see I have two Kernel versions listed
The menu list goes something like this:

2.6.31-21 Generic
2.6.31-21 Recovery
2.6.31-14 Generic
2.6.31-14 Recovery
Memtest
Windows XP

I (presume?) this resulted after I ran a bunch of updates a while back. 

My question is this. Do I really have two kernels installed? and one being redundant and taking up wasted space? If so can I safely remove it?

Thanks

---

### Post by wojox on 2010-05-22
General rule of thumb is to have two kernel accessible in case you newest one goes wonky on you.

You could remove it if you feel comfortable. Run:

```
sudo apt-get purge linux-image-2.6.31-14-generic
```

```
sudo update-grub
```

---

### Post by John Bean on 2010-05-22
> **oxf said:**
> Do I really have two kernels installed?

Yes.

>  and one being redundant and taking up wasted space? If so can I safely remove it?

If you have no operational issues with the newer kernel then yes, you can remove the older version to save space.

---

### Post by WorMzy on 2010-05-22
You can remove kernels you don't want by running synaptic, searching for the kernel, and removing it's headers and image. For example, to remove kernel 2.6.32-21-generic, I'd need to remove "linux-image-2.6.32-21-generic", "linux-headers-2.6.32-21-generic" and "linux-headers-2.6.32-21". You'll have to manually delete the initrd.img files for each kernel though, they're not installed, they're generated.

It's advisable to keep at least one backup kernel that you know works fine, just in case you need it.

After you've uninstalled the kernels, run ```
sudo update-grub
``` if you're using grub2, or manually edit menu.lst if you have grub legacy.

---

### Post by oxf on 2010-05-22
OK I take your points about having a backup version. However, until a few days ago when I ran some updates I only had one anyway. I only noticed this last night when I realised my Grub menu was a lot longer!

---

### Post by John Bean on 2010-05-22
> **oxf said:**
> OK I take your points about having a backup version. However, until a few days ago when I ran some updates I only had one anyway. I only noticed this last night when I realised my Grub menu was a lot longer!

Erm... one of the updates was the new kernel. Before the update it didn't exist, so...

If the reasoning behind not automatically removing a working kernel after update isn't clear, imagine the situation if the newly updated version wouldn't boot for whatever reason.

---

### Post by WorMzy on 2010-05-22
Yes, Canonical periodically add updated kernels to the repos, which your system will tell you about through the update manager. If you'd rather not get updated kernels, then open synaptic, search for linux-image-generic, mark it for removal, and apply changes. That package (and the other packages associated with it) make sure you always have the most up-to-date kernel, removing them stops them telling you about updated kernels.

This isn't advisable though, the kernel is the core of the Linux OS, if there's updates available for it, then they're generally beneficial to the system as a whole, making it more compatible with more hardware, fixing some problems, etc.

---

### Post by oxf on 2010-05-22
Oh I have no problem getting kernel updates. Just the new entry in Grub suprised me. I guess I'll leave it for a few days to check all is OK then remove it

---

### Post by oxf on 2010-06-02
> **WorMzy said:**
> You can remove kernels you don't want by running synaptic, searching for the kernel, and removing it's headers and image. For example, to remove kernel 2.6.32-21-generic, I'd need to remove "linux-image-2.6.32-21-generic", "linux-headers-2.6.32-21-generic" and "linux-headers-2.6.32-21". You'll have to manually delete the initrd.img files for each kernel though, they're not installed, they're generated.

It's advisable to keep at least one backup kernel that you know works fine, just in case you need it.

After you've uninstalled the kernels, run ```
sudo update-grub
``` if you're using grub2, or manually edit menu.lst if you have grub legacy.

So where are the initrd.img files located then? 
I assumed they would be in /boot
If thats the case they were removed automatically when I ran "sudo apt-get purge...."
Because the only ones I can see relate to 2.6.32-21 the kernel I'm using

---

### Post by elliotn on 2010-06-02
I too hve 2 kernels... Guess I must remove the old one

---

### Post by WorMzy on 2010-06-02
They should be in /boot, if they aren't, then I guess they must have been removed by purge.

@ elliotn: No. You don't -have- to remove the old one, but you -can- if you want to. Having both kernels installed will not cause any problems.

---

### Post by JoelOl75 on 2010-06-02
No need to 'purge' or rerun the update-grub command... or delete the initrd images.  All this is done by the postrm script.

The best way I found is run synaptic and search for 2.6.32 and remove anything referring to older versions.  Make sure to leave the newest of course.

Bascially it's just the headers, the header-generic and the image, but if you are running backported wireless modules or alsa modules these older versions should be cleaned up as well.  In older releases (pre-karmic IIRC) there's also restricted module packages to remove as well.

Also running sudo apt-get clean and sudo apt-get autoremove will free up some more space. These commands clean out previously downloaded packages and orphaned packages respectively.

---

