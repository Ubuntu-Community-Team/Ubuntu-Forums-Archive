---
title: "Won't boot after a failed 10.04 update"
date: 2010-05-03
forum: General Help
---

### Post by Henery on 2010-05-03
I am not sure what is up I tried to install the update 10.04 but it failed I thought a well never paid attention to the errors and rebooted now I still get grub and after a bunch of errors terminal prompt but won't boot! I am able to use my windows partition that is how I am able to post can anyone help?

---

### Post by cacycleworks on 2010-05-03
Unfortunately, that's not a whole lot of info to go on... My usual procedure / recommendation would to next try booting to the ubuntu CD as a live cd to see what does or doesn't work. Double check the disc's md5. Then try a reinstall. 

After that, it's a matter of carefully noting the errors and googling for paths to a fix. I have found that sometimes, a new release will bring up sometimes ancient problems which get patched kind of quickly.

---

### Post by aboyce22 on 2010-05-03
I had the same experience. Upgrade seemed to complete fine, but bootup yielded only a black screen.

I reinstalled from installation USB thumb drive, which seemed to go flawlessly. But same end result. 

Running on IBM Thinkpad R51.

Any suggestions?
Thanks!
Al

---

### Post by cacycleworks on 2010-05-03
I googled *IBM Thinkpad R51 ubuntu install blank screen* and this might help:
[http://ubuntuforums.org/showthread.php?p=9217815](http://ubuntuforums.org/showthread.php?p=9217815)

---

### Post by Henery on 2010-05-03
Well my windows partition works fine witch is better than most lol!
I tried sudo apt-get update that was a no go I tried fsck no go I am unsure what to try!
I get so many errors io errors when it checks the file system it fails tried recovery mode ends the same way hmm I have no idea!
I know I can put a clean install on but what about all my files and proggies gone lol would like to have my regular desktop back helppp!

---

### Post by cacycleworks on 2010-05-03
> **Henery said:**
> Well my windows partition works fine witch is better than most ... but what about all my files and proggies gone lol would like to have my regular desktop back helppp!

If you can get a liveCD to work on a USB thumbdrive or CD, then get it going. Find your /home/username directory and do a tar-gz of it then copy that to your windows partition. Then post install, copy the tar-gz back to /home and unpack it. 

I believe ubuntu has "archiver" as a visual archive tool.

I almost always use the command line. The commands to use would be like this:
```
cd /home
tar -czfv home_backup.tgz username
```

Normally, I use the "places" menu to find or mount partitions on the computer. You can use the file browser to copy the .tgz file over to windows-land or a usb stick.

On my own personal installs, I always have /home as a separate directory and then everything else on /. This way, I leave /home alone and do a new install. While it doesn't reinstall programs (you do have to apt-get install everything again), it does keep all your defaults and settings saved (as those are in /home).

---

### Post by Henery on 2010-05-03
Ya this really does not seem like a solution doing a fresh install I will keep trying and see if I can get it!  Should have never tried it 10.04 I mean way to many bugs I should have known better but I like to try new things this is what ya get I guess lol!

---

