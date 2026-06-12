---
title: "Re-Installing windows?"
date: 2010-07-03
forum: General Help
---

### Post by lazyrobot47 on 2010-07-03
Ok, so I'm having some minor hardware issues and stuff (nothing I can't live without) but I want to reinstall windows 7 as a dual boot for some things i cant get on here. Im still going to use ubuntu as my main OS, but I'd like to have windows back, just for some convenience.

What I want to do:
Set up my hard drive so the OS's are both on there, and still have all my documents accessible in both. Would I have to partition my hard disk with 3 partitions and have one accessible by both? Is that even possible? (I was thinking 50 to windows and its programs, 50 to ubuntu and its programs, and the other 400 to everything else.)

Also, I don't really want to have to reinstall ubuntu and re set up my settings and all my tweaks, so is there any way to do the partitioning without affecting ubuntu?

EDIT: There is a windows 7 product key on a sticker on the bottom of my laptop. can i use that key with a home premium installation disk (i can obtain one.), or would windows claim its already registered, even though i uninstalled it?

I do have a system restore disk set i made in windows, could i reinstall windows as a dual boot off that and not have to get a key for it?

thanks a ton guys. Im bashing my head against the wall in frustration trying to figure it all out.

---

### Post by Seanlol on 2010-07-03
> **lazyrobot47 said:**
> Ok, so I'm having some minor hardware issues and stuff (nothing I can't live without) but I want to reinstall windows 7 as a dual boot for some things i cant get on here. Im still going to use ubuntu as my main OS, but I'd like to have windows back, just for some convenience.

What I want to do:
Set up my hard drive so the OS's are both on there, and still have all my documents accessible in both. Would I have to partition my hard disk with 3 partitions and have one accessible by both? Is that even possible? (I was thinking 50 to windows and its programs, 50 to ubuntu and its programs, and the other 400 to everything else.)

Also, I don't really want to have to reinstall ubuntu and re set up my settings and all my tweaks, so is there any way to do the partitioning without affecting ubuntu?

EDIT: There is a windows 7 product key on a sticker on the bottom of my laptop. can i use that key with a home premium installation disk (i can obtain one.), or would windows claim its already registered, even though i uninstalled it?

I do have a system restore disk set i made in windows, could i reinstall windows as a dual boot off that and not have to get a key for it?

thanks a ton guys. Im bashing my head against the wall in frustration trying to figure it all out.

You should be able to access both partitions from both OSes if you give yourself the proper permissions. There's no need for a third partition unless you -really- want one.

You can create the second partition via the Windows install CD without affecting the Ubuntu partition.

You should be able to use your Windows 7 key without problems. At the installation, windows only checks to see if the key is valid at all. It is, so it will work. They will only lock your key if they see the key trying to get Windows updates from 2 different machines at the same time.

I don't believe you can do a complete reinstall Windows from a system restore disk, but it's been awhile since I've tried something like that. Someone more familiar with Windows 7 than I can give you a better answer.

---

### Post by Elfy on 2010-07-03
> ...so is there any way to do the partitioning without affecting ubuntu?Use the partition editor in the livecd to resize existing partitions - create a new one for win in the empty space.

> Would I have to partition my hard disk with 3 partitions... 
No - ubuntu will access the ntfs partitions - you'll have more trouble accessing linux partitions from win.

---

### Post by Yarui on 2010-07-03
> **lazyrobot47 said:**
> Ok, so I'm having some minor hardware issues and stuff (nothing I can't live without) but I want to reinstall windows 7 as a dual boot for some things i cant get on here. Im still going to use ubuntu as my main OS, but I'd like to have windows back, just for some convenience.
Have you tried asking about these issues on the forums here? They may be fixable.

> **lazyrobot47 said:**
> Also, I don't really want to have to reinstall ubuntu and re set up my settings and all my tweaks, so is there any way to do the partitioning without affecting ubuntu?
This is definitely doable.  Seanlol says the Windows 7 CD can do it, but I can't personally vouch for that.  Even if that weren't true, though, there are plenty of utilities that allow you to resize partitions without damaging the data that's already on them.

> **lazyrobot47 said:**
> There is a windows 7 product key on a sticker on the bottom of my laptop. can i use that key with a home premium installation disk (i can obtain one.), or would windows claim its already registered, even though i uninstalled it?
If the key is for home premium then you most likely can.  I remember with Windows XP sometimes the disks for a Dell copy of home wouldn't work with non-Dell XP home CD keys for some reason, I'm not sure if this is still an issue with Windows 7.

---

### Post by Seanlol on 2010-07-03
> **forestpiskie said:**
> Use the partition editor in the livecd to resize existing partitions - create a new one for win in the empty space.


The Windows install CD will allow you to create a new partition for Windows right before you install.

EDIT: or at least the Windows XP/Vista CDs would. I don't see why they would have ditched this in Windows 7.

EDIT2: Didn't see you had a Dell. Yeah, sometimes Dells can be a PITA, but it should still go alright. If Dell hasn't fixed that problem by now, they must be the most incompetent company on the face of the Earth.

---

### Post by Elfy on 2010-07-03
> **Seanlol said:**
> The Windows install CD will allow you to create a new partition for Windows right before you install.

I would be surprised if a windows install disc had the functionality to shrink a linux partition  - long time since I used a win disc though.

---

### Post by Seanlol on 2010-07-03
> **forestpiskie said:**
> I would be surprised if a windows install disc had the functionality to shrink a linux partition  - long time since I used a win disc though.
Actually -- good point. I can't say I've ever tried to install Windows alongside Linux. I've always installed Linux after Windows or gone straight Linux. But I do know that Windows will let you create and delete partitions. You can try it and see if it will work.

---

### Post by Yarui on 2010-07-03
> **Seanlol said:**
> Didn't see you had a Dell. Yeah, sometimes Dells can be a PITA, but it should still go alright. If Dell hasn't fixed that problem by now, they must be the most incompetent company on the face of the Earth.
There was no mention of a Dell in the OPs post, I was just speaking in general.  If he does happen to have a Dell or if the CD he is getting happens to be a Dell disk, it could be an issue.

---

### Post by lazyrobot47 on 2010-07-03
I'm currently rocking a Gateway. Thanks for the help you guys!
Im probably going to download a copy of win7 and make my own install disk, and use that liveCD tip for resizing the partition. I have asked about the issues, but Im stuck in a rut as i cant find some information as to  the actual pieces of hardware on here.

---

### Post by Yarui on 2010-07-03
> **lazyrobot47 said:**
> I'm currently rocking a Gateway. Thanks for the help you guys!
Im probably going to download a copy of win7 and make my own install disk, and use that liveCD tip for resizing the partition. I have asked about the issues, but Im stuck in a rut as i cant find some information as to  the actual pieces of hardware on here.
lspci is a wonderful utility for finding the exact hardware in your system.

Also, if you feel that you have found the solution to your problem, don't forget to mark the thread as [solved].

---

### Post by lazyrobot47 on 2010-07-03
I was going to mark as solved upon the dual boot itself being a success

---

### Post by Yarui on 2010-07-03
> **lazyrobot47 said:**
> I was going to mark as solved upon the dual boot itself being a success
Good point.  So did lspci do what you wanted as far as finding your specific hardware or were you looking for something a little different?

---

### Post by lazyrobot47 on 2010-07-03
Also, with lspci it doesn't tell me what kind of webcam and internal microphone i have, as well as what touch pad i have. those were the only things left acting up. Ubuntu doesnt even recognize the webcam and the touchpad doesnt turn back on when i push the button. It turns itself back on when i restart or come back from suspend. I have a Gateway NV53 Laptop, any ideas?

---

### Post by Yarui on 2010-07-03
Do you have a synaptics package installed for the touchpad?  I'm not really sure about the webcam or microphone, but I would imagine there is generic software that can run those.  Maybe someone else could give you a bit more info on those things.

---

### Post by Mark Phelps on 2010-07-03
> **lazyrobot47 said:**
> ... What I want to do:
Set up my hard drive so the OS's are both on there, and still have all my documents accessible in both.

Last time I checked, the Windows driver that was SUPPOSED to allow access to Linux filesystems would NOT work with Ext4 filesystems.  Unless they've update that, you are NOT going to be able to access your Linux files from Win7.

Your best bet would be to create a shared NTFS partition and store your shared files there. Both Win7 and Ubuntu can access NTFS partitions.

---

