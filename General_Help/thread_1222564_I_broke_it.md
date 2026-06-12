---
title: "I broke it"
date: 2009-07-25
forum: General Help
---

### Post by Nexxes on 2009-07-25
Hello, everyone

I've been using Ubuntu through windows install with Wubi and recently bought a new hard drive.
So I installed it on the new hard drive with Grub boot loader on the first.
I started having problems with patching as it was saying there wasn't enough space, I tried doing what it suggested but still couldn't free up enough.

So I increased the partition size of the Linux Ext3 logical partition and now when I try to log into Ubuntu it goes into command prompt trying to fix it.

Of course I can just reinstall Ubuntu but to avoid getting stuck in this situation again how can I increase the storage to allow the patches?

Thanks, Nexxes.

---

### Post by guitarMan666 on 2009-07-25
That's a very good question.  What patches would you be referring to? Are you filling your new hard drive with Ubuntu or sharing it with Windows?  Did you install Ubuntu or Windows first?

If you answer those questions it would be easier to help you.
Thanks

---

### Post by bacil on 2009-07-25
I guess you have now two different installation and the one thats complaining about the space is the one installed by wubi on to the virtual disk in windows, while your new disk is unused ... this is pure guess ..

---

### Post by Nexxes on 2009-07-25
> **guitarMan666 said:**
> That's a very good question.  What patches would you be referring to? Are you filling your new hard drive with Ubuntu or sharing it with Windows?  Did you install Ubuntu or Windows first?

If you answer those questions it would be easier to help you.
Thanks

The automatic updates, I have Vista and windows 7 both on separate partitions and Ubuntu installed on its own logical partition.

I also uninstalled the Wubi Ubuntu installation.

My OS installs are:

Primary contains, Windows 7
Slave contains, Ubuntu(Broken), Vista(Separate Partition), Windows 7(Separate Partition)

There is nothing else on my Slave drive except [bootsqm.dat]

The order I installed OS' on slave was Ubuntu with Grub > Vista > Ubuntu without Grub > Windows 7 > Ubuntu with Grub (Again)

After I found out that Windows removes Grub then searched around to find out why it disappeared that's how I got 3 installs.

Hopefully that clears some things up

(Just to tell you I do only have 1 existing install of Ubuntu, I removed the others to reinstall)

---

### Post by guitarMan666 on 2009-07-26
I suggest installing Windows first.  When you install Ubuntu after windows GRUB works really well and even detects your Windows installs.  It looks to me like it's a little crowded on that slave drive, although I am unsure how big Windows Vista and 7 are.

I suggest you reinstall Ubuntu on the newly enlarged partition.  It should be fine.  Just make sure you tell the installer to format the partition.

---

