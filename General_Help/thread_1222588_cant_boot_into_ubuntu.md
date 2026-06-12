---
title: "cant boot into ubuntu"
date: 2009-07-25
forum: General Help
---

### Post by haley-hoffman on 2009-07-25
ok, im a total noob and i think this is going to take a long explanation.
i have 2 hard drives, a 80 gb and a 250 gb. i put ubuntu on my 250, which is my second drive(1,0). then i decided to put windows on my other one, just so i could play the sims(addictive game!) and once it was installed i couldnt load grub, it auto loaded windows xp. so i downloaded super grub disk, and ran it from my hard drive, and i just did some auto thing (im actually not even sure what i did) and when i rebooted i couldnt load windows from grub, but ubuntu worked, and that was all i cared about anyway. then i was reading about it and i saw that i could add a entry for windows to my menu.lst so i did, and it worked. however, after i rebooted again i tried to load my ubuntu os, and it says loading, like it always does, and then the screen goes black, but the log in screen never comes up. recovery mode doesnt work either. there is no error message, it simply doesnt load. so i installed super grub disk again, and fiddled for about an hour, but no matter what i do i cant get ubuntu to load all the way. ive definitely done whatever i did before by now, along with just about everything else you can do with that program. please, some one help me! i didnt back up my files becuase i didnt think this would happen! i dont care about the windows install, by the way. will wiping the windows drive fix this?

edit: in case you're wondering, im on the internet on my windows system, which works fine.

---

### Post by kdetech on 2009-07-25
Applications --> Accessories --> Terminal 

Then, we have to remember which is our Ubuntu installation partition. 

In our example, it is the second one (/dev/sda2), formatted as ext3, in the first HDD of a SATA controller. We suppose that it is the second one, since, in case we have Windows that demand to be in the first partition (/dev/sda1), this one is occupied. 

Now, you have to be really careful. You have to enter the right partition, instead of sda2 (unless it is the same) In the terminal : 
  cd /
  
 
  sudo -s -H
  mount -t ext3 /dev/sda2 /mnt
  mount -t proc proc /mnt/proc
  mount -t sysfs sys /mnt/sys
  mount -o bind /dev /mnt/dev
  chroot /mnt  /bin/bash

And now, you are actually "running" Ubuntu within the Hard Drive but through Live CD's terminal. 

Now we restore GRUB like that: 

1) Restoration to MBR 
  grub-install /dev/sda

2) Restoration to partition (example: /dev/sda2) 
  grub-install /dev/sda2

In the first case (that is the most usual) you have certainly installed GRUB on MBR after you receive, in the terminal, the message that there are no errors. 

After you reboot, you have your favorite bootloader restored. 

Alternatively, mount the / and /boot folders you want to boot into and just pass the --root-directory argument into grub-install, there is no need to chroot anymore.

---

### Post by kdetech on 2009-07-25
If you have Ubuntu alternate cd its even easier. Just select rescue a broken system on start

---

