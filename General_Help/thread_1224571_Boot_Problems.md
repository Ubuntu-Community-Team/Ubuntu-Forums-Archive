---
title: "Boot Problems"
date: 2009-07-27
forum: General Help
---

### Post by FedoraJones on 2009-07-27
Hello everyone,

I've lurked these forums for a while whenever an Ubuntu problem pops up and have always found them helpful, so hopefully someone can figure out my current problem.

My desktop is currently set up to dual-boot Vista and Ubuntu Jaunty, using GRUB as the boot loader. It worked fine for several months, then suddenly developed an odd problem. When I try to start up my computer, it gets to "Verifying DMI Integrity........Successful!" (or a similar message), then hangs with a blinking cursor. However, if I put in my Vista DVD (or it's already in from before I shut off the computer), it'll display a message to press any key to boot from the CD-Drive, and if I don't, the GRUB menu shows and everything boots up fine. I haven't tried it with any other bootable CDs (though I know it doesn't work with non-bootable CDs since I've left game CDs in there with no luck), but I'd obviously like for it to work without the need for any CD/DVD to be in there. 

I found some instructions on how to fix a messed up boot loader, which said to boot into Ubuntu, open a terminal, and type

[INDENT]grub
[/INDENT][INDENT]find /boot/grub/stage1
[/INDENT]
which gave me "(hd0, 1)" as output. However, when I tried to continue on with the instructions by typing in

[INDENT]root (hd0, 1)
setup (hd0)
[/INDENT]I recieved an error that there is no such hard drive. 

If anyone can help me I'd appreciate it, before I go through and try reinstalling Ubuntu to see if that fixes the problem.

Thanks!

---

### Post by mikewhatever on 2009-07-27
I don't think there should be a space in (hd0,1), or in other words, not [s](hd0, 1)[/s].

---

### Post by philcamlin on 2009-07-27
> **mikewhatever said:**
> I don't think there should be a space in (hd0,1), or in other words, not [s](hd0, 1)[/s].

there shouldent :)

hope that helps you fix it :popcorn:

---

### Post by FedoraJones on 2009-07-27
Lol! Thanks for the quick fix. That seemed to make everything execute correctly in the instructions I was following, but unfortunately my problem remains. I tried changing the boot order of the CD and hard disk, but that didn't do anything either. This seems like such an odd problem, since it's obviously possible for the computer to boot via hard disk, it's just acting like it doesn't want to.

---

### Post by loomsen on 2009-07-27
so you get a grub command line only?

Try typing, each line on its own,

```

root (hd0,1)
kernel /vmlinuz
initrd /initrd.img
boot

```

I don't have ubuntu installed at the moment, but if I remember correctly ubu creates links to the kernel (vmlinuz) and the initial ram disk (initrd.img) in /
so
/vmlinuz
/initrd.img
should be the files.

If you get a file not found for the commands above, try

```

kernel (hd0,1)/vmlinuz
initrd (hd0,1)/initrd.img

```
or
```

kernel (hd0,1)/boot/vmlinuz
initrd (hd0,1)/boot/initrd.img

```
instead. Depending on your systems setup and where ubuntu creates the links this may vary. However, you should be able to boot up your system like this, as you said it used to work. Maybe the howto in my sig helps too.

---

