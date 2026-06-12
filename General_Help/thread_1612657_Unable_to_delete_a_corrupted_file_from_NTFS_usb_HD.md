---
title: "Unable to delete a corrupted file from NTFS usb HD"
date: 2010-11-03
forum: General Help
---

### Post by ozmian on 2010-11-03
Hi guys,
I have a problem.
I am using a USB drive to backup my movies. For some reason, I have a file that I cannot remove.
See the output:

ozmian@Surfer:/media/MOVIES 2$ rm *.img
rm: cannot remove `The last airbender.img': Input/output error
ozmian@Surfer:/media/MOVIES 2$ 

Checking it's inode number, I see the following:

ozmian@Surfer:/media/MOVIES 2$ ls -li
ls: cannot access The last airbender.img: Input/output error
total 201153324
173 -rw------- 1 ozmian ozmian 4691263488 2010-09-29 00:31 22 Bullets.iso
-snip-
133 -rw------- 1 ozmian ozmian 4442308608 2010-07-19 20:41 Afterlife.iso
176 -rw------- 1 ozmian ozmian 4593137664 2010-09-28 21:33 The Killer Inside Me 2010.iso
  ? -????????? ? ?     ?              ?                ? The last airbender.img
140 -rw------- 1 ozmian ozmian 4629659648 2010-07-02 09:30 The Losers.iso
209 -rw------- 2 ozmian ozmian 4102780928 2010-10-24 15:57 The Other Guys.iso

What gives? Any idea how I can get rid of this file?
Any tool to purge this? On windows it shows up as a 4GB file but even though I don't think it's really using the space, it is annoying. 

Who can offer some help? 
Thanks in advance!

---

