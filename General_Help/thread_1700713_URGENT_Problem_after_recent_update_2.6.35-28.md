---
title: "URGENT Problem after recent update 2.6.35-28"
date: 2011-03-05
forum: General Help
---

### Post by CrazyEyes on 2011-03-05
Hi folks,
I'm having a bit of urgent trouble, so I didn't search to thoroughly to see if this has been answered yet. I just allowed update manager to do its thing about 30 minutes ago, it was about 100MB for the update, and now when my system boots GRUB doesn't see my Windows system anymore. I get an error mounting the Windows file system, and an external drive, which suggests to me that the problem is ultimately an inability to mount NTFS. I have no idea what caused this, I have to assume it was something from the update. The error mounting code is 21. The title of this post has the generic version created by the update, and I'm almost certain I'm running Ubuntu 10.10, I installed it as 10.04 but I guess it keeps itself current. I really need to recover the Windows system, and I would love to not lose programs I've written for school in Ubuntu. Can someone give me a hand with this?](*,)

---

### Post by turtle153 on 2011-03-05
Have you run```
sudo update-grub
```

---

### Post by Trilby on 2011-03-05
You could try loading a live disk and then executing
```
update-grub
```

Also, [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) might be able to help you.

---

### Post by CrazyEyes on 2011-03-05
Yeah, I've done update-grub. I thought grub was the problem at first, but then I couldn't mount the windows file system or the external drive, which is also NTFS. So it seems like grub isn't the problem, or not exclusively anyway.

EDIT: I haven't tried with a live disk yet, I'll give it a shot just to be certain.

---

### Post by CrazyEyes on 2011-03-05
I guess I'm gonna mark this as solved. In a roundabout way it is. I tried a live disk, but it froze without completely starting up. Then I ran fedora from a live disk, which worked, and installed that on some extra space I had on my primary hard drive so I could at least get a bootloader option for windows and have a linux system running. Copied files from ubuntu to my documents folder in windows, and now I'm basically going to overwrite the fedora install with the latest 32bit 10.10 release. Tedious since I have software like Matlab and intel c++ compiler to reinstall, but it could be worse.

---

### Post by Trilby on 2011-03-06
Well I'm sorry to hear that we couldn't be of more help.
All the best in the future.

---

### Post by billbear on 2011-03-07
In short, to solve [this problem]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html"), recent update of grub introduces [this new bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225") which can corrupt the first ntfs partition.

---

