---
title: "Upgrade didn't change anything?"
date: 2011-07-10
forum: General Help
---

### Post by xDante on 2011-07-10
I just upgraded from Ubuntu 10.10 to 11.04, and it doesn't seem like there is much diffrent, shouldnt I have a desktop like this:

[IMG]http://upload.wikimedia.org/wikipedia/en/e/e9/Ubuntu_11.04_Alpha_Desktop.png[/IMG]

when mine looks like this (the same it was for 10.10):

[IMG]http://compixels.com/wp-content/uploads/2010/09/Ubuntu-10.10.png[/IMG]

Do I have to enable something? I went to System>About Ubuntu. And I am running 11.04 so I'm not sure why it is like it is.

Any help? 

Thanks.

---

### Post by wildmanne39 on 2011-07-10
Hi, run these commands in a terminal
```
/usr/lib/nux/unity_support_test -p
```
```
lspci | grep VGA
```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Also look in additional drivers and see if there is a driver for your video card, if so install it. You will need to be connected to the internet.

---

### Post by xDante on 2011-07-10
> **wildmanne39 said:**
> Hi, run these commands in a terminal
```
/usr/lib/nux/unity_support_test -p
```
```
lspci | grep VGA
```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Also look in additional drivers and see if there is a driver for your video card, if so install it. You will need to be connected to the internet.

```
OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv18 20091015 x86/MMX+/3DNow!+/SSE
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

```

```
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

```

```
CI (sysfs)  

```

Also, after the upgrade, the NVIDIA 3D driver was turned off, and I had to reinstall. But still no luck getting it to look like that

---

### Post by JRV on 2011-07-10
The "Unity supported:   no" is your answer.

Unity is not supported by your video card, so it defaults to classic desktop.

---

### Post by timgood on 2011-07-10
OpenGL vendor string:   Nouveau

You seem to be using the Nouveau driver rather than the Nvidia driver. If you go to System Settings/Hardware/Additional Drivers what is shown? If not the Nvidia driver, then you will need to install it. On reboot you should see the Unity desktop. This means that the driver is installed correctly.

---

