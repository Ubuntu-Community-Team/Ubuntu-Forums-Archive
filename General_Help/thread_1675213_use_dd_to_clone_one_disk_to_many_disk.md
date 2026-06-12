---
title: "use dd to clone one disk to many disk"
date: 2011-01-25
forum: General Help
---

### Post by cazz on 2011-01-25
Hi
I was thinking about make a clone machine.
I was thinking about use a old computer that have some SATA connection. One disk is source and then I add some other disk to destination.
I going to have Linux on USB stick.

I have look at dd and it look nice but what I can see it only use one disk to another. 

```
dd if=/dev/hdx of=/dev/hdy
```

is it possible to add more then one destination?

---

### Post by Smart Viking on 2011-01-25
Just create a script with several lines like that but different drives.

---

### Post by frostschutz on 2011-01-25
By default, there is only one destination.

However there are programs that can duplicate stdin/out to multiple processes. So you could have dd if= | tpipe several dd of=.

Alternatively you could cheat and create a mirroring md device (Soft RAID 1 or similar) for all your target devices and use a single dd to write to that.

---

### Post by cazz on 2011-01-25
> **Smart Viking said:**
> Just create a script with several lines like that but different drives.

I was hopping to make one run time to many to save time.

> **frostschutz said:**
> By default, there is only one destination.

However there are programs that can duplicate stdin/out to multiple processes. So you could have dd if= | tpipe several dd of=.

Alternatively you could cheat and create a mirroring md device (Soft RAID 1 or similar) for all your target devices and use a single dd to write to that.

any idea about the name of the program :)

---

### Post by ajgreeny on 2011-01-25
I see no reason why a script could not do it all in one operation, though admit I have only used dd a very few times, and generally in the past for copying to floppy disks.

Just write the shell script with each command on a separate line, and then run it.

```
#!/bin/bash
dd if=/dev/sda of=/dev/sdb &
dd if=/dev/sda of=/dev/sdc &
dd if=/dev/sda of=/dev/sdd &
```etc etc.

The & is needed to allow the commands to run without each one waiting for the previous one to finish.

---

### Post by psycho5 on 2011-01-25
> **ajgreeny said:**
> I see no reason why a script could not do it all in one operation, though admit I have only used dd a very few times, and generally in the past for copying to floppy disks.

Just write the shell script with each command on a separate line, and then run it.

```
#!/bin/bash
dd if=/dev/sda of=/dev/sdb &
dd if=/dev/sda of=/dev/sdc &
dd if=/dev/sda of=/dev/sdd &
```etc etc.

The & is needed to allow the commands to run without each one waiting for the previous one to finish.

Wow wouldn't that take a hefty computer to complete that task? Any risk of data being corrupt? Since they are running simultaneously. I'd rather do it the Raid 1 way.

---

### Post by ajgreeny on 2011-01-25
> **psycho5 said:**
> Wow wouldn't that take a hefty computer to complete that task? Any risk of data being corrupt? Since they are running simultaneously. I'd rather do it the Raid 1 way.
I don't really know how cpu intensive dd is, but I would have thought not very, and I also have no experience of any RAID systems at all, so can not comment on that either.

You could well be correct, however, and I will leave it to those with more knowledge than I, to discuss this further.

---

### Post by cazz on 2011-01-25
ok, I was thinking maybe I can make somekind of multicast inside a competer.

Have to see what I going to do

---

