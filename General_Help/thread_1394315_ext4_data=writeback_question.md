---
title: "ext4 data=writeback question"
date: 2010-01-30
forum: General Help
---

### Post by J V on 2010-01-30
I'm about to reboot after adding data=writeback to my fstab, I have used tune2fs, but I have not added it to grub (coulden't find any grub options for it)

I've heard that this could screw up my system (mounting root partition as read only), will this work? If not, how do I fix? I don't want to reboot until I'm sure im not gonna lock myself out...

(btw, I heard ext3 journaling was faster than writeback, how is ext4 in this regard?)

---

### Post by falconindy on 2010-01-30
Here's the applicable section from 'man mount'. Both Ext3 and Ext4 support the data=writeback option.

```
       data={journal|ordered|writeback}
              Specifies  the journalling mode for file data.  Metadata is always journaled.  To use modes other than ordered on
              the root filesystem, pass the mode to the kernel as boot parameter, e.g.  rootflags=data=journal.

              journal
                     All data is committed into the journal prior to being written into the main filesystem.

              ordered
                     This is the default mode.  All data is forced directly out to the main file system prior to  its  metadata
                     being committed to the journal.

              writeback
                     Data  ordering is not preserved - data may be written into the main filesystem after its metadata has been
                     committed to the journal.  This is rumoured to be the highest-throughput option.  It  guarantees  internal
                     filesystem integrity, however it can allow old data to appear in files after a crash and journal recovery.
```

If you're unsure of what this is going to do, why are you doing it on your live system? What is it you're trying to accomplish?

---

### Post by J V on 2010-01-30
A bit of a speed boost...

And it is in use in ext4, numerous people have [said so]("http://ubuntuforums.org/showthread.php?p=7171766#post7171766") on these forums... Perhaps cause it is backwards compatible...

What I'm worried about is that another page said something about not working unless you edit grub.cfg... and I don't really want to do that...

---

### Post by falconindy on 2010-01-30
Oops. Double post...

---

### Post by falconindy on 2010-01-30
Unlikely you'll need to change grub. You're right that this requires recreating the metadata using tune2fs, though. In order to do so, you'll need to boot off a liveCD and do this with the drive unmounted.

If I were you, I'd do this on a VM first (such as VirtualBox) before doing anything to your live rig. At least this way you can be familiar with the process and possibly anticipate any pitfalls.

---

### Post by skymera on 2010-01-30
I saw some benchmarks performed comparing EXT4 in Journaled mode and Data Writeback.

The difference was about 0.2MB/s#

Agh, can't find the source

---

### Post by J V on 2010-01-30
Oops, then we have another problem... I kinda had my drives mounted when I used tune2fs :S

I'm gonna have a pain in the *** amn't I? -_-

And skymera, if 0.2 is all it gives me, and the following code block states transfer rate of... 85, is it worth it?
```
sudo hdparm -Tt /dev/sda5

/dev/sda5:
 Timing cached reads:   6398 MB in  2.00 seconds = 3202.34 MB/sec
 Timing buffered disk reads:  258 MB in  3.01 seconds =  85.75 MB/sec
```

Edit: Reboot worked, grub works normally, [SOLVED]

---

### Post by skymera on 2010-01-30
> **J V said:**
> Oops, then we have another problem... I kinda had my drives mounted when I used tune2fs :S

I'm gonna have a pain in the *** amn't I? -_-

And skymera, if 0.2 is all it gives me, and the following code block states transfer rate of... 85, is it worth it?
```
sudo hdparm -Tt /dev/sda5

/dev/sda5:
 Timing cached reads:   6398 MB in  2.00 seconds = 3202.34 MB/sec
 Timing buffered disk reads:  258 MB in  3.01 seconds =  85.75 MB/sec
```

Edit: Reboot worked, grub works normally, [SOLVED]

Not bad speeds. That from a 10k drive?

I've run Ubuntu from 7.04 through 10.04. Having data=writeback on most of them. And i'd say the gain is minimal and to be fair, i never really noticed any improvement.

---

