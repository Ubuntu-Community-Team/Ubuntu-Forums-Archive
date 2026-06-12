---
title: "Screwed up royally please help!"
date: 2009-09-22
forum: General Help
---

### Post by bmfc187 on 2009-09-22
okay, ive been using ubuntu for maybe about 6 or 7 months, and i was looking into themes for ubuntu and it got me to reading about things like GTK+ and Compizfusion. i wanted a piece, so after figuring out what i needed to do, i set to it.  I was trying to get GTK+ to configure, but kept getting dependency errors. usually if i can apt-get install something, it works great, but i tried to get what i needed that way and it didnt work, so i tried downloading the packages from wherever and installing them manually.  i figured i would just be fine to put them all inside the GTK+ main directory, so i did, and it seemed to be working for a moment.  the packages it says it requires are :
ATK         
GLib         
Pango
Cairo

i downloaded those and extracted to the GTK directory (actually i got Cairo thru apt-get, so its good to go), and began setting them up.  then those started throwing dependency erros, too, and so i thought maybe i did it wrong by putting them where i did. but i didnt know where else theyre supposed to go, really, so i used synaptic to try to find and install them.  when synaptic finished doing its thing, i rebooted, and when it came back up, everywhere where there was supposed to be text, it was just rectangles!!! i dont know what i did wrong i didnt get any errors from synaptic, but i cant do anything!  please help!

-BMFC

---

### Post by bmfc187 on 2009-09-23
okay somebody please help me i was gonna try to format my ext3 partition and start with a fresh install, but i couldnt get my livecds to work...i have livecds for Gparted and ubuntu and both used to work fine but they quit working, so i burned a new Gparted cd and tried to boot it up but it just sits at a black screen forever...if i eject the cd grub starts right up, but i cant get the cd to work...i dropped to grub console and tried to "boot E:' to boot the cd and it told me "Kernel must be loaded first"  ive never got this any other time ive used these...so my windows vista partition still works but my ubuntu patition is royally F'ed.  and i dont know how to fix this other than wipe and start over.  Im still waiting for the new ubuntu LiveCD to download, i threw out both the old ones cuz they didnt work...can somebody help me get the Gparted cd working?!?!

---

### Post by c0mput3r_n3rD on 2009-09-23
Try doing a, sudo apt-get upgrade 
and running a file system check in recovery mode.

If you can't see anything and remove those files from the GTK directory then you're probably going to have to reinstall.

---

### Post by bmfc187 on 2009-09-23
> **c0mput3r_n3rD said:**
> Try doing a, sudo apt-get upgrade 
and running a file system check in recovery mode.

If you can't see anything and remove those files from the GTK directory then you're probably going to have to reinstall.

Umm....this answer doesnt really help, considering that i just said everything you did, right beofre you did.  i have already run clean, fsck, and anything else i could think that might have fixed the problem, but nothing did.  Yes, i need to reinstall.  however, when i try to run wubi in windows, it tells me that it has detected a previous installation of ubuntu and it must be removed before itll do anything...so i try to use the gparted livecd and it doesnt boot like its supposed to...so if anyone could help me out with that, WITHOUT repeating everything ive said back to me, id appreciate it...when i startup my machine with the Gparted livecd in the drive, it just hangs at a black screen with a flashing"_" at the top left corner.  if i eject the cd grub starts up, and if i press "c" to go to console, it works fine, then i type "boot E:" to boot the cd, and it tells me "kernel must be loaded first".  so, thank you, captain obvious, now if someone could tell me something i DONT know, ive been sweating bullets for about 12 hours now...
IM A BIT NEW TO THIS, BUT IM NOT DUMB, OR STUPID.  just stuck...thanks...

my question right now is, "How do i get the gparted LiveCD to start up so i can reformat my partition?"

-BMFC

---

### Post by bmfc187 on 2009-09-25
ok i figured it out...i think my DVD drive is screwed.  I made a ubuntu flash drive, formatted my ext3 partition, and reinstalled ubuntu just fine.  Funny thing is everytime i tried to burn or use a live cd, it wouldnt do anything, so i tried to burn a liveCD from my g/f's comp, and then tried to run wubi on it, and it ran just fine, so i thought maybe it was the DVD drive...ihardly ever use it so it couldve been screwed for a while now, id never have known.  Anyways, i lost alot of data, but both my Systems are running fine again.  If anybody cares.  

-BMFC

---

### Post by pcjunkie on 2009-09-25
Get an air compressor or compressed can of dry air and blast the dvd drive. Use the rest on your CPU. (hold the fan or it will break)

---

