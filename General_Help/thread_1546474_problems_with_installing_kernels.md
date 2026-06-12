---
title: "problems with installing kernels"
date: 2010-08-05
forum: General Help
---

### Post by slonnnik on 2010-08-05
Hi

Couple weeks ago my automatic update did not finished properly. It crashed (I'm not sure about the reason)
Since then, I'm not able to see installed new kernels in my computers.
I can see them in Synaptic package manager as installed but I do not see them when I reboot.

I would like to see them and try them

Any advice?

---

### Post by snowpine on 2010-08-05
Try opening a terminal and:

```
sudo update-grub
```

Did that work?

---

### Post by slonnnik on 2010-08-05
No 
Here is result

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done


2.6.31.20 is the one I'm using now

---

### Post by snowpine on 2010-08-05
Hmmm try installing the package 'linux-image-generic'. This is a metapackage that should restore the proper behavior of kernel updates.

---

### Post by slonnnik on 2010-08-05
> **snowpine said:**
> Hmmm try installing the package 'linux-image-generic'. This is a metapackage that should restore the proper behavior of kernel updates.

Do you mean linux-image-2.6.32-21-generic
or
just 'linux-image-generic'?

---

### Post by snowpine on 2010-08-05
> **slonnnik said:**
> Do you mean linux-image-2.6.32-21-generic
or
just 'linux-image-generic'?

linux-image-generic, as it is a "metapackage" that pulls in the latest.

Worth a try anyway... :)

---

### Post by slonnnik on 2010-08-05
it worked. Thanks

---

### Post by inameiname on 2010-08-06
Not to say this is directly related to this thread, but it's a shame there's no way of using this idea, using 'linux-image-generic', as a metapackage for other kernels, such as even newer ones in 'deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main', so it'll pull in the latest one from that repository as well. That'd be really cool.

---

