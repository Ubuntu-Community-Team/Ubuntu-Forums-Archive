---
title: "Advice on strange partition problem"
date: 2011-05-06
forum: General Help
---

### Post by saracb on 2011-05-06
I have a Dell laptop that I have been dual booting between Win 7 and Ubuntu 10.04 on since last fall. To make a long story short, I decided to move to Ubuntu and get rid of the Win 7 partition. I initially booted from the Live CD and used GParted to delete the Win partition and copy my Ubuntu partition to the beginning of the drive. That worked well, now I still have the original partition at the end of the disk from before and I want to delete it and let my main Ubuntu partition which is now at the front of the disk take over the space, keeping the swap of course at the end.
I ran into trouble with that this morning as it looks like my original Ubuntu partition (which is at the end of the drive) and swap partition are subpartitions of a larger partition if that makes any sense. I have
/dev/sda4 which includes /dev/sda6 (my original Ubuntu partition I want to delete) and /dev/sda5 (the linux swap which I still want).
Should I delete the whole /dev/sda4 and create a new swap manually in GParted? Or is there a better way?
Right now, I'm unable to boot as I get a Grub error when I boot off of the hard drive so I'm trying to fix things from the Live CD using gparted and potentially updating Grub when all is good.
Any advice or pointers to information about such a setup?
Thanks for the help, I have used a lot of info from this forum and hopefully someday will be able to help someone else out (maybe I am learning from all of my mistakes as of late).

---

### Post by saracb on 2011-05-06
Just to clarify, I have an extended partition which includes the original Ubuntu partition I want to delete and the swap space. Can I just delete it and create a new swap space or should I do something else? I'm trying my best to not have to start from scratch.
Thanks -

---

### Post by Lars Noodén on 2011-05-06
You can safely delete the swap partition and create a new one.  Nothing is stored there when the system is not running.

---

### Post by ajgreeny on 2011-05-06
Please click on the **Boot-info-script** link in my signature and follow the info there to copy back the RESULTS.txt file here (in code tags please, the # that shows above in the text entry dialog)

---

