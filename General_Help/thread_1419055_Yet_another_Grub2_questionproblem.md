---
title: "Yet another Grub2 question/problem"
date: 2010-03-01
forum: General Help
---

### Post by 1Privateer on 2010-03-01
Hello all, I've read the various Grub2 posts and even the guide, but unfortunately for me I can't seem to come up with an answer to my problem. I installed Ubuntu 9.10 on a new hard drive on a friends laptop, but I have problems with the system hanging on the Grub2 bootup.

I'll post the screen 

recordfail=1
if [ -n ${have_grubenv} ]; then save-env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
search --no floppy --fs-uuid --set ac1b1d46-bac1-4140--953e-70a8a61be\8b0
linux /boot/vmlinuz-2.6.31-14-generic root=UUI=ac1b1d46-bac1-4140-9\53e-70a8a61be8b0 ro   quiet splash
initrd /boot/initrd.img-2.6.31-14-generic


If I hold down the left shift and then press E to edit and remove the [COLOR="Red"]search --no floppy[/COLOR] line entirely then press ctrl-x the system boots just fine. I then opened up a terminal and did sudo update-grub to try that but it didn't fix it. 
Is this a problem in my bios looking for a floppy, I tried with the boot from floppy enabled and disabled (but always as the 3rd boot option) the floppy is not installed. Is there anyway to edit the file and save it so it will boot up? I was trying to research that and could not come up with it. If I can edit and save, I may need step by step if possible. 
Sorry for the long post. Thanks for any help

---

### Post by 3177 on 2010-03-01
In a terminal, type gksu nautilus and navigate to the following
"/boot/grub/grub.cfg" 
open and remove all the lines that say search no floppy as before
IMPORTANT: you cannot just save this edited file, you must save as 
I save as grub2.cfg, then rename the messed up one grub3.cfg
then of course simply rename grub2.cfg grub.cfg
exit nautilus and terminal 
reboot
enjoy
(a lot of people have had this problem)

---

### Post by 1Privateer on 2010-03-01
Removed that entire line, saved as suggested, renamed, checked to ensure after rename to grub.cfg it was the modified file. Rebooted and still hung up looking for the floppy. Any ideas what I may have done wrong? I did remove the entire line.

---

### Post by 3177 on 2010-03-01
post your grub.cfg

---

### Post by lidex on 2010-03-01
You can't edit grub.cfg directly and I wouldn't trust the method described. But before you try anything else download the boot info script from the link in my signature and follow the instructions there. Post back the results here. (You'll need to boot into LiveCD.)

---

### Post by 3177 on 2010-03-01
trust?......
As a matter of fact, I was given this explanation in a previous thread and am spreading it because it works. If you edit your cfg and remove all instances of --search no floppy---- line(up till after set uuid) grub cannot give the error as there is no command telling it to search for floppy.
there is 2 instances when you install 9.10 and 3 when you update the kernel.
Im sorry if I seem aggressive but I took offence to that remark about trust
on a final note there is no reason to be worried about editing files if you know what you are doing.

---

### Post by oldfred on 2010-03-01
It is not trust per se, but it is not correct to edit a file that says do not edit. Also every kernel update and maybe other updates will overwrite the grub.cfg as update-grub is run.

Better way to fix problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by 3177 on 2010-03-01
check out step 4 of the last link
its saying put a # in front of the line, which means dont use me
I said remove it 
For the record I have to use this method everytime i install ubuntu 9.1

---

### Post by lidex on 2010-03-01
> **3177 said:**
> trust?......
As a matter of fact, I was given this explanation in a previous thread and am spreading it because it works. If you edit your cfg and remove all instances of --search no floppy---- line(up till after set uuid) grub cannot give the error as there is no command telling it to search for floppy.
there is 2 instances when you install 9.10 and 3 when you update the kernel.
Im sorry if I seem aggressive but I took offence to that remark about trust
on a final note there is no reason to be worried about editing files if you know what you are doing.

Perhaps I could have worded that better - no offense was intended and I fully believe your intentions only to help. Please accept my apologies. 

oldfred's post explains it much better than mine.

---

