---
title: "grub2 doesn't recognize windows 7"
date: 2011-08-12
forum: General Help
---

### Post by karq on 2011-08-12
hey everyone!

here's my probem I installed windows 7 after I installed linux. I got grub reinstalled but windows doesnt show up in the grup menu. So I run in linux sudo update-grub, but this doesnt find my windows system.

Maybe someone can help me to add windows into grub menu.

Here's my fdisk -l 
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8511    68358144   83  Linux
/dev/sda2            8511        8572      487425    5  Extended
/dev/sda3   *        8572       12513    31662080    7  HPFS/NTFS
/dev/sda4           12514       19457    55777680    7  HPFS/NTFS
/dev/sda5            8511        8572      487424   82  Linux swap / Solaris

```

And here's my sudo update-grub
```
kaarel@mint ~ $ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-5-686
Updating /boot/grub/menu.lst ... done

```

---

### Post by coffeecat on 2011-08-12
Wee need to see more information that can be provided by meierfra's boot script. Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script according to the instructions there and post the contents of your RESULTS.txt between code tags for clarity. There are several reasons why grub's os-prober might not see Windows and hopefully the boot script may tell us. Also, it will give a better fdisk output than you get with fdisk -l, which gives you partition figures in cylinders, which is of little use. In future, you might want to use "fdisk -lu" which gives figures in sectors which is of more help. You don't need to run fdisk again now - the equivalent information will be in the boot script output.

---

### Post by raja.genupula on 2011-08-12
sudo os-prober

this command going to give where you have installed your windows 
then edit your grub.cfg file in /boot/grub location .

---

### Post by raja.genupula on 2011-08-12
[https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2)

---

### Post by raja.genupula on 2011-08-12
other wise write a program for your windows by editing your grub.cfg file man 


here is the code 


 Chain-loading an OS

Operating systems that do not support Multiboot and do not have specific support in GRUB (specific support is available for Linux, FreeBSD, NetBSD and OpenBSD) must be chain-loaded, which involves loading another boot loader and jumping to it in real mode.

The chainloader command (see chainloader) is used to set this up. It is normally also necessary to load some GRUB modules and set the appropriate root device. Putting this together, we get something like this, for a **Windows** system on the first partition of the** first hard disk**:

```
menuentry "Windows" {
	insmod chain
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
```

---

### Post by Ozymandias_117 on 2011-08-12
> **raja.genupula said:**
> other wise write a program for your windows by editing your grub.cfg file man 


here is the code 


 Chain-loading an OS

Operating systems that do not support Multiboot and do not have specific support in GRUB (specific support is available for Linux, FreeBSD, NetBSD and OpenBSD) must be chain-loaded, which involves loading another boot loader and jumping to it in real mode.

The chainloader command (see chainloader) is used to set this up. It is normally also necessary to load some GRUB modules and set the appropriate root device. Putting this together, we get something like this, for a **Windows** system on the first partition of the** first hard disk**:

```
menuentry "Windows" {
	insmod chain
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
```

You should put that in /etc/grub.d/40_custom so you don't lose it every time Ubuntu has a Kernel upgrade.

---

### Post by selenir on 2011-08-12
Chances are, os-prober is installed. If not, you should install that. If it is installed, chances are, in your windows boot partition, /dev/sda3 has two boot directories; boot/ and Boot/. You should delete boot/ and rename Boot/ to boot/. Run sudo update-grub2 and it should show up. The rest of the solutions will likely not help you.

EDIT: I don't remember where I got the information from; it came from somewhere on the Ubuntu forums. If anyone can link to it, it would be much appreciated. The boot directory conflict comes from the fact that ntfs partitions treat uppercase and lowercase as the same, according to the previously mentioned post.

---

### Post by raja.genupula on 2011-08-12
> **Ozymandias_117 said:**
> You should put that in /etc/grub.d/40_custom so you don't lose it every time Ubuntu has a Kernel upgrade.

thanks man i will append it from next time  for the threads like this

---

### Post by selenir on 2011-08-12
That's not exactly the best way to go about it. The method [raja.genupula]("http://ubuntuforums.org/member.php?u=1184528")  suggests is only a workaround; not the most appropriate solution.  Suppose you change your partitions around. Grub will crash if you don't  modify the code when you restart.

---

