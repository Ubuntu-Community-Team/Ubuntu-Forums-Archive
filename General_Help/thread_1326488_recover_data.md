---
title: "recover data"
date: 2009-11-14
forum: General Help
---

### Post by xw92 on 2009-11-14
Recently, my dad's computer (running Ubuntu) ran into "Kernel panic - not syncing: Attempted to kill init" problem while trying to boot. 
Currently, I am trying to recover his files using a live cd and then reinstall the system. However, when I try to copy files from his home folder to a USB, I am getting permission errors. I tried gksudo nautilus but that did not work.

First, is there a better way of solving the kernel panic problem?

Also how can I gain permission into his HD files through a live CD?

thanks for all the help

---

### Post by kiridude on 2009-11-14
Did you try sudo mv or cp from the command line?

---

### Post by jbrown96 on 2009-11-14
Does the kernel panic happen every boot? You might want to try a different kernel. When the grub menu shows up (you may have to press Esc or shift), try choosing an older kernel (not recovery!). You can also try to do some trouble shooting on the kernel that is causing the problems. At the grub menu, press e on the first listed kernel. Then scroll to the really long line (I think it's the third) and press e again. Scroll to the end of the line and find splash. Change it to nosplash then press Esc and b to boot. Now you should get all the booting messages. Try to write down the messages and post them here. 

On the liveCd, you should be able to copy everything over with ```
sudo cp -R /media/ubuntu/home/ /media/disk/
``` You will need to change ubuntu and disk to wherever you mounted them. Just open /media in nautilus and you should be able to tell.

---

### Post by xw92 on 2009-11-14
Hey thanks for the response.
@jbrown96: I am still not sure how to figure out what to change "ubuntu" and "disk" to. Right now, the files I want to recover are located at:
(harddrive name now a random bunch of numbers and letter)/home/user/Documents

---

