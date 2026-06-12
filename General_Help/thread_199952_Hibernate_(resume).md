---
title: "Hibernate (resume)"
date: 2006-06-19
forum: General Help
---

### Post by cbudden on 2006-06-19
Hey.  

If I leave some programs running when I hibernate, my laptop doesn't hibernate, and this messages flashes up for a few seconds on resume
```

Jun 19 20:06:15 localhost kernel: [17188365.156000] swsusp: Need to copy 70447 pages
Jun 19 20:06:15 localhost kernel: [17188365.156000] swsusp: Not enough free memory
Jun 19 20:06:15 localhost kernel: [17188365.156000] swsusp: Restoring Highmem

```

If I close some programs (usually firefox) it hibernates fine.

fdisk -l 
```


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5762    46283233+  83  Linux
/dev/hda2            5894        7296    11269597+  83  Linux
/dev/hda3            5763        5893     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

I have 512 mb of ram and assigned a gig of swap.

Any ideas?

---

### Post by ehula on 2006-06-20
[QUOTE=cbudden]Hey.  

If I leave some programs running when I hibernate, my laptop doesn't hibernate, and this messages flashes up for a few seconds on resume
```

Jun 19 20:06:15 localhost kernel: [17188365.156000] swsusp: Need to copy 70447 pages
Jun 19 20:06:15 localhost kernel: [17188365.156000] swsusp: Not enough free memory
Jun 19 20:06:15 localhost kernel: [17188365.156000] swsusp: Restoring Highmem

```

If I close some programs (usually firefox) it hibernates fine.

fdisk -l 
```


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5762    46283233+  83  Linux
/dev/hda2            5894        7296    11269597+  83  Linux
/dev/hda3            5763        5893     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

I have 512 mb of ram and assigned a gig of swap.

Any ideas?[/QUOTE]
I am getting similar results. I have GB of RAM and 2.5 GB of swap.

---

### Post by dave84 on 2006-06-20
hi everybody!

i were suffering from the same phenomenon.
perhaps I have a solution. at least give it a try.

1. look up the exact amount of swap space:
```
david@david-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515676     227224     288452          0       3184      58400
-/+ buffers/cache:     165640     350036
Swap:      2048248     210452    1837796
david@david-laptop:~$
```

2. now get administrator privileges and write the number of swap space into* /sys/power/image_size*
```
sudo -s
echo 2048248 > /sys/power/image_size
```

3. try hibernate again!

i hope i could help you. for the time being i don't know why acpi initialises with this number and which script does that.
maybe someone else could help us ati users.

lg david

---

### Post by ehula on 2006-06-20
It appears that the default for /sys/power/image_size is 500 MB, expressed in bytes (500 x 1024 x 1024). The result from the "free" command (kB) would need to be multiplied by 1024 to determine the number of bytes. But, having said that, I tried it and still get the same "not enough free memory" message.

---

### Post by cbudden on 2006-06-20
Well the first time I tried this, with firefox open (5 tabs) and 3 gaim windows and a terminal I hibernated fine.  I will post if it stops working.  Thanks dave84

---

### Post by cbudden on 2006-06-21
It seems that doing that works, but upon rebooting, it does not remember the value entered.

---

### Post by dave84 on 2006-06-21
[HTML]It seems that doing that works, but upon rebooting, it does not remember the value entered.[/HTML]

why don't you put this into your hibernate.sh script or better produce a new script for this special action. look into your hibernate.sh script.

i'll do this in the evening and post how to do it.

lg david

---

### Post by cbudden on 2006-06-21
Ok, I thought that I might be doing that.  I do that.  Would I need to have it prefixed with sudo or not ?

---

### Post by dave84 on 2006-06-21
no, not at all!

a simple

```

sudo -s
echo 'echo 2048248 > /sys/power/image_size' > /etc/acpi/suspend.d/01-image_size.sh
chmod +x /etc/acpi/suspend.d/01-image-size.sh

```

should do the trick.=D> 

lg david

---

### Post by cbudden on 2006-06-22
Thanks, I will see if that does the trick.

---

### Post by ehula on 2006-06-22
[QUOTE=dave84]no, not at all!

a simple

```
echo 'echo 2048248 > /sys/power/image_size' > /etc/acpi/suspend.d/01-image_size.sh

```

should do the trick.=D> 

lg david[/QUOTE]
Don't forget to do a:

sudo chmod +x /etc/acpi/suspend.d/01-image-size.sh

One more thing, in an earlier post I mentioned that the default image_size looked like it was 500 MB, expressed in bytes. The documentation I have read also seemed indicate that this value should be expressed in bytes, but others in this thread seem to be expressing image_size in kilobytes. I have now tried the above, and it is working for me, leading me to believe that image_size should be expressed in kB (kilobytes), contrary to what I have been reading elsewhere.

This would mean that the default image_size is actually set to 500 GB, which means that the error "not enough memory" is refering to the fact that it is unable to free up enough pages in swap to meet this requirement.

Thanks everybody for your help and insight.

---

### Post by cbudden on 2006-06-22
Yea I realised the chmod +x bit.  I use 1077501952 as a value from 1052248 readout from free.  Does that mean I should use 1052248 as that is a gig in KB (isn't it) rather than 1077501952 KB, which is rather more.

---

### Post by ehula on 2006-06-22
[QUOTE=cbudden]Yea I realised the chmod +x bit.  I use 1077501952 as a value from 1052248 readout from free.  Does that mean I should use 1052248 as that is a gig in KB (isn't it) rather than 1077501952 KB, which is rather more.[/QUOTE]
You should specify a size in kB (kilobytes). I am currently using the value reported by "free" as mentioned in one of the early posts in this thread. The value reported by "free" is in kB.

---

### Post by cbudden on 2006-06-22
Okey dokie, thanks for that.

---

### Post by sup on 2006-07-10
does this mean swap must be bigger than ram? I have only 256MB swap and 1GB RAM:-( - and I get the same error with hibernation.

---

### Post by cbudden on 2006-07-11
> **sup said:**
> does this mean swap must be bigger than ram? I have only 256MB swap and 1GB RAM:-( - and I get the same error with hibernation.

Your swap should be double the size of your RAM.

---

### Post by sup on 2006-07-11
Do you mean this generally or does it apply just for hibernation?
Because otherwise, my swap gets used hardly ever - I think I have never seen bigger use than 100MB...
Anyway I am _really_ looking forward to just another repartitioning...

---

### Post by cbudden on 2006-07-11
> **sup said:**
> Do you mean this generally or does it apply just for hibernation?
Because otherwise, my swap gets used hardly ever - I think I have never seen bigger use than 100MB...
Anyway I am _really_ looking forward to just another repartitioning...


It's generally advised to set your swap to double your RAM.  Also, if you swap isn't large enough to take all the RAM and whatever is in the swap then hibernate will not work because there is not enough space.

---

### Post by nanotube on 2006-07-11
> **cbudden said:**
> It's generally advised to set your swap to double your RAM.  Also, if you swap isn't large enough to take all the RAM and whatever is in the swap then hibernate will not work because there is not enough space.

well, it is generally advised, true, but i think the only difference you will see is the hibernate problem. i have 512m swap with 768m ram, no problems ever, except of course "not enough swap space for hibernation". but since i prefer suspend anyway (it's much faster both on suspend and on resume), it's just fine for me, and i save myself an extra gig of hd space, which is at a premium, since i run it on a 40g laptop, with dual boot.

well, that's my opinion on this, anyway :)

---

### Post by sup on 2006-07-11
so repartitioning was painful as usual, but it was worth it - hibernation works now! (suspend works as well, I think, but it does not manage to keep internet connection)

However, it works rather strange - when I choose hibernate, it blanks screen (with several rather interesting visual effects), then works with harddrive for quite some time and then it shuts down. When I then hit the power button, grub gets up as usual and when I choose to boot into linux, uspalsh appears, procces of reading boot files takes so muc htime it looks like it is freezed (it scared me a little actualy) and then voila - my gnome screen appeared and sudden sound of my headphones almost stunned me. 
I actually expected some nice screens like "hibernating now" "waking up from hibernation", but I was quite naive. But it works and is at least twice time faster then usual way, so it is great.

I just wonder what would happen if I choose different kernel from that which was hibernated.

---

### Post by mbeierl on 2006-07-12
Really bad things - don't try it.  If you're looking for a much nicer hibernate/resume splash, you should look at software suspend 2 at [http://www.suspend2.net/](http://www.suspend2.net/)

See [http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/) for an apt source for a software suspend 2 enabled kernel.

---

### Post by SylvainP on 2008-03-25
Just a note for Hardy users. If you were using the 01-image_size.sh script and use the "Hibernate" button from GNOME (System>Quit...>Hibernate), you will have to put the script at another location.

It should now be in /etc/pm/sleep.d/01-image_size.sh instead of /etc/acpi/suspend.d/01-image_size.sh (or it could be at both places). Apparently when suspending with GNOME, that uses the pm-utils packages which expects custom scripts at that location.

---

### Post by startherepodcast on 2008-05-13
Thank you, echoing the swap size to /sys/power/image_size did the trick!

---

