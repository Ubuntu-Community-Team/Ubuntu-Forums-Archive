---
title: "Make Windows 1st Choice (not just default) in Grub?"
date: 2011-03-04
forum: General Help
---

### Post by josephpford on 2011-03-04
I am dual booting Windows and Ubuntu 10.10.  I installed StartUp-Manager so that I could easily make Windows my default OS upon Startup.  However, I did a sudo apt-get update / sudo apt-get upgrade and now I have a new kernel.  This moved Windows down in the list, so now MemTest86 is the default OS upon Startup.

I want to make Windows the default always always always, not just until the next Kernel upgrade comes through. 

Any ideas on how I can accomplish this without installing lilo or another boot loader (I'm scared of losing my Windows partition because it takes forever to install Windows and get it working again).

Thank you.

---

### Post by idoitprone on 2011-03-04
I dont really use startup manager. I prefer the manual method of changing the grub order

Please becareful, messing around with grub.d/ files will mess up the  grub boot menu. If you wish back up the files in the same folder and  remove all permissions, since it will appear as double when you update  the grub menu

Method 1 
Changing the boot order
go to /etc/grub.d/

there should be a list few files 10_linux and 30_os_prober or whatever.


Becareful, make sure you dont mess up
rename os_prober number bigger than 00_header, but smaller than 10_linux but  ex. 03_os_prober

then sudo update-grub

windows and other os should always be first, while linux thereafter.

Method 2
adding custom entries
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries")
 You can copy the windows section of /boot/grub/grub.cfg 

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 8e0446680446537f
        chainloader +1
}
```add it to the bottom of /etc/grub.d/40_custom

of course, rename it to a number between header and linux. while adding proper read and excute permission.

sudo update-grub

---

### Post by Mark Phelps on 2011-03-05
> **josephpford said:**
> Any ideas on how I can accomplish this without installing lilo or another boot loader 

While idoitprone's suggestion is a good way to do it, it's also considerable work (but worth it, considering the result).

An alternative is to simply install startup manager.  Then, boot into Ubuntu, launch that, and select the Windows entry as the default.

This only takes 5 minutes or so, and you only need to do it when kernel versions change.

---

### Post by grahammechanical on 2011-03-05
I use Grub Customizer. It is in the Ubuntu Software Centre. You can select a line in the menu list and under the Edit menu you can move that line up or down the list. So, that the boot entry that you want is on the top of the list.

The utility also makes it easy to to do other things, such as put an image behind the grub menu. Once installed it sits in the Applications menu under System tools.

Regards.

---

