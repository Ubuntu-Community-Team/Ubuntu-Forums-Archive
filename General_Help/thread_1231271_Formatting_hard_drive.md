---
title: "Formatting hard drive?"
date: 2009-08-04
forum: General Help
---

### Post by Benbow on 2009-08-04
I have just unpacked a new "Memup"multimedia system on which I will save my music, photos and films to show on my projector. The disk is pre-formatted with FAT32 which is a problem as I use Ubuntu 9.04 and almost never touch windows. 
Can anyone explain to me how to re-format it for Ubuntu so that I can transfer all my music, film and photo files from my pc to the memupor alternatively point me in the right direction to find out.
The bad news is that my technical experience is limited and I would prefer a not too complicated answer.:confused:

---

### Post by martinbaselier on 2009-08-04
The easiest way would be to use partition manager in your system/settings. Keep in mind though that the hdd won't be accesible in windows afterwards, unless someone installed a ext3 driver in windows (presuming you wil use ext3 for your filesystem)

---

### Post by Benbow on 2009-08-04
Thanks for your reply.
I also use a Humax PVR (personal Video Recorder) which uses FAT32 as well but I can't see where this would cause me any problems, or would it?

---

### Post by Paul41 on 2009-08-04
If you think that you will ever need to use Windows with it Linux (and therefore Ubuntu) will read and write to FAT32 with no problems.

---

### Post by martinbaselier on 2009-08-04
It won't cause problems to use fat32 with linux. A linux filesystems will probably work faster though. I would not change the filesystem on the PVR, since it probably is made to work with fat32 and chances are high it won't work with a linux filesystem.

---

