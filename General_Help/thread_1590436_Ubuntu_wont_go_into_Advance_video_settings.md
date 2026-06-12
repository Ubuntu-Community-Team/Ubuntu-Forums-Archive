---
title: "Ubuntu wont go into Advance video settings"
date: 2010-10-07
forum: General Help
---

### Post by Skattles on 2010-10-07
Hello,

I have used Ubuntu before on my laptop and am just now putting it on my desktop.
when i install and update and install compiz and try putting my visual settings to Advanced it trys to detect drivers and then doesn't find them for my Graphics card.

I have a Nvidia GeForce 2 GTS/GeForce 2 Pro
This should run in Advanced settings or at least above low settings.
But i am having a problem going to any of the settings.
I have tryed finding drivers for my video card for Ubuntu but am
a little nubish when it comes to Ubuntu.
Can anyone help?

---

### Post by andrewthomas on 2010-10-07
Have you tried System > Administration > Additional Drivers (Hardware Drivers)?

---

### Post by Skattles on 2010-10-07
yes and it finds no drivers.
Its funny when i first installed ubuntu on this computer it had no graphics card
it was just the built in one on the motherboard and the advanced graphics were working fine at first.
and then all the sudden was having driver issues.
then once i got the new graphics card i had unistalled and reinstalled ubuntu with the new Graphics card and was still having the problem, also have been having problems finding drivers for the graphics card.

---

### Post by andrewthomas on 2010-10-07
post the output of 
 
```
 
glxinfo | grep OpenGL

```

---

### Post by Skattles on 2010-10-07
[FONT=monospace]owner@ubuntu:~$ glxinfo | grep OpenGL
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils

Im guessing i should install?
[/FONT]

---

### Post by andrewthomas on 2010-10-07
There really is no downside to installing mesa-utils.  Just install it then post the output of the glxinfo cmd.

---

### Post by Skattles on 2010-10-07
This is what i get from glxinfo | grep OpenGL

owner@ubuntu:~$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by andrewthomas on 2010-10-07
How about 
 
```
 
lspci | grep VGA

```

---

### Post by Skattles on 2010-10-07
owner@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)

lol are we getting anywere?

---

### Post by andrewthomas on 2010-10-07
```
sudo aptitude update && sudo aptitude install nvidia-current
```
 
 
That should get you the latest nvidia driver.

---

### Post by Skattles on 2010-10-07
ok so i did that it installed everything with what looked to be without any errors and i restarted computer and go to appearance and try to change it to either normal or advanced it trys to find drivers the screen goes in n out and then says desktop features could not be enabled.

i double checked to make sure driver was enabled and it is.

---

### Post by Skattles on 2010-10-07
I also notice that my GL screen savers are not working such as the matrix one it just shows up blank not sure what the problem is here.

---

### Post by andrewthomas on 2010-10-07
what does the 
 
```
 
glxinfo | grep OpenGL

```
 
say now.

---

### Post by Skattles on 2010-10-07
owner@ubuntu:~$ glxinfo | grep OpenGL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by andrewthomas on 2010-10-07
It doesn't look like the nvidia-current is working for you.  
 
I would 
 
```
 
sudo aptitude purge nvidia-current

```
 
To go back to the standard driver.  
 
Then maybe search about that particular card.

---

### Post by andrewthomas on 2010-10-07
I didn't realize that you had such an old card.  Accoding to this
 
[http://www.linuxquestions.org/questions/linux-newbie-8/video-help-822107/](http://www.linuxquestions.org/questions/linux-newbie-8/video-help-822107/)
 
 
I didn't realize that you had such an old card.  Accoding to this
 
 
the gf2 card is NOT supported anylonger -- there is NO xorg 1.8 support 
 
 
You might have to go to the nvidia site and download some legacy drivers.

---

### Post by Skattles on 2010-10-07
lol yeah its an older Mobo so i had to get an older Gcard if i found some legacy drivers you think that would help? with this card.

---

### Post by Skattles on 2010-10-07
The thing that gets me though is the face that it was working at one point the desktop features i could use cube and everything not sure why all the sudden it stoped it was working restarted the computer for some reason and that messed it up but i have tryed reinstalling ubuntu since then thinking it would fix the problem and didn't.

---

### Post by andrewthomas on 2010-10-07
[http://www.nvidia.com/object/linux-display-ia32-71.86.14-driver.html](http://www.nvidia.com/object/linux-display-ia32-71.86.14-driver.html)
 
for 32-bit
 
[http://www.nvidia.com/object/linux-display-amd64-71.86.14-driver.html](http://www.nvidia.com/object/linux-display-amd64-71.86.14-driver.html)
 
for 64-bit

---

### Post by Skattles on 2010-10-08
Thanks hopefully that will help.

---

### Post by Skattles on 2010-10-08
Like i said before im a nub when it comes to linux commands on here how do i install this drive whats the command i would use?

---

### Post by Skattles on 2010-10-08
I had tryed installing the driver and this came up while trying to install

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

---

### Post by andrewthomas on 2010-10-08
> **Skattles said:**
> I had tryed installing the driver and this came up while trying to install

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com/").

[http://uk.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/installdriver.html](http://uk.download.nvidia.com/XFree86/Linux-x86_64/256.53/README/installdriver.html)

Here is the instruction link.  You need to substitute either NVIDIA-Linux-x86_64-71.86.14-pkg2.run  or  NVIDIA-Linux-x86-71.86.14-pkg1.run to correspond to the driver that you picked (64 or 32-bit)

You were getting that error because you cannot be logged into gnome during the driver install.

---

