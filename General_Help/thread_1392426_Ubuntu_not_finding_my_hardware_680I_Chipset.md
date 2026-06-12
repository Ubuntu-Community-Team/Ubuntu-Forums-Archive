---
title: "Ubuntu not finding my hardware 680I Chipset"
date: 2010-01-28
forum: General Help
---

### Post by Toxicmoon on 2010-01-28
Hello all,
   
  I’m a new Linux user. I installed Ubuntu on my laptop. Loving it for the last two weeks. I Like it so much I want to duel boot my main desktop machine. However here lies the problem.
   
  First running it off the live CD, it stops mid boot and the screen starts flashing on the logon screen, doesn’t enter xwindows at all.  When installing it from the CD the same thing happened.   So what I did is changed the graphic option before the install via the splash screen menu when you boot the CD. This allowed me to load Ubuntu on my computer. However none of my hardware works unlike my laptop where everything works.  
   
  From research it appears the chipset is the problem. However the only information I can find on it is tons of threads asking the same question I am “How do you get it to work?”. Found a couple other threads similar to my problem talking about using kill commands but no clear directions on how to do just that with my specific setup.  Being completely new the information I found was useless as it was presented with implied knowledge I don’t have yet. 
   
  Kind of surprised Google is littered with complaints about this chipset not working since 2006 but no solutions I can find yet. However the new version of Ubuntu does not include these drivers or a fix? 
   
  Would appreciate any help trying to get this to work. Keep in mind I’m pretty new so you might need to break it down for me. I’d really like to put this on my desktop to make the switch. 
   
  Here’s the Hardware I’m working with. 
   
  Mother Board: Asus- P5N32-E  
  BIOS: Phoenix 
  CPU: Intel 3.0 Core 2 duo 
  Chipset: Nforce 680I 
  Video: Nvidia Geforce 8800 GTS
  Network: Nvidia nforce network controller (there’s two built on the mobo)
  Sound: Sound Blaster Xtreme Gamer 
   
  I recently just formatted my machine, so I only have Windows on it. I can reinstall Ubuntu the way I did before, or if there’s something I can do differently or include on the Ubuntu CD to make everything work for my next install that would be awesome. 



Thanks! 

-Tox

---

### Post by Toxicmoon on 2010-01-28
):p

---

### Post by Toxicmoon on 2010-01-28
Update:

Installed Ubuntu 9.10 using the safe graphic mode. 

Was able to get my network cards working by using the following commands in terminal 
sudo rmmod forcedeth
sudo modproce forcedeth msi=0 msix=0 


Problem now is getting the video card to work (Nvidia 8800gts) 

I tried using Envy, this loaded the drivers but limited me to 640 x 480 display.  

I removed Envy and downloaded and installed the .run driver file from Nvidia website.  
Same problem stuck in 640 X 480.   

I've invested over 5 hours so far on JUST the video card and I haven't made any progress.  Any suggestions besides waiting a couple more years for Ubuntu to include support?  Or is there a Distro someone could recommend that has popular video card drivers already installed? 

Thanks

---

### Post by Toxicmoon on 2010-01-28
I have about 10 hours totally invested in trying to install Ubuntu on my desktop and this is what I learned. 
   
  Linux is pretty far from “ready” to go main stream. Perhaps if your one of the lucky ones where you pop the disk in and everything just works you can experience the operating system.  But unlike commercially supported software your not going to find any easy fix i.e (pop in a CD or download a driver and have it just install).  
   
  From beginning to end my experience. 
   
  Inserted disk and attempted to install.  Didn’t even get to any of the menu’s just stopped at a logon text prompt flashing endlessly without allowing me to type anything.  
   
  After a lot of research 
   
  Booted from CD and selected safe Graphics mode.  Was able to install this time. After installation was complete to my dismay everything didn’t work, by everything I mean the following devices.  Network card, sound card, video card . 
   
  Step one I wanted to get the network working so I can download what I needed. After a lot of researching and crashing the thing I found some commands I listed in the thread above that allowed me to use the internet.  Yay! 
   
  I updated Ubuntu with the software update option then continued on to try to get the display to work. 
   
  I’ve exhausted many options trying to get the video card to work. 
   
  Tried Envy, Stuck on 640 x 480.  Many suggestions are too dated and not compatible. I tried all three card options in the hardware manager, no change. Edited the xconf file and manually added monitor and card resolutions.  Nothing. 
   
  Uninstalled Envy did everything manually, even tried doing it all from shell many times. No change. 
   
  So I invested over 5 hours in just trying to get the video card to work.  I was unsuccessful. Needing a break I decided to move to try to get my sound card to work so I can feel like I accomplished something so I’d stick with it. With little research I found that my card has no driver for Linux, other version of my cards do but the particular one I have it doesn’t exist yet as of a Nov 09 post and the solution is to “wait and hope”. After I read that I said, I’m done! 
   
  In the mean time I was checking my thread hourly hoping that someone could provide some useful information or instructions on how to solve these issues and didn’t receive a thing.  
   
  Looking at my time investment and having an OS that’s completely useless to me with zero support, it’s clear that Ubuntu has a loonnnnnnnnnnngggg way to go. 
   
  In the mean time if there is a Linux package out there the includes support for my hardware I’d really like to give it a try.  But I’m officially done with Ubuntu, you couldn’t pay me to continue with it at this point.

---

