---
title: "Lost yaboot on dual boot"
date: 2006-03-26
forum: General Help
---

### Post by deteringb on 2006-03-26
I have been using Ubuntu blissfully along with OS9 (for the DVD player) for a couple of months now and could hardly be happier.  That is, until this afternoon when I did a reset-nvram and a reset-all under open firmware to try and reset my Pismo's battery.  Now the yaboot is gone and the machine only boots into OS 9.  I tried going into open firmware and "boot hd:9,yaboot" where hd 9 is the Linux partition, as recommended in the forums, but to no avail.  Next I was going to boot from the 5.10 disk and find a command line to rebuild yaboot, but before I do (and possibly blow up my Ubuntu), does anyone know a better way that won't compromise my Ubuntu install?  Thank you..

---

### Post by engla on 2006-03-26
Is it a very old mac [oldworld, the old grey boxes] or newer than that?

If it's newer then it should be easy: Either go into change startup disk and see if you can use select a different one there, or run the Apple boot loader at startup:

Press and **hold the Alt key** directly after the computer starts, you should get a screen with a button per partition and it should even display a penguin icon on the one with ubuntu on. 
Select it and go on with the boot, ubuntu should start.
When you are in ubuntu again, run **sudo ybin** in a terminal to reinstall yaboot.

---

### Post by deteringb on 2006-03-26
Thank you for the quick reply.  Its a new world mac (G3 Powerbook), when I hold down the option key to go into the boot loader and pick an OS, both 9 and Linux are there,  when I select the Linux partition the screen goes black, (while the machine stays on).   I tried selecting it under the Finder in OS 9, to no avail. Hmmm.  I seem to recall there being an option when installing Breezy that allowed me to go into the command line, but after finally getting fluxbox to run just the way I want it, I am rather fearful of going where I have not been before on a production machine..

---

### Post by engla on 2006-03-27
Hm, then it looks like something more about yaboot was reset.. I really don't know that much about it. :/
You can try to start with the install disc in rescue mode or use the LiveCD. You should be able to get a chrooted shell (A shell with a "normal point-of-view", with your normal / on / even though you boot from a cd). I don't know what to do from there, but you could try the same command I suggested above.

---

### Post by deteringb on 2006-03-27
Right on, well I can always rebuild my install as you suggested with a rescue CD.  Thanks for your advice,  Blaine

---

### Post by deteringb on 2006-03-27
Aha!  I actually had to look up my partition table and see where Linux resided.  For some reason OS 9 makes 9 partitions so I had to go into Open Firmware and **boot hd:10,yaboot** and I have my machine back..whew.  I would hate to have to do any unecessary thinking this am..  ;)

---

### Post by wizzer on 2006-06-25
[QUOTE=engla]Is it a very old mac [oldworld, the old grey boxes] or newer than that?

If it's newer then it should be easy: Either go into change startup disk and see if you can use select a different one there, or run the Apple boot loader at startup:

Press and **hold the Alt key** directly after the computer starts, you should get a screen with a button per partition and it should even display a penguin icon on the one with ubuntu on. 
Select it and go on with the boot, ubuntu should start.
When you are in ubuntu again, run **sudo ybin** in a terminal to reinstall yaboot.[/QUOTE]
Thank you so much :-)   I also lost my yaboot and this worked like a charm!
:-)

---

