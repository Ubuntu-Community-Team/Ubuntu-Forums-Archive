---
title: "File-roller crashes PC on drag-drop"
date: 2011-10-31
forum: General Help
---

### Post by bazcor on 2011-10-31
Just installed Lubuntu on my machine and love it.Only real problem I've encountered is that file roller drag-drop causes the PC to crash. Only way out is a reboot!

File-roller does give an error message, 'could not extract file' or something, then leaves the cursor as a +.

File extraction through the file-roller menu works fine.

Anybody else getting this?

Barry

---

### Post by infinitybot on 2011-10-31
You could try to reinstall fileroller
```
sudo apt-get purge file-roller
```
```
sudo apt-get install file-roller
```

---

### Post by bazcor on 2011-10-31
Thanks for that but I just tried it and there was no change in the file-roller bug.

Should just give a description of my system:
OS Lubuntu 11.10 64 bit
PC amd hex core with 16GB of ram
Graphics nvidia gts250 with proprietary driver.

Barry

---

### Post by kjoe on 2012-02-17
For me the only workaround to fix this bug was to install nautilus. I then was able to drag files from an archive (opened with file-roller) to a nautilus window. But it still crashes, if you drag to the Lubuntu desktop.

So the reason for the bug seams to be related to nautilus dependencies. Maybe this information is helpful and someone who is more into linux than me can fix the bug.

kjoe

---

### Post by kjoe on 2012-02-17
additional information:

This annoying file-roller bug is still present in latest daily build of Lubuntu 12.04 Precise Pangolin (Feb 17th 2012) when testing it as live CD in virtualbox.

I would like to report this to the developing team of Lubuntu, but I do not know, where to post.

kjoe

Edited: Ok, I've just confirmed the bug at launchpad.net

---

### Post by stefan_g on 2012-08-10
Hi there.

The bug has been reported on Launchpad to be closed ([https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/878993?comments=all](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/878993?comments=all)). 

Fixed packets are still only in proposed repository, but should be available in 'productive' repository, soon.

Need threads in this forum be closed? I would do it, but don't know how ...

---

### Post by RyanHall on 2013-02-25
No they should not be closed, as it is 2/24/13 and I installed Lubuntu 12.04 X64 and ran into this issue. This issue still has not been fixed and is quite a nuisance.

---

