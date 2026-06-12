---
title: "Wubi GRUB overwritten by Win7. Really need help!!!"
date: 2012-09-24
forum: General Help
---

### Post by PoxSpax on 2012-09-24
Hello and thanks for reading,

I really need help **now**, as I have a project for work stuck on an inaccessible Wubi Ubuntu install.

I currently have (had) Wubi installed alongside Windows 7 on my laptop.

I was finished using Ubuntu so I restarted back into Windows and went to do something while it restarted. I came back and Windows was doing a start up disk check!

Previously when I started my laptop, I received a screen asking if I wanted to boot into Windows or Ubuntu. I still get this screen, but now if I choose Ubuntu I am simply given a GRUB prompt, and it no longer boots into Ubuntu.

I have never messed much with GRUB, and so I am completely lost now. And I am stressing out. I have backed up my root.disk, swap.disk, and wubildr from the C:\ubuntu\disks directory and I don't know where to go from here. 

I tried launching Ubuntu off my live disk and mounting these disks, but I had no success. I received superblock errors.

Please please please please help!

Thank you very much for your time.

EDIT: I apologize if there is a sub-forum for Wubi, I looked but couldn't find one.

---

### Post by albandy on 2012-09-24
This can help:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

---

### Post by PoxSpax on 2012-09-24
> **albandy said:**
> This can help:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

Thanks for the response albandy, but already tried that. That's where I received the superblock error. =[

---

### Post by Mark Phelps on 2012-09-24
Wubi doesn't actually install along side Win7; instead, it installs INSIDE the Win7 partition.  And, as such, it doesn't really use GRUB; instead, it uses a derivative known as GRUB4DOS -- a version that runs on a Windows partition.

I'm telling you this because if folks tell you to reinstall GRUB, not only will that not work, it may break access to Win7 in the process.

What I have read might work, is the following:
1) save off the root.disk file
2) boot into Win7 and remove Ubuntu
3) reinstall Ubuntu using Wubi
4) copy the saved root.disk file over the new root.disk file
5) reboot

Should then be able to access Ubuntu again.

---

### Post by PoxSpax on 2012-09-24
> **Mark Phelps said:**
> Wubi doesn't actually install along side Win7; instead, it installs INSIDE the Win7 partition.  And, as such, it doesn't really use GRUB; instead, it uses a derivative known as GRUB4DOS -- a version that runs on a Windows partition.

I'm telling you this because if folks tell you to reinstall GRUB, not only will that not work, it may break access to Win7 in the process.

What I have read might work, is the following:
1) save off the root.disk file
2) boot into Win7 and remove Ubuntu
3) reinstall Ubuntu using Wubi
4) copy the saved root.disk file over the new root.disk file
5) reboot

Should then be able to access Ubuntu again.

Thanks Mark,

But my root.disk file shows as having 0KB? Where as the swap.disk is ~240MB. Is the data stored in root.disk or swap.disk?

I may still try that idea, and just use a separate computer so I don't have to remove anything that is existing.

---

### Post by oldfred on 2012-09-24
Did Windows run chkdsk and move the root.disk to the chkdsk folder in the root of Windows?

Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by PoxSpax on 2012-09-24
> **oldfred said:**
> Did Windows run chkdsk and move the root.disk to the chkdsk folder in the root of Windows?

Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

Thanks Fred. I wish it was that easy. But the root.disk is still in-place. Just it appears the Grub4DOS files have been removed.

---

### Post by oldfred on 2012-09-24
If the only root.disk you have is 0KB, then it is a bigger issue.

I do not know wubi, some say they have used it for extended time periods, but that is not what it was meant for.

From the Developer of wubi.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Wubi is relying on the Windows boot loader and the NTFS filesystem. So if Windows has issues then wubi will not work. True dual boot with separate partitions may allow one system to boot when the other does not.

---

### Post by PoxSpax on 2012-09-24
> **oldfred said:**
> If the only root.disk you have is 0KB, then it is a bigger issue.

I do not know wubi, some say they have used it for extended time periods, but that is not what it was meant for.

From the Developer of wubi.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Wubi is relying on the Windows boot loader and the NTFS filesystem. So if Windows has issues then wubi will not work. True dual boot with separate partitions may allow one system to boot when the other does not.

Are you saying that it could be... gone?

---

### Post by oldfred on 2012-09-24
The root.disk cannot be 0 if it has and data. Did it get backed up somewhere to a hidden location. It does not normally just change to 0 bytes.

---

