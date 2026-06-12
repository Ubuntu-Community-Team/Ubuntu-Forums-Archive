---
title: "no directx? and graphics card isnt being picked up."
date: 2009-07-26
forum: General Help
---

### Post by Kd40 on 2009-07-26
so???
i just opened up chess and tried to run it in 3d mode got this
"You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support" 

i also went to system->preferences->appearance->Visual effects and tried "normal" and "extra", they both came up with the message "Desktop effects could not be enabled".

I know i have a good graphics card because i used it in my vista when it was installed, firstly i'd like to know which graphics card i have? (how do i find).

secondly im guessing visual effects is because of that and how do i get it working.

thirdly how do i install my graphics card?

please can you actually tell me here and not stick a link to some manual because all the wone i've seen i hav'nt understood at all.

---

### Post by sisco311 on 2009-07-26
First, try to install the driver for your card.

Go to System -> Administration -> Hardware Drivers and enable the driver.

If your card is not listed there, then open a terminal and post the output of the following command:
```
lspci | grep VGA
```

---

### Post by Kd40 on 2009-07-26
hardware and drivers didnt pick up anything, so i typed the comand and got this.

kd40@*****-******:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
kd40@*****-******:~$

edit: dubbed out name

---

### Post by jocko on 2009-07-26
> **Kd40 said:**
> hardware and drivers didnt pick up anything, so i typed the comand and got this.

kd40@*****-******:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
kd40@*****-******:~$

edit: dubbed out name
Install the packages "nvidia-glx-180" and "nvidia-180-modaliases", then check if the restricted driver manager (System -> Administration -> Hardware Drivers) picks up your card.

And: You'll never get DirectX. That's Microsoft's proprietary technology that they will probably never share...

---

### Post by Kd40 on 2009-07-26
k thanks, how do i install? sorry im complete newb at ubunto at the moment.
in windows you'd google then download and install, here you use the terminal right?

---

### Post by jocko on 2009-07-26
> **Kd40 said:**
> k thanks, how do i install? sorry im complete newb at ubunto at the moment.
in windows you'd google then download and install, here you use the terminal right?
Either you open up synaptic (System-->Administration-->Synaptic package manager) and search for the packages, or you can copy and paste this into a terminal:
```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
```

---

### Post by Kd40 on 2009-07-26
i know these are really newby questions but how do i enter my PW >.<.

```
kd40@tango-laptop:~$ sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
[sudo] password for kd40: 
```it wont let me type my password when i get to this point. i pressed enter and tried to type my password and within a second it said something like "password doesnt exist" before i finished typing.

---

### Post by jocko on 2009-07-26
> **Kd40 said:**
> i know these are really newby questions but how do i enter my PW >.<.

```
kd40@tango-laptop:~$ sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
[sudo] password for kd40: 
```it wont let me type my password when i get to this point. i pressed enter and tried to type my password and within a second it said something like "password doesnt exist" before i finished typing.
You will not see your password (or any other visual confirmation that you are typing anything, not even ***** or xxxxx) when you type it. Just type your password, then press enter. Don't press enter before you type it...

---

### Post by Kd40 on 2009-07-26
thanks done that

```
kd40@tango-laptop:~$ sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-180
kd40@tango-laptop:~$ 
```

---

### Post by jocko on 2009-07-26
> **Kd40 said:**
> thanks done that

```
kd40@tango-laptop:~$ sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Couldn't find package nvidia-glx-180[/COLOR]
kd40@tango-laptop:~$ 
```
Hmmm... Maybe you need to enable the restricted repo.
Open up synaptic, then go to Settings-->Repositories, and in the first tab make sure the restricted repo is activated. That's the one that says something like "proprietary hardware drivers (restricted)". Once that's done hit the refresh button in synaptic and then try searchin[COLOR=Black]g for [/COLOR][COLOR=Black]"nvidia-glx-180". If you find it, either install it from synaptic or close synaptic and repeat the command in the terminal.[/COLOR]

---

### Post by sisco311 on 2009-07-26
If you are using Hardy, then you need the nvidia-glx-new package:

```

sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite
```

---

### Post by Kd40 on 2009-07-26
whats hardy?

i think i downloaded nvidiax successfully just then im not sure, also i was doing a bit of poking around and i got this message:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by sisco311 on 2009-07-26
> **Kd40 said:**
> whats hardy?

Hardy is the codename of Ubuntu 8.04 (Hardy Heron).

> **Kd40 said:**
> 
i think i downloaded nvidiax successfully just then im not sure, also i was doing a bit of poking around and i got this message:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Anyway, you have installed the driver, now you have to run the second command from my previous post, then log out and log back in.

---

### Post by Kd40 on 2009-07-26
kd40@tango-laptop:~$ sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite
[sudo] password for kd40: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Option "AllowGLXWithComposite" "True" added to Screen "Screen0".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

kd40@tango-laptop:~$

---

### Post by jocko on 2009-07-26
> **Kd40 said:**
> kd40@tango-laptop:~$ sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite
[sudo] password for kd40: 

Using X configuration file: "/etc/X11/xorg.conf".

[COLOR=Red]VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.[/COLOR]

Option "AllowGLXWithComposite" "True" added to Screen "Screen0".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

kd40@tango-laptop:~$
Have you tried logging out and back in? Is it working?

---

### Post by Kd40 on 2009-07-26
just rebooted,

kd40@tango-laptop:~$ sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite
[sudo] password for kd40: 

Using X configuration file: "/etc/X11/xorg.conf".
Option "AllowGLXWithComposite" "True" added to Screen "Screen0".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

kd40@tango-laptop:~$ 


i think its not working right?

---

### Post by j.bell730 on 2009-07-26
No, it's working. If you still don't get 3D, restart X (just log out and log back in), then try it.

---

### Post by jocko on 2009-07-26
> **Kd40 said:**
> just rebooted,

kd40@tango-laptop:~$ sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite
[sudo] password for kd40: 

Using X configuration file: "/etc/X11/xorg.conf".
Option "AllowGLXWithComposite" "True" added to Screen "Screen0".
Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

kd40@tango-laptop:~$ 


i think its not working right?
Run this in a terminal:```
glxinfo
```If the correct driver is in use you should see something like this in the beginning of the output:```
jocko@jocko-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**[COLOR=Blue]direct rendering: Yes[/COLOR]**
**server glx vendor string: [COLOR=Blue]NVIDIA Corporation[/COLOR]**
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float
**client glx vendor string: [COLOR=Blue]NVIDIA Corporation[/COLOR]**
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_ARB_create_context, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
**OpenGL vendor string: [COLOR=Blue]NVIDIA Corporation[/COLOR]**
OpenGL renderer string: GeForce Go 7600/PCI/SSE2
**[COLOR=Blue]OpenGL version string: 2.1.2 NVIDIA 185.18.14[/COLOR]**
```

---

### Post by Kd40 on 2009-07-26
its working now :) thanks guys. your awesome.

---

