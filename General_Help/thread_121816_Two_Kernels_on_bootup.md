---
title: "Two Kernels on bootup?"
date: 2006-01-26
forum: General Help
---

### Post by Puptentacle on 2006-01-26
Maybe this is an obvious question. If so, sorry and move it to Newbies...

I'm dual booting Ubuntu and The Evil Ones Last Spawn, XP. When GRUB comes up, it shows me two linux kernels. 2.6.12-10-386 and 2.6.12-9-386. When I did the second install I know it was only showing me 2.6.12-9-386. It upgraded the kernel during my install. 

Is this normal? Will I get a separate kernel listed there every time the kernel upgrades? Could I conceivably boot from either kernel? Am I losing my mind?

Appreciate any help!

---

### Post by Iandefor on 2006-01-26
> Maybe this is an obvious question. If so, sorry and move it to Newbies...

I'm dual booting Ubuntu and The Evil Ones Last Spawn, XP. When GRUB comes up, it shows me two linux kernels. 2.6.12-10-386 and 2.6.12-9-386. When I did the second install I know it was only showing me 2.6.12-9-386. It upgraded the kernel during my install. 

Is this normal? Will I get a separate kernel listed there every time the kernel upgrades? Could I conceivably boot from either kernel? Am I losing my mind?

Appreciate any help! If you upgrade your kernel, the old one is still installed. So, yes, you could easily boot between two different kernels. You can also uninstall the old kernel via Synaptic (if you boot into the new kernel, of course!). It should update grub automatically.

---

### Post by o_fortuna on 2006-01-26
[QUOTE=Puptentacle]Maybe this is an obvious question. If so, sorry and move it to Newbies...

I'm dual booting Ubuntu and The Evil Ones Last Spawn, XP. When GRUB comes up, it shows me two linux kernels. 2.6.12-10-386 and 2.6.12-9-386. When I did the second install I know it was only showing me 2.6.12-9-386. It upgraded the kernel during my install. 

Is this normal? Will I get a separate kernel listed there every time the kernel upgrades? Could I conceivably boot from either kernel? Am I losing my mind?

Appreciate any help![/QUOTE]
This is normal since the kernel is stil installed and you can boot it (but don't). To remove it, you can edit /boot/grub/menu.lst:
```
sudo gedit /boot/grub/menu.lst
```
Just remove any paragraph that has your kernel name. It will probably look like this:
```
title		Ubuntu, kernel 2.6.12-9-i386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-i386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-i386
savedefault
boot
```

On second thought, go into synaptic, look for that particular kernel (ending in 9-i386) and remove all instances of it. As long as you still have the 10-i386 installed (ie don't uninstall it!), you will be find. Then it should go away.

And here I am babbling again. The kernels don't do anything, and they won't harm you except for cluttering GRUB. So, option A if you want to clean up GRUB, option B will save you a few megabytes on your system and clean up GRUB.

---

### Post by Puptentacle on 2006-01-26
Thanks a ton for the quick reply!

It seems this is a good thing on the one hand. If there is a problem with a new kernel install you have the old one still sitting there to fall back on. NEAT!

Thanks for the quick replies and useful info! I've been trying to find the answers to questions myself, but that one was stumping me.

---

### Post by byen on 2006-01-26
> It seems this is a good thing on the one hand. If there is a problem with a new kernel install you have the old one still sitting there to fall back on. NEAT!
Yes. That is what i do... after the new updated kernel comes in I use it for a few weeks and then get rid of the old one...  better off being safe I guess..

---

