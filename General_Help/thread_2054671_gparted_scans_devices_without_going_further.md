---
title: "gparted scans devices without going further"
date: 2012-09-07
forum: General Help
---

### Post by ezsit on 2012-09-07
I just installed Xubuntu 12.04.1 and updated and installed all my usual apps including gparted. 

Running gparted from the menu and running from terminal with 'gksudo gparted' results in the same behavior with no output to the command line. All I get is the gparted program scanning all devices indefinitely. 

I have let it run for over ten minutes with no change in behavior. Any one else experience this behavior? 

I have tried running gparted with no external usb drives connected, with a flash drive connected, and with an external hard drive via usb connected, all with the same result.

Thanks for any help.

PS. I searched for threads on 'gparted' but nothing recent and or relevant came up.

---

### Post by cryptotheslow on 2012-09-07
What message is showing in the bottom left of the gparted window? (Should be something like "Scanning /dev/sda partitions")

Also how many partitions do you have and what type?

This command should let us know:
```
sudo fdisk -l
```

gparted takes around 25 - 30 seconds scanning for partitions for me with just 7 partitions.

---

### Post by ezsit on 2012-09-11
Sorry to have taken so long, but I have one internal hard drive, 1TB split into four primary Linux partitions (one swap 4gb, and three ext3: 4gb, 40gb, and 950gb) and the behavior occurs whether I have no other external drives plugged in, or whether I have a flash drive or an external 1TB USB drive with two 500gb linux partitions.

I did wait it out and after fifteen minutes gparted finally finished scanning all devices and becomes usable, but this process only took a few seconds under all previous versions of Ubuntu.

Worse yet, between each operation it takes about fifteen minutes for gparted to scan all devices again and again... ARGHHHHH!!!!

PS "fdisk -l" command just sits there returning nothing for longer than my patience. I have run fschk from a live cd and the disk appears fine.

I do not mind using cfdisk and mkfs, which seems to work just fine, but gparted is so pretty. :)

---

### Post by ezsit on 2012-09-11
Found my answer: I had the bios set to see a floppy drive when there was none and this is an old bug in gparted that has never been fixed. Now it works as it should. I do not know how that bios setting got changed, maybe an old cmos battery. I'll have to check that. Thanks anyhow.

---

