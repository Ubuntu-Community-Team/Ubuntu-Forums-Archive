---
title: "Have Ubuntu.. Need to format internal HD clean as NTFS (HOW?) and install Windows..."
date: 2009-12-21
forum: General Help
---

### Post by needhelpnow on 2009-12-21
Need help, please.

Due to an unfortunate set of circumstances and some problems I encountered in Ubuntu (which I intend to run with Wubi), I need help with the following...

I have a computer that had a complete clean install of Ubuntu 9.10.  There's no Windows recovery partition or anything like that. It's all Ubuntu.  But... I'm need to go back to Windows 7.  I have a bootable DVD and can run the installer.. but when I go to install, it says that my drive is not NTFS.  (I'm only 1/2 techie... so.. ) How do I format the primary drive (the only drive on the laptop) NTFS? I can also drop to an MS DOS prompt with limited commands from the Windows 7 bootable DVD.  I was thinking I'd find the drive letter and just convert driveletter:/fs:ntfs but it doesn't appear to have a drive letter.. 

I did a bunch of Google searches already but there's nothing readily available to help with this problem.  I'm kinda looking for detailed instructions because I experimented way too far this time and have a slightly-better-than-novice ability with the command line.

Thanks so much in advance.

---

### Post by zvacet on 2009-12-21
Download [Gparted live Cd]("http://gparted.sourceforge.net/") and do it with it.

---

### Post by omskates on 2009-12-21
> **zvacet said:**
> Download [Gparted live Cd]("http://gparted.sourceforge.net/") and do it with it.

Doesn't the Ubuntu live CD have Gparted (Partition Editor)? I havn't used the GParted live CD on its own.

---

### Post by omskates on 2009-12-21
> **needhelpnow said:**
> Need help, please.

Due to an unfortunate set of circumstances and some problems I encountered in Ubuntu  Just curious if you've addressed these on the forum before taking on a full reinstallation.

---

### Post by SecretCode on 2009-12-21
So you aren't trying to dual-boot or to save data on the existing Ubuntu installation? You want to wipe it clean?

Windows XP installation can do this - I'm sure Windows 7 can - in fact any OS should be able to reformat the drive regardless of what's there. 

You might be better off asking in a Windows forum how exactly you do this with the Windows 7 disc.

---

### Post by needhelpnow on 2009-12-21
Thanks all!  Gparted worked like a charm and I accomplished what I wanted to accomplish.  Thanks for the help at off hours.  

By way of background... I hope my initial posting didn't come across like an indictment of Ubuntu. I think it's great and I prefer it in many respects to Windows 7.. but I really want the best of both worlds... I was running VirtualBox with Ubuntu in Windows 7 and then decided to reverse it.  I had trouble virtualizing Windows 7 well.. trouble with sound and other issues...  Win 7 ran slow and junky even if I tweaked the settings.  In any event, I will be continuing to run Ubuntu either virtually or as a dual boot up.  

I really appreciate the help and I am a big Ubuntu fan... went through great lengths to make it work for me as a host OS but unfortunately I should have followed the ain't-broke-don't-fix-it line of advice.  My netbook runs Ubuntu Netbook Remix exclusively.

---

### Post by omskates on 2009-12-21
> **needhelpnow said:**
> .... but I really want the best of both worlds... I was running VirtualBox with Ubuntu in Windows 7 and then decided to reverse it. Excellent, I don't mind recommending dual boots like that, do all the time.> **needhelpnow said:**
>  My netbook runs Ubuntu Netbook Remix exclusively.even better:)

---

### Post by steveneddy on 2009-12-21
Don't use Wubi.

Use a virtual machine like Virtual Box.

You will be much happier in the long run.

---

