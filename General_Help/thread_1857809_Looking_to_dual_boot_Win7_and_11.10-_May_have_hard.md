---
title: "Looking to dual boot Win7 and 11.10- May have hardware problems"
date: 2011-10-11
forum: General Help
---

### Post by thelamppost103 on 2011-10-11
Hello Ubuntu community!  I have recently stopped liking Windows as much as I used to and after looking at the developments of Ubuntu, I think I'm ready to make the switch.  I am, of course, going to keep Windows just for safety, but I would like to start primarily using Ubuntu.  I have researched a few parts of my laptop, however, and I am worried my graphics card, wireless card, and webcam (not a necessary feature, I know, but would be nice) may not work.
I will provide a basic link to my laptop specs (not sure if this includes all necessary hardware specs) [http://reviews.cnet.com/laptops/asus-n61jq-a1-core/4507-3121_7-33953721.html](http://reviews.cnet.com/laptops/asus-n61jq-a1-core/4507-3121_7-33953721.html)

My graphics card is as listed, an ATI Mobility Radeon HD 5730, the wireless card is an Atheros AR9285 Wireless Network Adapter, and the webcam is listed under Device Manager as "ASUS USB2.0 UVC 2M WebCam" 

Can anyone reassure me that these things will/will not work?  I appreciate the help and look forward to joining the Ubuntu community.

---

### Post by drofart on 2011-10-11
> **thelamppost103 said:**
> Hello Ubuntu community!  I have recently stopped liking Windows as much as I used to and after looking at the developments of Ubuntu, I think I'm ready to make the switch.  I am, of course, going to keep Windows just for safety, but I would like to start primarily using Ubuntu.  I have researched a few parts of my laptop, however, and I am worried my graphics card, wireless card, and webcam (not a necessary feature, I know, but would be nice) may not work.
I will provide a basic link to my laptop specs (not sure if this includes all necessary hardware specs) [http://reviews.cnet.com/laptops/asus-n61jq-a1-core/4507-3121_7-33953721.html](http://reviews.cnet.com/laptops/asus-n61jq-a1-core/4507-3121_7-33953721.html)

My graphics card is as listed, an ATI Mobility Radeon HD 5730, the wireless card is an Atheros AR9285 Wireless Network Adapter, and the webcam is listed under Device Manager as "ASUS USB2.0 UVC 2M WebCam" 

Can anyone reassure me that these things will/will not work?  I appreciate the help and look forward to joining the Ubuntu community.
Try running live cd if everything is ok you could install it along side of win.
 
Or you should re post this in asus supporrt forum below general help u can find it.

---

### Post by An Sanct on 2011-10-11
Welcome to the forums!

My guess would be, that the only thing, that you should worry about right now is the wireless card. Go check [this post]("http://ubuntuforums.org/showthread.php?t=1286503") and download the needed packages and info, to a USB stick, before installing Ubuntu if you have no chance for a wired connection afterwards.

PS. Keep in mind, that before you install Ubuntu it is recommended, that you re-partition you disk, so, that you have some empty space (the size of the Ubuntu install+RAM) after the Windows partition. It's not, that Ubuntu could not install or handle this situation, it's just, that Windows (specially Win7) sometimes cannot handle partition modifications, that *it* is unaware of (not done and approved within Windows)

---

### Post by An Sanct on 2011-10-11
> **drofart said:**
> Try running **live cd** if everything is ok you could install it along side of win.

I took a look at the specs ... and there is no optical drive, so make a Live USB (same thing as a Live CD [link here]("http://www.ubuntu.com/download/ubuntu/download") take a look at step II. for that.)

PS. Also :) be carefull about the version of Ubuntu, a new release is due somewhere in the next 48h or so :) ... so pick :) LTS 10.04, 10.10, 11.04, [11.10 the new release]

---

### Post by Mark Phelps on 2011-10-11
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair USB. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by thelamppost103 on 2011-10-11
thank you everyone for your replies and help! I will be looking into a different version or waiting until the 13th for 11.10.  In the mean time I guess I'll be setting everything up as you said

---

### Post by An Sanct on 2011-10-11
Well, the version I have has not been updated for days now, so one can presume, that it is the release candidate ...

I can hardly think of a reason why they would postpone some mayor merges or patches...

---

### Post by thelamppost103 on 2011-10-11
currently running 11.04!  so far it seems to be working pretty well, except I'm not sure if download speeds are slower or if I'll be able to play League of Legends/other windows games :/

---

### Post by An Sanct on 2011-10-11
Test your internet speed with some online tool - you can find it if you google "online speed test" or something similar.

About the games, try PlayOnLinux, the WINE "helper".

---

### Post by thelamppost103 on 2011-10-11
> **An Sanct said:**
> Test your internet speed with some online tool - you can find it if you google "online speed test" or something similar.

About the games, try PlayOnLinux, the WINE "helper".

Will do.  I think my campus internet is just sometimes rather slow.  Right now I'm only using Wubi.exe to launch ubuntu, so my hard drive is capped at 11gb.

As for WINE/PlayOnLinux, on WINE's website, there is no known way to play League of Legends just yet, which is fine if I set up a proper Windows partition for gaming.

---

