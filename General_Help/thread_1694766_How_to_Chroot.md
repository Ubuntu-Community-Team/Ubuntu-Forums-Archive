---
title: "How to Chroot"
date: 2011-02-24
forum: General Help
---

### Post by ki4jgt on 2011-02-24
I've been working on my dad's computer [had to reinstall Ubuntu] I had to make changes to Grub before the hard drive would boot, so I tried to chroot it. Ubuntu 10.10 using:

> sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

It said it was already mounted. I tried the disk utility and it said it wasn't&#8253;

---

### Post by ki4jgt on 2011-04-09
Bump

---

### Post by techunit on 2011-04-09
1. Why are you chrooting in to the computer?
2. Are you chrooting from the Live CD
3. Are you attempting to reinstall GRUB?
4. Is this a dualboot config

These fairly simple questions should help me figure out what the problem is. I will be leaving for Dinner in a bit so I'll take another look then.

PS. Don't Use Bump or Up because many of us will pass over problems that appear to have someone working on them. After about a day of no solutions reply to your thread asking again for help instead.

Good Luck.

---

### Post by AlphaLexman on 2011-04-09
From a terminal, what is the output of```
mount
```and, ```
cat /etc/fstab
```??

---

### Post by AlphaLexman on 2011-04-09
> **techunit said:**
> PS. Don't Use Bump or Up because many of us will pass over problems that appear to have someone working on them. After about a day of no solutions reply to your thread asking again for help instead.
To me It looks like they waited 45 days before 'bumping', and you're giving them a hard time?

---

### Post by techunit on 2011-04-09
> **AlphaLexman said:**
> To me It looks like they waited 45 days before 'bumping', and you're giving them a hard time?
Its still good advice regardless. I didn't notice though.

---

### Post by ki4jgt on 2011-04-09
I'm chrooting from the Live CD to the computer. I need to edit Grub and then update grub on the computer. (I can't boot without nolapic noapic and acpi=off) So I go into grub (On the hard drive) and add the three boot options, then I need to update grub on the hard drive from the LiveCD. I was able to accomplish this quite easily on 10.10, but 11.04 has been a pain :-(.

I can't post the terminal responses yet from mount and cat /etc/fstab I'm currently not at the computer :-(

---

### Post by 3Miro on 2011-04-09
This is what I use in Gentoo:
```
livecd usr # cd /
livecd / # mount -t proc proc /mnt/gentoo/proc
livecd / # mount --rbind /dev /mnt/gentoo/dev
livecd / # cp -L /etc/resolv.conf /mnt/gentoo/etc/
livecd / # chroot /mnt/gentoo /bin/bash
livecd / # env-update && source /etc/profile
>>> Regenerating /etc/ld.so.cache...
```

So In Ubuntu it should be something like this:
```
livecd / # cd /mnt
livecd /mnt/ # sudo mkdir /mnt/hddub
livecd /mnt/ # sudo mount /dev/something /mnt/hddub
livecd /mnt # cd /
livecd / # sudo mount -t proc proc /mnt/hddub/proc
livecd / # sudo mount --rbind /dev /mnt/hddub/dev
livecd / # sudo cp -L /etc/resolv.conf /mnt/hddub/etc/
livecd / # sudo chroot /mnt/hddub /bin/bash
livecd / # sudo source /etc/profile
>>> Regenerating /etc/ld.so.cache...
```

/dev/something is your Ubuntu / partition (i.e. /dev/sda1, /dev/sda3 ... )

The command about resolve is there is you need to get Internet in the Chroot environment. If all you need to do is reinstall Grub, ignore the resove.conf command.

The last line may not be needed, I am not sure about it.

---

