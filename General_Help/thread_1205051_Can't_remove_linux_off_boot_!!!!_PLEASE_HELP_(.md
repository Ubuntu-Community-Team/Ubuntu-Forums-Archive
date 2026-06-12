---
title: "Can't remove linux off boot !!!! PLEASE HELP :("
date: 2009-07-05
forum: General Help
---

### Post by L.J on 2009-07-05
Hello everyone, i need help in deleteing linux off the boot screen selector, which i think is called grub or something. I just cannot get it off as i have got a new computer and want to use the hard drive linux is on for it to become a download server if this makes sense. Can anybody help me as this is urgent and all the ways i have tryed have failed :( !

cheers all...

---

### Post by taurus on 2009-07-05
Are you trying to install a server on that harddrive?  If you are, the installer will install it own bootloader, wiping out the previous version so you do not need to remove it first before you install the server version.  Just make sure you've selected to boot from the CD/DVD first in the BIOS.

---

### Post by lotharmat on 2009-07-05
Hi,

Have you edited /boot/grub/menu.lst?

---

### Post by L.J on 2009-07-05
Im just trying to delete it first, then i will think about the server.

no, not that im aware of lotharmat

---

### Post by mhgsys on 2009-07-05
A quick google search; found lots of info ; have a look here.

[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

---

### Post by taurus on 2009-07-05
> **L.J said:**
> Im just trying to delete it first, then i will think about the server.

no, not that im aware of lotharmat

Are you trying to delete an entry for Ubuntu or are you trying to remove GRUB from MBR?

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by L.J on 2009-07-05
im trying to remove grub... i think

im new to this sorry

cheers

---

### Post by mhgsys on 2009-07-05
Have you clicked my link:>
?

---

### Post by L.J on 2009-07-05
yes just tryed doing it through linux and it hasnt worked, all the other ways it states i have tryed earlier and they have not worked either :/ any more suggestions ?

---

### Post by taurus on 2009-07-05
What exactly are you trying to do?  Are you trying to install another OS on that harddrive since removing GRUB from MBR will prevent you from booting Ubuntu on that harddrive?

---

### Post by L.J on 2009-07-05
no i just want to remove ubuntu off of grub so that my computer boots straight onto windows and then i can delete the whole of the hard drive from windows....

---

### Post by L.J on 2009-07-05
all the possible ways of doing this don't seem to be working, maybe im doing something wrong ?? I've tryed using a windows xp cd with fixmbr but it just doesnt work, this may be because it doesnt even ask me for what windows i am using or a password which some tutorials say it should do :S, any help ?

---

### Post by ajgreeny on 2009-07-05
> **L.J said:**
> no i just want to remove ubuntu off of grub so that my computer boots straight onto windows and then i can delete the whole of the hard drive from windows....
So you want the windows MBR back again.  You can do that either with the windows install CD, recovery module, or even the supergrub live CD.  If you did the default when you installed ubuntuit will have grub on the windows drive in place of the windows MBR, so you need not do anything to the ubuntu drive until you reinstall another OS, or need to re-use it for windows file or data storage.

Just a thought, are you booting the correct drive?  Have a look in your bios and see if the windows drive is the first boot device;  perhaps fixmbr did its work OK, but you don't get the windows MBR as the ubuntu drive is still first boot device instead of windows.

---

### Post by L.J on 2009-07-05
urm im not sure if i understand, i've tryed just deleting linux off windows but when i boot my computer up it gives me an error because it can't find linux, i need to install it again to be able to use my computer. I dont want to have to select a OS at all i just want it to boot automatically into windows and not show linux at all :(

---

### Post by taurus on 2009-07-05
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

---

### Post by L.J on 2009-07-05
ok i need a bit of help i have used the link and i am now stuck... i've got to the point where it is going to reinstall MBR but i need to select the operating system i had on befor installing grub which is windows, it does not give me this option only syslinux :S:S help :S

---

### Post by L.J on 2009-07-05
Woohoooooo i done it !!! thanks for all the help everyone, greatly appreicated !

thanks :guitar:

---

### Post by ajgreeny on 2009-07-05
Did you originally install using wubi, rather than partitioning and installing a dual boot?   The two are quite different and require a different approach to removing ubuntu.

Either way can you please boot the live ubuntu CD and then in terminal run ```
sudo fdisk -l
``` and copy the output here.  That will tell us if you do still have windows installed, as it sounds as if it might have disappeared, if your windows install CD can't find it.

---

### Post by L.J on 2009-07-05
sorry i've already done it, read my last comment :lolflag:, 
thanks anyway

---

### Post by Chronon on 2009-07-05
Any clarification about your situation and what eventually worked would be helpful for future readers.

---

### Post by L.J on 2009-07-06
well i eventually fixed it via the super grub disk, once i had it loaded up on the other computer i google for a tutorial and that explained all the options and possible ways of fixing it, after abit of exploring i found the right setting on the disk which i think is (fix windows boot>syslinux) this was explained to do the same thing as fixmbr in the windows recovery console but it worked unliked fixmbr. If anyone wants any more details then im happy to help...

---

