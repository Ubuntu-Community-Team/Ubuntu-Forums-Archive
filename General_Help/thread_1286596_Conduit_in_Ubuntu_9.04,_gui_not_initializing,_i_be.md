---
title: "Conduit in Ubuntu 9.04, gui not initializing, i believe"
date: 2009-10-09
forum: General Help
---

### Post by Predatorian on 2009-10-09
Hello *buntu'ers,

i recently became curious about syncing files between my portable usb devices and my main tower. i've been reading about how to do rsync and grsync, but im still exerpimenting with how to set up the config file and commandline command. so i went with conduit cause it seemed to be an easier program for beginners. i installed it using apt-get, and once the program was finished installing, i went to the menu, and selected the program. i waited for about 30min before trying again, clicked the icon again, and nothing happened. i tried starting it from the commandline and i get a large output of data, and then it just stops. i sent it to the background, and then the forground, and still got nothing. is there somethign i missed, like, probley a gui for the conduit program, or is it just somethign about the repo version of it? thanks for the help guys/gals.

---

### Post by lasleym on 2009-10-26
I installed conduit 2 ways - once w/add-remove & once with synaptic package manager.  Both load the program fine for me.  I **however** cannot get the program to correctly sync with my jump drive.  

I add the sample "file" option through the "File->Examples->Synchronize between folders".  I then configure with a right click, making the tower folder the 'left' folder the jump drive the 'right' folder, assigned to a one-way sync.   The most progress I have is right now where's it's stalled at 10%.  

I even gparted the jump drive to try and erase everything and sort of start from scratch.  Again, the most progress I have is stated above, where previous attempts said "Synchronization OK" but nothing had actually changed.

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]http://pix.mickysgreenguide.com/conduit.png[/IMG]

---

### Post by Predatorian on 2009-10-27
i installed it on my laptops, and they run the i686 version of 9.04, and the GUI worked, but with the amd64 version the GUI doesnt want to pop up, the program says its working when i issue ps -e, but i cant bring it to the foreground or anything.

---

