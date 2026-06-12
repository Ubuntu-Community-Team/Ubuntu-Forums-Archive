---
title: "Grub2 mount windows iso"
date: 2010-01-03
forum: General Help
---

### Post by parrimin on 2010-01-03
Is there a way to mount a windows-xp.iso image from grub2 to not to have to burn the cd?

I know burning a cd is not so much cost, but i thought mounting images from grub would be great, but i crashed on first round.
After some tries, i discovered all the examples I found are about mounting linux images, but not windows images. Is there any restriction?

My last entry in /etc/grub.d/35_Windows_ISO is as:

```

#! /bin/sh -e
cat << EOF
menuentry "Windows ISO" {
loopback loop (hd0,1)/SOSEG.iso
chainloader (loop)
}

```

and after sudo update-grub, i reboot, and there is a new line in grub menu, but it says no such file '' when entering.

Perhaps i can only do it with Linux images, but i have not found anyone saying so...

---

### Post by parrimin on 2010-01-04
Sorry, i have not explained the first attempt:
```

#! /bin/sh -e
cat << EOF
menuentry "Windows ISO" {
set root=(hd0,1)
loopback loop /SOSEG.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/SOSEG.iso
initrd (loop)/casper/initrd.lz
}

```

and it says: You have to load the kernel first

---

### Post by 9AndS on 2010-01-18
Me too would like to know is there a way to do so..

---

### Post by ggcom on 2010-01-24
hello

i'm interted too
what i'm trying (in command mode)
loopback loop (hd0,1)/myfile.iso
root (loop)
chainloader
->error: nofile specified
chainloader (loop)
->error: invalid file name `'

I'm reading this ([http://mgerards.net/blog/?cat=4](http://mgerards.net/blog/?cat=4)) but it's only for unix iso

Do you know this ?
[http://members.iinet.net/~herman54/p20/GRUB2](http://members.iinet.net/~herman54/p20/GRUB2) CLI Mode Commands.html

---

### Post by h4p0 on 2011-01-08
I'm interested too:popcorn:.

---

### Post by ggcom on 2011-01-09
hmm sorry...

---

### Post by NickJones on 2011-01-09
I saw this done on Hak5 a while ago, 
[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

---

### Post by ggcom on 2011-01-09
thanks a lot
i'm going to read it.

---

### Post by Jack Smith on 2011-11-09
I'm not an expert on the matter, but i've tried doing something similar to this.  It will be very hard if not impossible to get the windows XP ISO to loop mount with grub.  In order for ISO's to loop mount in grub2 they have to be built a certain way.

Why are you trying to loop mount the ISO?

---

### Post by parrimin on 2011-11-10
Uff. I am sorry, but I was not ever successful on this, and I gave up.

---

