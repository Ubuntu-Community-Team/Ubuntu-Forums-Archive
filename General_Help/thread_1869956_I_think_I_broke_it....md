---
title: "I think I broke it..."
date: 2011-10-26
forum: General Help
---

### Post by c11h17n2o2sna on 2011-10-26
This is going to be a long one, so thanks for reading in advance.

  I have a pc (vista 64) that crashed a while back and I have been trying to find a cheap way to recover my data since.

  I read in a forum that sometimes linux can read corrupted hard disks, so I proceeded to burn a ubuntu boot disk (11.10).  Loaded this on my laptop (vista 32) to try it out, and it worked.  I could access/copy files freely from my old hard drive that I have been unable to access since march.

  I have a blank 2tb internal drive that I had the idea of loading ubuntu on to use as the primary os for my pc.  I have never used ubuntu or any other os than windows for nearly 16 years, and theoretically this sounded like a good option.  My only working computer was my laptop, so I had my 2tb in an enclosure and planned on using the boot disk via usb and the "something else" install option.

  So I load the disk and power up.  At the main disk screen, i chose "install ubuntu".  I ended up canceling when I got an error about partitioning and privileges, and ubuntu loaded fully from the disk to desktop.  I then read that to have ubuntu as the primary os (no dual booting), partitions were not required. From here, i selected the "install ubuntu 11.10" icon thinking this would be the same as the initial menu install.  I chose the first option, which said all files would be kept intact during installation.

  I received a prompt about detecting multiple os's, and if I wanted to continue.  Since there was no threat of losing info implied, I selected continue.  Very quickly afterwards, i realized this was installing a dual booting system on my laptop as I never saw the partition manager screen before it began.  Not my intentions, but figured it wouldn't hurt to run ubuntu occasionally on my laptop as well, so I let it go.

  Prompted to reboot after installation, and watched the final shut down screen and removed the disk and hit "enter" to complete.  Restarted the machine and get the initial compaq boot screen, then goes directly to a flashing cursor, with no key input ability.  It will still boot from the disk, so I tried to find out what happened and come across another thread that says to reinstall.  Again, i go to the initial disk menu and chose install.  Now I only have "erase disk install" (and this says no os found) or "something else", so I go into something else where the partition manager shows my entire c: drive as free space with no partitions.  Did I wipe out my laptop? And if so, can it be restored?

  I also tried installing onto my blank 2tb, and the contents are identical when looking at devices/file system.

  On a somewhat related note, the importing documents and settings step took an hour or more.  Does this mean that the documents and settings folder was imported into ubuntu, and if so how is that accessed?  Sorry for the length of this, just wanted to give as much info as I could.  Thanks.

---

### Post by Nixarter on 2011-10-26
Can you please make paragraphs?  It is very difficult to follow when not separated into paragraphs.

---

### Post by nothingspecial on 2011-10-26
> **Nixarter said:**
> Can you please make paragraphs?  It is very difficult to follow when not separated into paragraphs.

Fixed :)

---

### Post by c11h17n2o2sna on 2011-10-26
I have since located my original partitions using parted's rescue tool, but still get a flashing cursor on startup.  

Is there an uninstall option?  Or a ubuntu alternative to easy bcd?

---

### Post by theDaveTheRave on 2011-10-26
You say that you get a simple flashing cursor on boot up.

How long have you left this to see if it changes to anything else? I have a rather old laptop that takes a while to get to a log in screen (long enough to get a coffee etc).

I don't know what the current default is in terms of 'echo' on a new install, but you have options that you should be able to get to to change this once you have started up.

You mention that with the live CD you are able to see your original windows partition, are you also able to see your 'Ubuntu' parition on the C:\ ??

Bear in mind it will not be called < c:\ > but something cryptpic like hda1 or sda1 (or something else maybe ?), from the live CD you may need to browse to the /dev/disk folder. This should contain a bunch of subfolders <by-uuid> <by-path> <by-id>, if you did parition your disk you will have multiple 'files' in each of these (there are effectively how linux 'thinks' of your HDD).

Also you say that you intended to boot from an external 1TB drive. I assume you have adjusted the BIOS of your laptop to allow boot from USB ?

Quickly on paritions... Although if you have Ubuntu (or any single OS) as your principle system you don't "need" partitions. However just because you don't need something doesn't mean that having it isn't a good idea (My car runs just as well with or without insurance :lolflag: paritioning your disk is equally a good idea as having insurance on your car ).

If you plan to have your Desktop using Ubuntu, and you have already been able to get all your old data back (and backed up somewhere). I would just run with Ubuntu straight to there, and not worry about having it on your laptop (untill you are more comfortable with stuff).

I'm not sure if that is helpfull or not...

David

---

### Post by c11h17n2o2sna on 2011-10-26
I tried leaving it, and after over 20 mins it was still sitting.  

I know what you mean about the partitions, I had originally set up 4 total but received the error that a partition could not be written.  after starting the process and thinking about it more (the longer it took to create the ext2 file system) i wished i had created one.  being that it just took me 17 hours to format the drive to ntfs via usb.

when booting with the cd the only partition i see on /dev/sda is this:

Model: ATA ST9250320AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  238GB  238GB  primary  ntfs


There was originally a recovery [d:] partition as well, and i have tried every combination of memory i can think of using rescue, but no others are recognized.

I have tried adjusting the boot order in bios and also toggling virtualization technology.  Neither of these worked either.

As far as running on my desktop, i can't get that to load either after i installed to the blank drive, but i think that machine has some other issues (i turn it on and it will power up, then power itself off, on, off, on and then start to boot?)  My intentions were to not load it on the laptop and just use the live cd if needed, but when it started the installer and I realized it was going onto my laptop's hard drive there was no cancel or quit option.  I was more worried about losing data, but nothing is lost yet so i was just hoping to get vista back up and running, or at least be able to fully load something without the disk.

---

