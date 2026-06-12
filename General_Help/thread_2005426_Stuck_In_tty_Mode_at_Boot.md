---
title: "Stuck In tty Mode at Boot"
date: 2012-06-17
forum: General Help
---

### Post by Eric Oblepias on 2012-06-17
Specs (64 bit):  
CPU: Intel Core i7 970 @3.20GHz x 12 
 Memory: 11.7 GiB  GPU: NVIDIA Geforce GTX 580 3GB  
Main Drive: 128 GB Solid State  
Data Drive: 2 TB HDD         

I recently installed Ubuntu 12.04 on my comp, I am using Ubuntu exclusivley so I allocated my entire SSD for the OS. After messing around a bit I decided to use GParted Partition Editor to format my data drive to NTFS, this was the last thing that I did before rebooting. 

Once I booted up my comp once again I was sent to the usual grub menu and splash screen, but instead of being sent to my desktop login screen I was presented with a black tty1 screen prompting me for a log in that way. I attempted to access desktop mode by entering (Ctrl+Alt+F7) where I recieved a wall of text stating something along the lines of "plymoth had disconnected and the cpu interrupts daemon".

If I enter my Live CD and choose the option of booting from the first hdd then I can load up the desktop fine but the moment I try to do this without the live CD then I encounter all of the same problems. Somebody please help me out!

---

### Post by Eric Oblepias on 2012-06-17
Bump

---

### Post by sffvba[e0rt on 2012-06-17
Please don't bump more than once every 24 hours.


404

---

### Post by gnusci on 2012-06-17
Hi,

First of all, your post is quite bad. Try to split it in parts. Secondly, try to give only relevant information. 

Did you machine run well using the LiveCD?

If you have a CUDA card you are not a noob

[http://developer.nvidia.com/category/zone/cuda-zone](http://developer.nvidia.com/category/zone/cuda-zone)

Try to install the CUDA dev drivers.

---

### Post by Eric Oblepias on 2012-06-17
I'm sorry for the bad post, when I first tried to format this post it would revert back to the chunk of text editing it this time worked.

Regarding the LiveCD.  I should clarify that I didn't even use the normal desktopCD to install Ubuntu because the installer was extremely slow and always froze at the welcome screen.  I had to use the alternate installer to install Ubuntu 12.04.  

When I use the LiveCD to boot Ubuntu from the first HDD it runs extremely well, yet when I don't use the LiveCD to boot I'm stuck in tty and when I attempt to "Ctrl+Alt+F7" I receive the "Plymouth has disconnected text".

Also, I have no idea what a CUDA card is...

---

### Post by gnusci on 2012-06-18
Dont waste your money or maybe check your the hardware first:

[http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-580/architecture](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-580/architecture)

I have a high performance NVidia CUDA and it runs perfect.

---

### Post by Eric Oblepias on 2012-06-18
I don't think that this is a hardware problem though because the system used to be able to boot fine.  I only began to have have trouble when I rebooted my comp after formatting my Data Drive.

---

