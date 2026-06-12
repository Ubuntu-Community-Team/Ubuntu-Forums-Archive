---
title: "Is their a better way to erase a drive then &quot;sudo dd if=/dev/zero of=/dev/XXX&quot;?"
date: 2009-12-18
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-18
I've been searching around Google for a way to wipe a drive (fill it with zeros) in Ubuntu but the best I can find is "sudo dd if=/dev/zero of=/dev/XXX" with "XXX" being the drive you want erased, it seems to work but (1) it doesn't tell me stuff like KiBps, time remaining, percentage complete, etc, and (2) it will eventually crash my computer before completing for what reason I do not know because it's not erasing a system drive it's erasing a flash drive and it's unmounted.

So does anyone know a better way to wipe drives in Ubuntu? Not by booting into DBAN, even though I love DBAN I need something that I can still use my computer while it's running, and preferably have a GUI or at least info in a terminal of when it'll complete wiping the drive.

Also before someone says something about me wiping a flash drive will wear it out, yes I know it will but I think the flash drive is already wearing out and I wanted to completely wipe it to see if it helps any before I have to dig up the receipt to return it.

---

### Post by wojox on 2009-12-18
You can shred it.

```
man shred
```

---

### Post by Leppie on 2009-12-18
you could also try to format it using gparted.

---

### Post by KeyserSoze93 on 2009-12-18
> **wojox said:**
> You can shred it.

```
man shred
```

+1 for shred. much faster then dd.

---

### Post by TheOnlyMrK on 2009-12-18
> **Leppie said:**
> you could also try to format it using gparted.

Yeah but that only reformats it, I'm looking to erase the drive to make it like it's brand new, or at least appear to be to the operating system.

---

### Post by dcstar on 2009-12-18
> **TheOnlyMrK said:**
> Yeah but that only reformats it, I'm looking to erase the drive to make it like it's brand new, or at least appear to be to the operating system.

Then you use gparted to write a new partition table: Device-Create Partition Table.

---

### Post by TheOnlyMrK on 2009-12-18
> **dcstar said:**
> Then you use gparted to write a new partition table: Device-Create Partition Table.

But that still doesn't wipe the drive, data can still be recovered if you use the right software.
Anyways I will try using the "shred" command later tonight and see how it does.

---

### Post by TheOnlyMrK on 2009-12-21
> **wojox said:**
> You can shred it.

```
man shred
```

I'm trying it now, it seems to be working fine so far except the info doesn't seem to update;

```
mike@mike-desktop:~$ sudo shred -v -z -n 0 /dev/sdc
shred: /dev/sdc: pass 1/1 (000000)...
shred: /dev/sdc: pass 1/1 (000000)...541MiB/7.6GiB 7%
```

it's been like that for over 10minutes, but at least it doesn't eat my RAM till the computer crashes like dd does, instead I can see the RAM go up for a little then going back down ~10seconds later. So thank you.

---

### Post by johngreth on 2010-02-25
My vote goes to dban. I have some info about it on [my blog]("http://johngreth.com/blog/?p=4")...

---

