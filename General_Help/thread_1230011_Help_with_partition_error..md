---
title: "Help with partition error."
date: 2009-08-02
forum: General Help
---

### Post by Saprissa on 2009-08-02
Today I attempted to repair an installation of Vista that I almost never use.  It was on the computer when I bought it, but I immediately installed Ubuntu and hardly ever booted to Vista.

I tried to boot it and got a "missing bootmgr" message.  I was told to insert my original disc and repair the installation, but Vista never gave me a chance.  It moved immediately into "copying files" at which time I halted it, but the damage was done.

It appears it reformatted the hard drive partition table but did not reformat the partitions.  

Using the LiveCD and Partition Editor, I can see the partitions, but they are reported as an unknown file system.

Any chance I can recover the data from my drive?  I don't think it has been written over yet, and I have now disconnected it.

Thanks so much.

---

### Post by pastalavista on 2009-08-02
You might try going through the motions of an install (from the live CD desktop) just like normal but select the 'manual' installation which will take you to a partition editor. Leave everything as it is except uncheck all the 'format' boxes and install using the same user name. I've been told it doesn't write anything except files from the original install. You could lose data though, so back it up first.

---

### Post by Saprissa on 2009-08-02
Thanks.  I'll give it a try.

---

### Post by pytheas22 on 2009-08-02
If the advice above doesn't work, testdisk is a good program for fixing damaged partition tables.  To use it, boot to an Ubuntu live CD on the Vista computer, then install testdisk with:
```

sudo apt-get install testdisk
```

Next, run it by typing 'sudo testdisk' and following the instructions.  It will search for old partition tables and can attempt to restore their structure if you choose.

If testdisk fails to fix the partition table, or if the partitions turn out to have been partially reformatted, you can use photorec to try to recover the lost files, even if you can't mount the partition.  photorec is installed along with testdisk and can be run by typing 'sudo photorec'.

Also, it would be a good idea before doing anything else to make a copy of the Vista disk as it exists now, just so that you can go back to it in case you accidentally make things worse.  You can use [partimage]("http://www.partimage.org/Main_Page") on the SystemRescueCD to take an image of the disk, or the 'dd' command in Ubuntu.

---

### Post by Saprissa on 2009-08-02
Testdisk did the trick.

Thank you SO MUCH!

It is an amazing tool.

---

