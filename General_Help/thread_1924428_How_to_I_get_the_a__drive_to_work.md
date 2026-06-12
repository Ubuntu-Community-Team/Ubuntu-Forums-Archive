---
title: "How to I get the a:  drive to work?"
date: 2012-02-12
forum: General Help
---

### Post by jbocean on 2012-02-12
I'm running Ubuntu 10.04 on an old Dell Dimension 4550. It has an a: drive and I found some old floppy disks that I want to see whats on them. But the computer isn't recognizing the drive or the disks.

What do I need to do to get the a:  drive working?

Thanks,
jbocean

---

### Post by matt_symes on 2012-02-12
Hi

Is the drive enabled in the BIOS. If it is has Ubuntu seen it and created a device node for it ?

From the terminal

```
ls /dev/fd*
```

Does this return anything ? Post back the results.

Assuming there are no problems above then put a floppy in it and mount it manually.

```
sudo mount /dev/fdX /mount/point
```

If your unsure how to do this then post back.

I assume you have a floppy driver loaded?

```
lsmod | grep -i floppy
```

Does your floppy have an entry in /etc/fstab ?

Kind regards

---

### Post by oldfred on 2012-02-13
Someone posted this:

[http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*

---

