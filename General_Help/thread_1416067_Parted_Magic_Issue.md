---
title: "Parted Magic Issue"
date: 2010-02-25
forum: General Help
---

### Post by jose1986 on 2010-02-25
So I used a bootable cd of parted magic 4.8 and change my partitions to have a blank one that i could install windows on but this became my primary partition because that was the only option they gave me and i still have ubuntu on my computer, just on a different partition.  

The problem that happened after the partitioning finished, is that when I turn on my laptop, I only get a blank screen and no menu for parted magic, grub, or anything.  Am I even able to reformat my disc, my keyboard will not respond to other buttons pressed.  The scroll lock and caps lock keys are actually flashing during the starting process despite the computer not starting with anything besides some noise from the hard drive turning on and the monitor not making noise....

Someone please be of help?

---

### Post by oldfred on 2010-02-25
Can you boot with Ubuntu liveCD? or even the parted magic CD? It should not have modified the boot sector (MBR), but may have renumbered partitions so grub and fstab need updating for the system to work.

If you can boot a liveCD download and run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by dabl on 2010-02-25
> **jose1986 said:**
> 

 I used a bootable cd of parted magic 4.8 and change my partitions



If you _added_ a partition or _deleted_ a partition, then as oldfred says the numbering of partitions was changed.  But Grub was not changed -- it is still looking for Ubuntu in the partition number previously assigned.  So you will probably need to become a student of installing Grub2, once you are clear on which partition Ubuntu is now living.

---

### Post by jose1986 on 2010-02-26
i cannot see my monitor, therehas to be a way around this. my thoughts were to use parted magic to change ubuntu to the primary partition but when i turn on my laptop i cannot do anything and i have tryed the boot discs and hitting buttons.

---

### Post by oldfred on 2010-02-26
Ubuntu does not need to be on a primary partition but windows just about has to be.

If you do not see your monitor on boot it is a hardware issue. The BIOS should show the screen initially. I would check all connections and make sure connections inside computer are ok. Other wise you should be able to boot the CD.

---

### Post by Mark Phelps on 2010-02-26
If by not being able to "see your monitor", you mean that your screen is absolutely black -- no blinking cursor, no text, no background color, no menu -- then it could be a hardware failure.

You might have your BIOS setting configured to now show anything by default.  So, to confirm that your monitor even works, next time you boot, press the Del key repeatedly.  The often displays a BIOS text screen allowing you to set BIOS options.

If that key does nothing, and you have some PC documentation, see what key you need to press to get the BIOS screens to display.

---

### Post by jose1986 on 2010-02-26
Yeah, delete key did nothing.

---

