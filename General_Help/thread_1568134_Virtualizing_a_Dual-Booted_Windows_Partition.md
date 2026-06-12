---
title: "Virtualizing a Dual-Booted Windows Partition"
date: 2010-09-04
forum: General Help
---

### Post by Wangsta on 2010-09-04
So this has been discussed a bit on other place throughout the internet, but after two days of searching, I haven't found any guide.

I have a dual-booted Windows 7 and Ubuntu. Primarily, I plan to use the Ubuntu partition for most of the time. However, on a shared partition, much of my music is in the iTunes format. I'd like to run iTunes and play this music from Ubuntu. I've tried using Wine, which completely didn't work. 

How can I "tunnel" over to the Windows partition and run a virtualization of the iTunes program?  Most sites and people online have expressed doubt of running an ACTUAL windows partition as a virtualization.



On a side note, with Wine, does one have to run an iTunes 7.x version? Guides online have said that any version will do, and some have said otherwise.

---

### Post by Revolutionary101 on 2010-09-04
Being able to use an actual Windows partition as a virtual machine, is not possible (at least to my knowledge). The reason why this doesn't work is because some of the settings like RAM allocation, USB mounting, and CPU allocation in the virtual machine can interfere with the Windows install. That is why you must have Virtual Box, VMware or whatever virtualization application, install your Guest OS for you.

As for the Wine and iTunes question, you can run whatever iTunes version you want. Although, you will find that some iTunes versions run better than others. Some can be usable, while others can be complete garbage.

---

### Post by Wangsta on 2010-09-04
Well, this probably isn't the place to ask, but whenever I tried playing a song in wine-run itunes, it would never actually PLAY anything. the play button would become a pause, but nothing would come out of the speakers and the song wouldn't progress.

happen to know a fix?

---

### Post by jeight on 2010-09-04
First of all make sure you have the latest version of wine. The previous versions had problems running itunes but I do believe the latest version works. Secondly you should consider using Rythmbox to play those music files. As long as you have the windows partition mounted you can point rythmbox to that file and have it import your music.

---

### Post by Wangsta on 2010-09-05
I guess I'll try doing another wine install. However, the music is sadly in the encrypted iTunes format, making it only available to iTunes players.
I currently use Rythmbox to manage all my NON-encrypted music files, which work great, but it can't play some of my favorite ones.

---

### Post by Revolutionary101 on 2010-09-06
Well you may be able to create a new Windows install using Virtual Box or VMware. You would be able to run iTunes on it for your songs. However, it would not be using your Windows partition, instead it would be considered its own install.

---

### Post by borth92 on 2010-09-06
i would suggest installng a new Windows on a virtual machine (mentioned above), but it will be easier on ram to just import the music to ubuntu and use a linux media player.

---

