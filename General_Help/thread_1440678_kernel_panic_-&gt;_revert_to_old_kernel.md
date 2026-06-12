---
title: "kernel panic -&gt; revert to old kernel"
date: 2010-03-27
forum: General Help
---

### Post by noob* on 2010-03-27
Hi I'm sorry if this is a noob question, but i didnt know how to search for the answer with google. 

So recently after some updates and messing with fstab, I got a "kernel panic: unable to mount root fs on unknown block" error on bootup with one the newest grub kernel entry. I've tried recovery console for that with no success (prob cause the kernel won't even come up..duhh). So I reverted back to an older kernel entry, which is working fine so far. So I have a few questions regarding this.

1. wth? are these grub entries like some sort of virtual machine things with each entry being some commit?

2. did messing with fstab to automount partitions cause my kernel panic? added entries below

> /dev/sda2 /media/Storage ntfs rw,auto,user,fmask=0111,dmask=0000 0 0
/dev/sda1 /media/Windows7 ntfs rw,auto,user,fmask=0111,dmask=0000 0 0


3. can i just keep using the older kernel? what's the difference?

I appreciate your help ;)

---

### Post by noob* on 2010-03-27
.......bump

---

### Post by jerrrys on 2010-03-27
never dealt with kernel panic, but this can help your search

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by noob* on 2010-03-27
any comments on how grub works?

---

### Post by falconindy on 2010-03-28
> **noob* said:**
> did messing with fstab to automount partitions cause my kernel panic? added entries below

Probably, yes. Why not comment them out and try booting the new kernel?

You should change your fstab entries to use the UUID instead of the static device file name. An example out of my fstab:
```
UUID=6cddd5bb-3210-4260-9cc1-96c564f65fac   /                   btrfs   defaults,relatime,compress          0 1
```
The console program 'blkid' will happily tell you the UUID for each partition.

---

### Post by noob* on 2010-03-28
falconindy: I already tried commenting out those fstab entries, but it didn't work. I was concerned if they did permanent damage. 

and what's the difference between using uuid vs device name?

and thanks for the reply!

---

### Post by falconindy on 2010-03-28
device nodes for hard drives can change on boot. While they **usually** stay the same, there's no guarantee that they'll be the same on the next bootup. The only time UUIDs change is when you reformat the partition. It's simply a more robust way of defining a partition. You can use similar LABEL= syntax to identify a drive by its label.

BTW, the extra entries in GRUB are for each individual kernel installed on your system. There's essentially two camps of software in Linux: kernel land and user land. Kernel land can change and user land will stay happy. You're booting a different kernel to the same user land. As you've discovered, this flexibility can be immensely helpful.

---

### Post by john newbuntu on 2010-03-28
As for the kernel panic problem, try completely uninstalling the kernel that is causing the problem(obviously not the current kernel) from Synaptic (System->admin->synaptic package manager).  Choose the linux-headers-xxx and linux-image-xxx corresponding to the version giving your the problem.

Then mark the same for re-install and hit apply.  Reboot and choose the newly installed kernel and see if it helps.

---

### Post by noob* on 2010-03-28
> **falconindy said:**
> \
BTW, the extra entries in GRUB are for each individual kernel installed on your system. There's essentially two camps of software in Linux: kernel land and user land. Kernel land can change and user land will stay happy. You're booting a different kernel to the same user land. As you've discovered, this flexibility can be immensely helpful.

oh so it's a layer of abstraction(ie changes to 'kernel land' layer are independent of 'user land' layer?) thanks again!

john newbuntu: thanks thats exactly the answer I was looking for.

---

