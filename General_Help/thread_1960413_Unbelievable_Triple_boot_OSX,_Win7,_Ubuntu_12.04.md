---
title: "Unbelievable Triple boot OSX, Win7, Ubuntu 12.04"
date: 2012-04-17
forum: General Help
---

### Post by thinktyler on 2012-04-17
I used the lifehackers guide to triple booting on a MacBook Pro.

- MBP (5,2 Early 2009)
- Refit Installed
- Fdisk for Mac Installed


Windows will not boot, it just blink a cursor, UNLESS, I plugin my USB drive and my Windows 7 Disc, then everything is fine. This behavior occured after I installed Ubuntu.

Do I need to reinstall the Master Boot Record on the Win7 partition? Why am I required to boot Win7 with the USB drive and DVD/CD Win7 disc to "push" past the blinking cursor.


Kinda of a funny situation, but I didn't know exactly how to search for this on the forums.

---

### Post by thinktyler on 2012-05-04
Solution to this problem took a while to figure out.

Just in case it happens to anybody else.

I put in the Windows 7 DVD Install. Then used the repair tool. The first time it errored out, but the second time fixed the problem.


So, now strangely Ubuntu Grub boots before Refit. Which is exactly what I wanted, but I'm not sure how it happened. 

By hitting option key at boot I can get into refit. 

Perfect Ubuntu Triple boot now!

---

### Post by Ubun2to on 2012-05-04
Good to know you fixed your computer, but the MBR is not something you can reinstall, and it is not something you should ever modify. Let the OS installer do that for you-if you mess up those partition tables, your computer is basically unbootable until you get the hard drive wiped, and reinstall your operating systems. I'm not too sure Apple would be happy about that, either.
I'm a computer technician, mind you, so I know what I'm talking about when it comes to hardware and boot processes.

---

### Post by volanin on 2012-05-04
That's great thinktyler!
You may want to backup your MBR, in case some upgrade/reinstall messes up with it.
This way you can easily recover this triple boot setup when necessary.

Just do this command to backup:
It will create a ~20Kb file called *mbr.backup*.
```

sudo dd if=/dev/sda of=mbr.backup bs=512 count=40

```

And to restore:
```

sudo dd if=mbr.backup of=/dev/sda

```

Save this file in a pendrive, so you can restore using an Ubuntu CD.
And remember to backup again everytime you create or modify partitions!

[COLOR="Red"]**_Warning:_** This command only works on MACS and computers with a GPT Partition Table.
Anybody who doesn't have a MAC or don't know what GPT is, please use **count=1**.[/COLOR]

---

### Post by thinktyler on 2012-05-06
> **Ubun2to said:**
> Good to know you fixed your computer, but the MBR is not something you can reinstall, and it is not something you should ever modify. Let the OS installer do that for you-if you mess up those partition tables, your computer is basically unbootable until you get the hard drive wiped, and reinstall your operating systems. I'm not too sure Apple would be happy about that, either.
I'm a computer technician, mind you, so I know what I'm talking about when it comes to hardware and boot processes.

Thank you for clarifying what the MBR is/does. I played around with fdisk trying to create a hybrid mbr. Very technical documentations... Glad I didn't execute the command now.

> **volanin said:**
> That's great thinktyler!
You may want to backup your MBR, in case some upgrade/reinstall messes up with it.
This way you can easily recover this triple boot setup when necessary.

Just do this command to backup:
It will create a ~20Kb file called *mbr.backup*.
```

sudo dd if=/dev/sda of=mbr.backup bs=512 count=40

```

And to restore:
```

sudo dd if=mbr.backup of=/dev/sda

```

Save this file in a pendrive, so you can restore using an Ubuntu CD.
And remember to backup again everytime you create or modify partitions!

[COLOR="Red"]**_Warning:_** This command only works on MACS and computers with a GPT Partition Table.
Anybody who doesn't have a MAC or don't know what GPT is, please use **count=1**.[/COLOR]

thank you for this tip as well. I backed up the mbr to my Ubuntu one! Wahoo.

---

