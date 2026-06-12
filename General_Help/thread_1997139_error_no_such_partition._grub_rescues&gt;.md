---
title: "error: no such partition. grub rescues&gt;"
date: 2012-06-04
forum: General Help
---

### Post by stasi43k on 2012-06-04
Hello guys.
I have Windows 7 and Ubuntu 11.04 on my laptop, after try to delete ubuntu with gpart. I reinstalled my computer and get this message.
error: no such partition. 
grub rescue>

I already read about 20 topics of how to improve that, but the thing is that in my case the problem is different, I cant load anything. I tried to load Windows 7, XP with disc I am chosing in BIOS boot from disc, and still this error, I tried to boot Ubuntu 12.04 with USB flash drive, and still this error, so thing look like I cant do anything with my laptop, until I will know how to work with this line GRUB RESCUE> ??
ANY HELP???
OR MAYBE SOMEBODY can tell me how to delete everything from my HD, so it will be absolutely clean, and I can reinstall everything from the begining.
Thanks.

---

### Post by oldfred on 2012-06-04
Welcome to the forums.

Some BIOS just seem to lock up, Can you totally power down, remove battery for a bit with a laptop.

Some BIOS have settings that only let you boot from HD or require both setting CD or USB first in BIOS and also using one time boot key (f12 on my system) to choose CD or USB. CD or USB has to be bootable for either to work.

Since you get grub rescue you may be able to manually boot.

at grub rescue command:

# is comment
#show you the available partitions
ls
#IF you know Windows was first (or second partition hd0,2 )
chainloader (hd0,1)+1
boot

---

### Post by stasi43k on 2012-06-04
Thank you for response.
I did took off battery, nothing had changed.
Now I am typing ls 
and that what I am getting
(hd0) (hd0,msdos) (hd0,msdos1) (hd1) (hd1,msdos4)

I am trying any combination of chainloader (hd0,1)+1 
or chainloader (hd1, 0) +1, and some more.
and response is : Unknown command 'chainloader'
I am typing : boot
and response is 'Unknown command 'boot'
.......
anything else can help me or I can put my laptop in garbage?

---

### Post by oldfred on 2012-06-04
chainloader and boot are supposed to be valid commands.

you could try 

set root=(hdX,Y) # where X is drive and Y is partition from the ls command
# or
(hd0) (hd0,msdos) (hd0,msdos1) (hd1) (hd1,msdos4)
# above had hd0,? hd0,1 and hd1,4 as valid partitions
set root=(hd0,1)
chainloader +1
boot

You also show hd1, so do you have two drives? have you tried in bIOS to boot from the drive that is hd1 or the one time boot key.

---

