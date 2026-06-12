---
title: "Kubuntu is really slow on my friends computer"
date: 2010-02-24
forum: General Help
---

### Post by mattmill30 on 2010-02-24
Hi,

My friends computer is extremely slow with all versions of kubuntu. Its very slow to boot, very slow to load applicatons, very slow to switch between windows, very slow to do anything.

I can't think of what would be causing the slowness, its not new, doesn't have any fancy hardware AFAIK, but it runs XP perfectly well, its probably a 2.0+ghz pentium 4 processor.

Do you think it could be a kernel chipset issue?

Or perhaps a graphics driver/window manager issue?

Any help would be greatly appreciated.

I don't know what the hardware is, is there a command i can run to list all the hardware?

Thanks,

Matthew Millar

---

### Post by anonymous_user on 2010-02-24
Do other KDE distros work fine? If not, maybe KDE is just too heavy. 

Try Xubuntu or other Xfce distro.

---

### Post by hansdown on 2010-02-24
Hi mattmill30.

For hardware info, open a konsole, and type 

```
lshw
```

---

### Post by drdanielfc on 2010-02-24
what are the computer specs? what graphics card, etc

---

### Post by stephenmac7 on 2010-02-24
The computer may be slow just on your friend's computer is it on your computer? Try and see if your friend's computer meets the system requirements. If it does not with kubuntu try ubuntu or xubuntu and if it still goes slow go with lubuntu or Fedora 12.

[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by mattmill30 on 2010-02-25
Hi,

I've generated a txt file with the lshw feedback.

I've noticed that the pc seems to get slower and slower through use.

Which makes me think it might be a memory issue, hence the kernel presumption.

Just to note, this computer uses wubi, but I don't think that'd cause a problem.

I have noticed that the kernel that's being used is pae, which when I checked in aptitude says its for large capacity memory support on 32-bit systems.

I've just checked the lshw.txt file and apparently this computer has 4224Mib. So thats probably the right kernel?

I've just noticed that the pc has 1x 128mb stick of RAM and 1x 4 gig, lol. It doesn't mention the fsb speed, but that could explain the speed issue. Especially as the computer is actually a 3.00Ghz pentium 4.

Also noteworthy, when wubi was being installed, it flashed up lots of I/O errors, which I thought were disk errors, although after I ignored the errors, it seemed to install fine.

Do you think the errors could explain the issue?

Is there anyway of accessing the wubi installation logs, to try and extract the error?

Thanks for all your help.

Matthew Millar

---

### Post by hansdown on 2010-02-25
I/O errors might point to the problem.

Could you post the output of

```
sudo fdisk -l
```

That will give us a good look at the partitions.

Oh, I just caught the wubi install part.

I don't have any experience there.

---

### Post by mattmill30 on 2010-02-26
Hi,

Ok.

A little more serious an issue.

Kubuntu will no longer boot :S

Because its wubi I have to select Kubuntu from the OS list (boot.ini).
When I do, I see "Try (hd0,0 ) : NTFS5", and then the screen goes blank, and the pc restarts.

Normally I see a few lines flash up, before grub, but only the NTFS5 one is appearing now.

Because I was having the problems, I upgraded to 10.04 (before I posted this thread). So yesterday, I ran a full-upgrade in Kubuntu and about 80 updates were available. I installed them all, and after turning it back on today, I get the above error.

Any help would be appreciated.

Thanks,

Matthew Millar

---

### Post by sandyd on 2010-02-26
> **mattmill30 said:**
> Hi,

Ok.

A little more serious an issue.

Kubuntu will no longer boot :S

Because its wubi I have to select Kubuntu from the OS list (boot.ini).
When I do, I see "Try (hd0,0 ) : NTFS5", and then the screen goes blank, and the pc restarts.

Normally I see a few lines flash up, before grub, but only the NTFS5 one is appearing now.

Because I was having the problems, I upgraded to 10.04 (before I posted this thread). So yesterday, I ran a full-upgrade in Kubuntu and about 80 updates were available. I installed them all, and after turning it back on today, I get the above error.

Any help would be appreciated.

Thanks,

Matthew Millar
its one of the reasons why we tell people not to use wubi....
+ your using 10.04, which is currently beta. someone upstream may have made a bad commit, and as a result, it went into the updates that you downloaded, and into your computer.

wubi + 10.04= not good.

---

### Post by hansdown on 2010-02-27
Um...

Thanks carlee?

---

### Post by mattmill30 on 2010-02-27
Hi,

I don't think using wubi+10.04 should be a problem.

Although i don't fully understand. My understanding of wubi is that its simply a boot-loader, that points to wubildr.mbr, which in turn points to the ubuntu.disk image as the boot partition.

I think its likely an NTFS corruption, as thats the only message that's displayed before it reboots. I was working through the FAQ on wubi's website, I've run chkdsk /r but that hasn't fixed it.

Where do you think the fault lies? Is it a wubi bug, possibly something to do with the I/O errors?

If it were the I/O errors, wouldn't the problem have manifest itself in the beginning, rather than after several uses?

Is it possible that the wubildr.mbr, or one of the following stages has corrupted? In which case, is it possible to re-configure wubi, to re-generate the stages?

Thanks for all your help,

Matthew Millar

---

### Post by hansdown on 2010-02-27
Having never tried a wubi install, I can't offer much advice.

There are a number of bug reports.

[http://www.google.ca/search?q=i%2Fo+errors+with+wubi+install+of+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=i%2Fo+errors+with+wubi+install+of+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

