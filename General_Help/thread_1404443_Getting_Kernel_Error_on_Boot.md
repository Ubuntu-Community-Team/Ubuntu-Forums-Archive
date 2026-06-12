---
title: "Getting Kernel Error on Boot"
date: 2010-02-11
forum: General Help
---

### Post by Living_The_Dream on 2010-02-11
I am dual booting Windows Vista and Ubuntu 9.10 and I'm getting the error "No Kernel Loaded" when I try to boot Ubuntu. I was just using it and the internet started acting weird so I rebooted and got that error. It won't even bring me to the menu to select the kernel. Ran Boot Info Script here are the results any info would be appreciated.

---

### Post by Living_The_Dream on 2010-02-11
Okay after some searching i found a way to get it to boot by running these commands in grub:

```
sh:grub>insmod htfs
sh:grub>set root=(hd0,2)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root+(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-17-generic
sh:grub>boot
```

I then in terminal ran apt-get for linux (sorry about not knowing the whole command, i just entered "linux" at first and put in what it told me) and then again in terminal I entered:

```
sudo update-grub2
```

I can boot now but I have to enter all those commands in grub everytime. I have all my data backed up online so if I have to reinstall it's not the end of the world but I'd rather not. Seeing as the problem seems to be with wubi it's just gonna happen again (Since this is my work comp not personal, I have to leave windows on it).

---

### Post by Richard1979 on 2010-02-11
Pretty sure a reinstall of Grub will fix this, you'll most likely need to recreate the Grub conf at least.
Search the forums - tons of info about this.

---

### Post by samantha_ on 2010-02-11
> **Living_The_Dream said:**
> I am dual booting Windows Vista and Ubuntu 9.10 and I'm getting the error "No Kernel Loaded" when I try to boot Ubuntu. I was just using it and the internet started acting weird so I rebooted and got that error. It won't even bring me to the menu to select the kernel. Ran Boot Info Script here are the results any info would be appreciated.

```

sudo apt-get --purge remove grub-pc grub-common
sudo apt-get install grub-pc grub-common

```

---

### Post by Living_The_Dream on 2010-02-16
Tried reinstalling Ubuntu. That didn't work now i can't even boot using the GRUB command line. Is there any word on when this issue with Wubi will be fixed?

---

### Post by Jackzor on 2010-02-16
What do you get at boot now?

---

### Post by Living_The_Dream on 2010-02-16
> **Jackzor said:**
> What do you get at boot now?

After running
```
sh:grub>linux /boot/vmlinuz-2.6.31-17-generic root=?dev/sda2 loop=ubuntu/disks/root.dik ro
```I get a file not found error. I've tried booting off my USB and selecting "Run Ubuntu without making any changes to my Computer" and tried reinstalling grub that way but it still won't work.

---

