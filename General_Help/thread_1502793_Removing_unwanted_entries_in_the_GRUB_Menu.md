---
title: "Removing unwanted entries in the GRUB Menu"
date: 2010-06-06
forum: General Help
---

### Post by karthick87 on 2010-06-06
I am using ubuntu 10.04 and I would like to keep only the main menu,and i have to disable all the other options including recovery and memtest in the GRUB menu..How to do this..?

---

### Post by Elfy on 2010-06-06
To disable memtest you can remove the executable bit from the script

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

If you had other os's showing I'd assume the same would apply for 30_os-prober.



To stop recovery options 

```
sudo nano -B /etc/default/grub
```

Remove comment from #GRUB_DISABLE_LINUX_RECOVERY="true" to 

GRUB_DISABLE_LINUX_RECOVERY="true"

Run 

```
sudo update-grub
``` after changes have been made.

(Thanks to drs305's innumerable grub2 threads/wiki.)

---

### Post by MedianMajik on 2010-06-06
/boot/grub/grub.cfg is where your grub configuration file is located.  Open it in an editor to view/change whatever you want.

Be sure to read up on Grub2 [here.]("https://help.ubuntu.com/community/Grub2")

---

### Post by karthick87 on 2010-06-06
> **forestpiskie said:**
> To disable memtest you can remove the executable bit from the script

```
sudo chmod -x /etc/grub.d/20_memtest86+
```If you had other os's showing I'd assume the same would apply for 30_os-prober.



To stop recovery options 

```
sudo nano -B /etc/default/grub
```Remove comment from #GRUB_DISABLE_LINUX_RECOVERY="true" to 

GRUB_DISABLE_LINUX_RECOVERY="true"

Run 

```
sudo update-grub
``` after changes have been made.

(Thanks to drs305's innumerable grub2 threads/wiki.)


Is it possible to remove the memtest entry,if so how..?

---

### Post by Elfy on 2010-06-06
> /boot/grub/grub.cfg is where your grub configuration file is located. Open it in an editor to view/change whatever you want.That file is read only for a reason as far as I can tell - as soon as there's a change that requires an update of grub your changes will be gone. Of course I am happy to be proved wrong as I much preferred fiddling about with menu.lst :)

---

### Post by Elfy on 2010-06-06
> Is it possible to remove the memtest entry,if so how..?

sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

It's there in the first post.

Edit - 
```
sudo chmod -x /etc/grub.d/20_memtest86+
[sudo] password for kevin: 
kevin@kevin-desktop:/etc/grub.d$sudo update-grub
Generating grub.cfg ...
Found background image: SmoothMoment.png
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found PCLinuxOS on /dev/sdb1
done

kevin@kevin-desktop:/etc/grub.d$sudo chmod +x /etc/grub.d/20_memtest86+
kevin@kevin-desktop:/etc/grub.d$sudo update-grub
Generating grub.cfg ...
Found background image: SmoothMoment.png
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
**Found memtest86+ image: /boot/memtest86+.bin**
Found PCLinuxOS on /dev/sdb1
done

```

---

### Post by karthick87 on 2010-06-06
Thanks a lot..!And pls tell me how to hide the GRUB Menu..?

---

### Post by Elfy on 2010-06-06
```
sudo nano -B /etc/default/grub
```

find GRUB_HIDDEN_TIMEOUT=0 - remove the #

```
sudo update-grub
```

---

### Post by karthick87 on 2010-06-06
Once again thank you :)

---

### Post by Elfy on 2010-06-06
Welcome :)

Have a look at 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by saharavenon on 2011-07-17
tried Grub Customizerby Daniel Richter. awesome!

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)
[http://www.omgubuntu.co.uk/2011/05/grub-customizer/](http://www.omgubuntu.co.uk/2011/05/grub-customizer/)

or maybe you try Super Boot Manager.

[http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/](http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/)

---

