---
title: "Backup"
date: 2006-05-07
forum: General Help
---

### Post by giddy1945 on 2006-05-07
I now have the 'backup.tgz' ( as outlined in this thread: [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)) copied to a 4.7G DVD. 
         It is one single 2.3G file. Let's say that my harddrive fails beyond repair. I go buy a new harddrive and install it. What do I do with the disk? Do I just plop it in as if it where the 'install' CD? Do I use the 'live' CD? 


Never have used the $oft and never will.

---

### Post by aysiu on 2006-05-07
The thread you linked to has restore instructions as well.
You can use a live CD if your installation is unbootable.
Otherwise, you can also use the mounted DVD.

---

### Post by giddy1945 on 2006-05-07
I did not notice any instructions in that thread that suggested that I could boot from the CD that contains the one compressed file.  I am just making sure that I could actually do that as if it were the install CD.  I will  incert the CD and boot from CD ROM as if it is the "install" CD.  Based the number of posts you have initiated, I will trust your judgement and review the thread, interpret it as best I can, and continue.
     I am brand new to computers (5 months).  I do have my box performing in a manner that meets my requirements; however, I,being a newb, could lose all of it with one command.  It took me five months to figure this out, and I just don't want that to happen.
      That being said, I will wait awhile to see if you or  anyon else has any further suggestions before I continue.
     Thank you for the reply.

---

### Post by aysiu on 2006-05-07
No, you won't be able to boot from the CD and have it automatically load your system.

You would need to either...

1. Have two drives--one CD-ROM for booting the live CD, another DVD-ROM for reading from the DVD you burnt.

or

2. Have a workable installation (that's broken but still bootable) and copy the backup file back to your root partition and the extract it.

---

### Post by giddy1945 on 2006-05-08
OK.  I'll use both the CD ROM and the DVD ROM.  I'll report on what happens.  Thank you.

---

### Post by giddy1945 on 2006-05-14
OK. I have done what aysiu told me to do, but it did not work.  I used both the DVD ROM and the CD ROM, and I switched them both up with both CDs incase the instructions given were vise versa.  
Maybe I am booting from the wrong drive.  Whitch CD do I actually boot from?  If I boot from the live CD, the sesion comes up, and the desktop that comes up is similar to the install default.  My question is,"What then?".

---

### Post by aysiu on 2006-05-14
Sorry. I should have explained better.

You boot up the live CD.

Once the live CD is up and running in its session, you pop the DVD backup into the other drive.

Wait for it to mount.

Then, you mount the hard drive and un-tar your backup from the DVD to your hard drive. Let me know if you need help mounting your hard drive in the live CD environment.

---

### Post by giddy1945 on 2006-05-15
Thank you for checking back in after the few days.  I will report back.

---

