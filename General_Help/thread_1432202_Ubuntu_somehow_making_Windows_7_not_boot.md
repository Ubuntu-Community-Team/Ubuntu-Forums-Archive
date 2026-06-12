---
title: "Ubuntu somehow making Windows 7 not boot"
date: 2010-03-17
forum: General Help
---

### Post by brottman on 2010-03-17
I know, from the title you probably think I'm some stupid Linux noob. I assure you, I am not.

So here is the deal, I have my wifes computer set up to dual-boot Ubuntu 9.10 and Windows 7. She uses a HP G60-445DX laptop, and something very funky is going on.

1. I first installed Windows 7, and it boots fine multiple times with no problem.
2. Next, I install Ubuntu 9.10. After installation is finished, I select reboot, and choose Windows 7. It boots fine.
3. Then, I reboot into the newly installed Ubuntu for the first time, get to the desktop, and reboot.
4. Now when I select to boot Windows 7, it gets about half-way, and suddenly reboots the computer.

I've troubleshooted this thing for days on end trying to isolate exactly what is causing Windows 7 not to boot. After reinstalling Windows 7 again, it once again boots fine, even after I use the live CD to restore Grub 2. It's only after I boot the fully installed Ubuntu 9.10 that her Windows 7 install starts acting weird. All I can narrow it down to is that after I boot into Ubuntu for the first time (after an install), Windows 7 no longer boots properly.

Help?

---

### Post by louieb on 2010-03-17
Try running the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  might give you a clue as to what is messing up. It is kind of weird that it works once - then starts messing up after you boot to Ubuntu.

---

### Post by oldfred on 2010-03-17
New grub2 is larger than grub legacy and windows boot loaders. Since there was a few bytes of hidden space in the MBR some software started to write into that space. Dell media also has its own boot to directly load media and some virus software now detects any non-windows boot loader as a virus.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by brottman on 2010-03-17
Oldfred, I think you might be on to something. The problem first appeared when I upgraded her to Ubuntu 9.10 (grub2). Do you have any ideas for a solution? You mentioned software writing into the mbr like Dell's media connect. It's possible there is something in there from HP. Should I attempt to get rid of it?

---

### Post by oldfred on 2010-03-17
The first link by meierfra. who wrote the boot_info script has several choices. The best one is to try to find what is writing into the MBR. Review what programs you have running and if they are running when the problem occurs. If you cannot find it then the link suggests alternative boot loaders.

These are not my comments but one's I have copied:
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.

---

