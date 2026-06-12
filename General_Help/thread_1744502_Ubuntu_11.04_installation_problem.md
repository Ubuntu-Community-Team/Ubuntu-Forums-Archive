---
title: "Ubuntu 11.04 installation problem"
date: 2011-04-30
forum: General Help
---

### Post by j0suk on 2011-04-30
hello guys, im trying to get ubuntu for the 1st time. I install with wubi, reboot, take ubuntu, it load up, but when it is done it comes with the message:
No root file system
there is not defines any root file system!

i dont understand this??

My computer is a dell dimension 9200

thanks

---

### Post by linuxliam on 2011-04-30
Ok, I'm guessing from the fact that you mentioned WUBI that you are trying to install Ubuntu 11.4 through Windows?   Wubi is not as stable as the other methods of installing Ubuntu, so if you can, burn the ISO image to a blank CD/DVD and boot from that. Then you can try it out and install.  Feel free to reply back...

---

### Post by j0suk on 2011-04-30
ive tried doing that and it didnt work out eather, it said the same after the whole process was almost done

---

### Post by linuxliam on 2011-04-30
Another approach you could take is:  1) Insert the Ubuntu disc 2) Start going through the installation 3) When you get to the part about partitioning and whether you would like to run Ubuntu alongside Windows, use the drop down box at the bottom of the window to select a root location. 4) Cross your fingers!

---

### Post by Rubi1200 on 2011-04-30
Are you still on the LiveCD right now?

If yes, run this command in the terminal:

```
sudo parted -l
```
(lowercase L not 1)

If you are back in Windows already, go to Disk Management and post a screenshot of how Windows sees the disk.

Thanks.

---

### Post by j0suk on 2011-04-30
[http://img204.imageshack.us/f/hdfgh.png/](http://img204.imageshack.us/f/hdfgh.png/)
here it is.
its in danish, but hope it still makes sence.

---

### Post by j0suk on 2011-05-01
and noooo further help.......
i will never be able to try ubuntu :(

---

### Post by bcbc on 2011-05-01
Usually this is due to:
1. mix of GPT and MBR partition table - this confuses ubiquity
2. leftover fakeraid metadata or unsupported raid option

If you burn an Ubuntu CD (or USB), boot from it, select "Try without installing" and run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) it should give some clues.

---

