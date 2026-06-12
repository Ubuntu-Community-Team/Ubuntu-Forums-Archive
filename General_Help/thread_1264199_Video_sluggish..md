---
title: "Video sluggish."
date: 2009-09-11
forum: General Help
---

### Post by mbuehl on 2009-09-11
Hello,

Pre-ubuntu my computer ran everything rather quickly. My machine isn't a beast by today's standards, but I have a geforce 9600GT (1gb dedicated ram), decent processor (AMD X2 5200+). 2 gigs of ram, I even keep it clean inside, too!

Now, back when I was using Windows this issue was usually due to bad graphics drivers (or no graphics drivers), and I have no idea how to check what driver I am using for my card, I also don't know how to remove a driver, or add one.

Can someone please help me figure out if a badly configured graphics card is what's making my computer so much more graphically slow than my old WindowsXP install?

Thanks!

---

### Post by misfitpierce on 2009-09-11
Ok lets go over the basics first... Can you hit System-Admin-Hardware Drivers... Is there a Nvidia driver listed under there that you can install or have installed?

---

### Post by mbuehl on 2009-09-11
When I enter that I get a window, looks like this:
[IMG]http://img24.imageshack.us/img24/4697/93710824.jpg[/IMG]

---

### Post by misfitpierce on 2009-09-11
I have ATI personally so lets see, anywhere in settings or app's do you have a Nvidia control center or control app or something named Nvidia settings or something along those lines? May be able to tweak the performance settings and so on. Also are you using compiz aka Desktop Effects?

---

### Post by mbuehl on 2009-09-11
> **misfitpierce said:**
> I have ATI personally so lets see, anywhere in settings or app's do you have a Nvidia control center or control app or something named Nvidia settings or something along those lines? May be able to tweak the performance settings and so on. Also are you using compiz aka Desktop Effects?

No, not using that. There is an X Server thing for nVidia, but if there are tweaks in here I have no idea what to do with them.

---

### Post by misfitpierce on 2009-09-11
sudo apt-get install nvidia-settings in the terminal if you do not have it... If it does not work and nothing working properly still and still sluggish i'd maybe recommend this...

[http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)

Get newest 9 series driver from there for 32 bit linux...

Use this guide to make it simple to install this driver and follow it piece by piece... But where it says sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run - Replace that with the new driver name you downloaded from link I sent you which is version 185 for 9 series...

Guide - [http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/) - Remember to replace driver name with yours from link I gave you.

Can try that if you wanna install manually for 9 series which I would think would have to make it work for sure.

Also the part about stopping the GDM may make it so you have to do this in terminal mode... So rename the install driver name to something simple like Nvidia.run and know where its at in your home folder so when you run command you can do something like this Terminal: sudo sh /home/YOURUSERNAME/Nvidia.run
YOURUSERNAME = login name

---

### Post by mbuehl on 2009-09-11
> **misfitpierce said:**
> sudo apt-get install nvidia-settings in the terminal if you do not have it... If it does not work and nothing working properly still and still sluggish i'd maybe recommend this...

[http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)

Get newest 9 series driver from there for 32 bit linux...

Use this guide to make it simple to install this driver and follow it piece by piece... But where it says sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run - Replace that with the new driver name you downloaded from link I sent you which is version 185 for 9 series...

Guide - [http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/) - Remember to replace driver name with yours from link I gave you.

Can try that if you wanna install manually for 9 series which I would think would have to make it work for sure.

Also the part about stopping the GDM may make it so you have to do this in terminal mode... So rename the install driver name to something simple like Nvidia.run and know where its at in your home folder so when you run command you can do something like this Terminal: sudo sh /home/YOURUSERNAME/Nvidia.run
YOURUSERNAME = login name

loads of stuff to try, thanks.

---

### Post by misfitpierce on 2009-09-11
Like I said try the nvidia settings first and somewhere in there, there should be a place to change from like high quality or whatever its on to performance... If nothing in there works then do the new driver from Nvidia part... read my notes below link though and do that on top of what it says in link... Renaming driver to simple name will make it easy when you shut down GDM which is graphics... will be done in terminal style mode so Nvidia.run instead of Nvidia874598345345Whatever.run  is alot easier... Let us know how it works out and goodluck.

---

### Post by mbuehl on 2009-09-11
when I do

sudo /etc/init.d/gdm stop

stuff gets all black, im at a full screen "console" (not sure if that's it. and it's entirely unresponsive. I can type, push enter, but nothing happens?

I had to reboot, lol

---

### Post by misfitpierce on 2009-09-11
Okay, when that pops up did you type in sudo sh /home/YOURUSERNAME/Nvidia.run assuming you renamed that new Nvidia driver you downloaded to Nvidia.run instead of default name? When you do that a semi-graphical thing should pop up in terminal mode for the Nvidia installer!
This is also assuming after you renamed it that it is in your home folder and that you replaced YOURUSERNAME with your login name.

---

### Post by misfitpierce on 2009-09-11
I got to get offline now, but what I posted should help, I am not sure if you did enter that like I said. Also the installer will ask to auto uninstall the driver you already got from Ubuntu which you want to do obviously... If any other problems another user i'm sure will help. Goodluck though buddy, Best of luck to you.

---

