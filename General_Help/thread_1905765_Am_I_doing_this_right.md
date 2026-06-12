---
title: "Am I doing this right?"
date: 2012-01-07
forum: General Help
---

### Post by Jaybyrrd on 2012-01-07
Ok so I want to finally dual boot with 11.10 and Windows 7 (Tired of Wine). My computer has two hard drives, a 320 gb which has Ubuntu currently, and a 1 tb which I was using as a place to store files.

This is what I am currently doing and want to know if my approach will work. First I am transferring out all of my from my files from the 1 TB drive "Big Pappa" to my current Ubuntu install (as I had only used 150gb on Big Pappa and have plenty of room on my 320gb). Then I am going to wipe the 1 tb drive clean. Next I am going to go into my BIOS and create a partition out of the 1 TB (I will be disconnecting the 320gb while doing this in order to make sure nothing goes awry, but is that even necessary?) I will be making a 350gb partition and a 650gb partition. Then I am going to install Windows 7 to the 350gb partition and use the 650gb as my storage partition.

Will that conflict at all with Ubuntu, and how do I make it so that my computer gives me the choice between which OS I want to run at boot?

Should this work?

---

### Post by ajgreeny on 2012-01-07
If you disconnect the ubuntu drive and install windows on the only remaining drive, obviously ubuntu will not be touched.  Check that windows will boot properly, then shutdown and reconnect the ubuntu drive.

You will now need to boot with the ubuntu drive as first boot device in your BIOS, and once in ubuntu run command ```
sudo update-grub
``` which will add windows to your ubuntu grub menu.

It should be simple, but it's a long time since I used windows, and that was XP, so I may have either forgotten something, or simply be completely out of date.

---

### Post by Jaybyrrd on 2012-01-07
I was pretty sure that I was going to be fine with how I was doing it, one just can't help but be worried when dealing with sensitive data.

---

### Post by Jaybyrrd on 2012-01-07
Also how do I make grub ALWAYS come up on boot?

---

### Post by bluexrider on 2012-01-07
> **Jaybyrrd said:**
> Also how do I make grub ALWAYS come up on boot?
if the BIOS is set to boot the Ubuntu HDD first it will show GRUB

---

### Post by zvacet on 2012-01-07
I never work with 2 or more drives,but as others say it should be fine.Just want to make suggestion.Why don´t you install Windows on same drive where Ubuntu is and use bigger drive for data?Your 320GB disk is big enough for both OS. ;)

---

### Post by QIII on 2012-01-07
Installing Windows after Ubuntu on the same drive is a lot of work.

With two drives, it is as simple as unplugging one drive, installing an OS on the one still plugged in, shutting down, plugging in the drive, checking the boot order to be sure the Ubuntu drive is first, booting to Ubuntu and updating GRUB.

I have 5 physical HDDs and 5 OSes, each alone on one of the drives.  What is not partitioned for the OS is partitioned as NTFS and is just another drive for storage.  I can unplug 4 of the 5 drives and the one that is left will happily boot all by itself.

You're not out of date, ajgreeny.  That's how I do it when I want to fool around with a new OS.

---

### Post by Jaybyrrd on 2012-01-07
Alright, going in bios to make sure it boots to Ubuntu HDD like you said. Everything went through fine, and honestly this was a lot less work, the most time consuming part was getting the windows install started. (For some reason it took forever to start setup).

---

### Post by Jaybyrrd on 2012-01-07
Crap new issue, for some reason the Scratch Drive partition is now a read only filesystem. How do I fix this?

---

### Post by bluexrider on 2012-01-08
What are you calling a scratch drive? BTW it is better to start a new thread with a new issue. OH, don't forget to mark this one (SOLVED)

---

