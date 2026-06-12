---
title: "grub rescue&gt; message"
date: 2009-12-15
forum: General Help
---

### Post by jfroneb0 on 2009-12-15
Help! New to Linux and am trying to get display while installing Ubuntu. Deleted the previous installation and now cant boot machine. Get grub rescue> message

---

### Post by houseworkshy on 2009-12-15
Well as you have deleted the previous system that should mean you have no work on your machine.  So I'd be inclined to do a fresh instal.  To get rid of remenants boot from the live cd.  In the system tab find the partition manager then use it to delete the drive.  Set the drive to msdos.  Format it with exe2.  After that manage flags and set to bootable.  Then proceed to install.  That said also wait for someone who knows better than me to confirm this as I am by no means an expert

---

### Post by houseworkshy on 2009-12-15
I've just realised that the advice above applies to a whole installation and somehow you have managed to post.  If you do have work on your drive get it off first.  You could write it to a flash stick whilst running from the the live cd.  Failing that download Puppy linux which can be loaded to ram from its' cd and then burn your work to a cd or dvd.  Also if you are duel booting make sure windows is the first system on the machine. If it's a "how to" on repairing your grub I'm afraid that I'm not clued up enough to give that advice.  Good luck.

---

### Post by jfroneb0 on 2009-12-17
got the boot issue fixed. I am trying now to install inside windows. My issue has been no graphics after the install screen. I get a greenish blob in the center of the screen and then it goes blank. The OS is installing in the background as I can hear the sounds. Tha problem is i can't see to finish the install. It is a Compaq CQ60 64 bit laptop. Any help is appreciated.

---

### Post by jfroneb0 on 2010-01-03
Ok, I have managed to fix the boot problem as mentioned and all is working well on my machine, BUT I still see the option to go to the Ubuntu OS at start up. I am trying to rid laptop of Ubuntu and research some more to get a fresh install when I can figure out the display issue. How do I get rid of all Ubuntu files so I can start from scratch. Windows is working fine on both partitions, 7 Home and 7 Pro. Thanks

---

### Post by houseworkshy on 2010-01-05
Well as you have got rid of Ubuntu the way to remove the mention of it from the boot menu would be to boot from your windows installation disc and run "fixmbr".  The areas of disc covered by Ubuntu will not be readable by windows so you will likely get something like "in order to use this disk it needs to be formated" on trying to look at it.  Just treat those areas as unused disc space to be reformated or extended into it as required, the linux data and formating will simply be over written.  Also wait for another responce as the last windows I used much was xp, I know very little of vista and nothing of 7 so things may have changed.

---

