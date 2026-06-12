---
title: "How do i upgrade a kernel"
date: 2012-04-18
forum: General Help
---

### Post by jpg123 on 2012-04-18
Can anyone tell me how to upgrade a kernel? Thanks.

---

### Post by for.i.am.root on 2012-04-18
If you have never compiled code you should stay away from manual kernel upgrades. Just use the Update Manager under System --> Administration.

---

### Post by wojox on 2012-04-18
> **jpg123 said:**
> Can anyone tell me how to upgrade a kernel? Thanks.

There are ppa's you could install as well as downloading from [kernel.ubuntu.com]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

What kernel did you want?

---

### Post by jpg123 on 2012-04-18
im having an overheating problem and my current kernel is 3.0.0-17 generic, ive read that the overheating problem is a kernel issue so i thought i might update/change it ad see if the overheating issue improves.

---

### Post by wojox on 2012-04-18
> **jpg123 said:**
> im having an overheating problem and my current kernel is 3.0.0-17 generic, ive read that the overheating problem is a kernel issue so i thought i might update/change it ad see if the overheating issue improves.

You could try these [v3.2-rc4-oneiric]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/").

Open a terminal Ctrl + Alt + T and one command at a time:
```
mkdir ~/kernel

cd kernel

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-headers-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-headers-3.2.0-030200rc4_3.2.0-030200rc4.201112012035_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-image-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb

sudo dpkg -i *.deb

sudo update-grub

```

Restart and you can pick that kernel. :p

---

### Post by jpg123 on 2012-04-19
my architecture is i386, would it be compatible? or is that nor really relevent

---

### Post by codemaniac on 2012-04-19
> **jpg123 said:**
> my architecture is i386, would it be compatible? or is that nor really relevent

Seems like the wgotten .debs by wojox is of i386 arch .

---

### Post by jpg123 on 2012-04-19
thanks wojox, the code seemed to work, but im not sure how to pick the new kernel, will it automatically convert to the new one?

---

### Post by wojox on 2012-04-20
> **jpg123 said:**
> thanks wojox, the code seemed to work, but im not sure how to pick the new kernel, will it automatically convert to the new one?

It should boot right into it. If not reboot and hold down the left shift key. Run this command to see what is loaded:
```
uname -a
```

---

### Post by jpg123 on 2012-04-21
thanks again wojox, it worked so its sorted.

---

