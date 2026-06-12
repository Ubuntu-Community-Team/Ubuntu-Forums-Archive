---
title: "Screen resolution / Detection Problems Nvidia in 9.10"
date: 2009-11-15
forum: General Help
---

### Post by leehamer on 2009-11-15
Evening guys,

I am completely new to using Ubuntu, I have always been a windows user but as I have just built a PC from bits I had about I have decided to give Ubuntu a shot. I have got it installed and working pretty nicely, but then I remembered that I had a Nvidia 5600 fx card I could put in it. 

Now I am having issues with my LCD monitor being detected and getting a decent resolution, I have searched about and followed some guides but not really had any luck. Managed to cause an issue getting Ubuntu to even boot properly and having to resart,  I am using driver version 173. Any help would be greatly appreciated, I am at a loose end trying to get it running and really want to have Ubuntu running properly.

Cheers

---

### Post by arnab_das on 2009-11-15
you need to install the latest nvidia drivers from the site.

here's the way to do it:
[http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/](http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

---

### Post by leehamer on 2009-11-15
I have just followed the instructions and when I rebooted my monitor would not support the format, it is a 17 inch LCD screen. Would that make a difference?

I have had to boot from the cd to be able to get back in.

---

### Post by arnab_das on 2009-11-15
u got the proper drivers right? just checking if u got the 5FX series drivers or not. it should be this one:

[http://www.nvidia.com/object/linux_display_amd64_173.14.20.html](http://www.nvidia.com/object/linux_display_amd64_173.14.20.html)

assuming you have a 64 bit processor.

---

### Post by arnab_das on 2009-11-15
did u get a message saying that your installation was successful?

---

### Post by leehamer on 2009-11-15
I [http://www.nvidia.co.uk/object/linux_display_ia32_173.14.20_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_173.14.20_uk.html)

I have a 32 bit processor so downloaded that one. Then followed the guide in the link to the word, has got me a bit stumped now.

Is it possible to reverse the changes whilst using the live cd?

---

### Post by arnab_das on 2009-11-15
well what you did was the perfect procedure, and u installed the very latest drivers. did u get a message (in the dark screen/command line) saying that the installation was successful?

one more thing, is ur monitor in perfect shape? i have heard of people having problems with ubuntu because of their monitors.

---

### Post by arnab_das on 2009-11-15
i just reinstalled the drivers of my pc from the website. and it works perfectly. not sure why urs didnt work out.

okay for reverting do the following:

boot from live cd.

go to the terminal once it boots, and type

```
sudo fdisk -l                      
``` check the code of ur hard drive - sda1 or hda1 etc.

now type

```
grub-install  --root-directory=DIR /dev/ABCD 
```

where ABCD is your hard drive which you can find from the previous command (sda1 or hda1 etc. replace ABCD with that).

reboot.

---

### Post by leehamer on 2009-11-16
The first time I followed the instructions I got an installation complete message, however I could not get the instructions you supplied to remove the changes I made so I restarted and did a fresh install. I followed the instructions again and got a message saying it was complete, but I am back to the screen saying "mode not supported" on my monitor. 

I have just had a thought, my pc has on board graphics but I am using my graphics card in my AGP slot. I havent changed any settings in the BIOS to say use the graphics card over the on board, I will see if this helps when I leave work.

Yeah as far as I am aware my monitor is all ok, I have tried it on 2 LCD screens now to check if that was the issue.

---

### Post by arnab_das on 2009-11-16
> **leehamer said:**
> The first time I followed the instructions I got an installation complete message, however I could not get the instructions you supplied to remove the changes I made so I restarted and did a fresh install. I followed the instructions again and got a message saying it was complete, but I am back to the screen saying "mode not supported" on my monitor. 

I have just had a thought, my pc has on board graphics but I am using my graphics card in my AGP slot. I havent changed any settings in the BIOS to say use the graphics card over the on board, I will see if this helps when I leave work.

Yeah as far as I am aware my monitor is all ok, I have tried it on 2 LCD screens now to check if that was the issue.

dont get me wrong mate, but i think its ur monitor which is not supporting ur ubuntu installation. its happened before to people. were the 2 monitors from the same company? even i used to get "No Signal" message on my previous AOC monitor. :(

also, i just checked. your version of your default nvidia driver is the latest version, so the next time you install do it from System>Administration>Hardware Drivers and install/activate the recommended one, since its not causing any problems to ur monitor res that way.

---

### Post by leehamer on 2009-11-16
The 2 monitors are different brands, one is about 4/5 years old and the other I have been using is an LCD TV. I think I am going to set up as dual boot so I have a OS that I can use without issues and have Ubuntu as a second OS.

I might sweet talk the IT department at work and see if I can borrow a CRT monitor and see if that makes a difference... If it turns out to be my monitor I will just have to replace that!

Cheers for your help anyway mate it has been greatly appreciated :)

---

