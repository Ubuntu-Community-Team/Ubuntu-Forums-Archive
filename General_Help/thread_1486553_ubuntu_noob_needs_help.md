---
title: "ubuntu noob needs help"
date: 2010-05-18
forum: General Help
---

### Post by THE-CHAD on 2010-05-18
a friend of mine installed ubuntu on my pc, version 10.04, and now he has dissappeared and i cannot reach him.

Anyway, the problem i have is neither my cdrom or DVDrw are working, by that i mean, they do not even open.

I know nothing of ubuntu and i don't even know where to begin to try and get them working...  but yes, i have tried rebooting ;)

Can anyone help me?

---

### Post by smellyman on 2010-05-18
when you reboot can you open it?  Ubuntu can't control your cd rom drive especially while it isn't loaded.  sounds like hardware failure.
 
Reboot and try popping a cd in it.
 
or use a paperclip and stick it in the little hole in the front of the drive. to eject it.  Then put a cd in and see if it still reads the cd.

---

### Post by jbrown96 on 2010-05-18
You mean that the drives don't respond to pushing the hardware eject button?
Try running ```
eject
``` in a terminal. That's not normal that you would need to do that.

---

### Post by THE-CHAD on 2010-05-18
smelly man: no, it still does not open when i reboot, as soon as i get my fat *** off the couch i will try to find a paperclip to try and manually open the drive....

Jbrown96: this is what happens when i type eject in the terminal:

mj@mj-desktop:~$ eject
eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'

---

### Post by THE-CHAD on 2010-05-18
both drives manually opened with paperclip, cd inserted and nothing, no power to drives it seems... but then again, what do i know?? i am definitely not a computer whiz...

when i go to the start menu, select places, then cdrom0, i get an error window stating "UNABLE TO MOUNT CDROM0 mount: special device /dev/scd0 does not exist"

---

### Post by jbrown96 on 2010-05-18
You need to install a couple utilities. ```
sudo apt-get install xclip hwinfo
``` Then run ```
sudo hwinfo | xclip xclip -selection clipboard
``` The use the quote tags and Ctrl+v to paste the output here.

---

