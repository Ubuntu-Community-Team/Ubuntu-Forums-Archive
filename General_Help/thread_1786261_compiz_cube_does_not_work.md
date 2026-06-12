---
title: "compiz cube does not work"
date: 2011-06-19
forum: General Help
---

### Post by Mr Nemo on 2011-06-19
I just bought a new HP pavillion dv6t. I can't seem to get compiz cube to work with it. I've exhausted google looking for a solution and have come up with nothing that has had any effect. If anyone has any ideas I would appreciate it. I'm using the ubuntu classic desktop.

---

### Post by Slovak on 2011-06-19
I could not get it to work on 11.04 either, so I went back to 10.04LTS

---

### Post by Mr Nemo on 2011-06-20
hmmm... that's disappointing. I guess ill just bump this once....

---

### Post by wildmanne39 on 2011-06-20
> **Mr Nemo said:**
> I just bought a new HP pavillion dv6t. I can't seem to get compiz cube to work with it. I've exhausted google looking for a solution and have come up with nothing that has had any effect. If anyone has any ideas I would appreciate it. I'm using the ubuntu classic desktop.Hi, To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.

---

### Post by Mr Nemo on 2011-06-20
Thanks for the link, I'm trying it now. As a quick update I've noticed that anything that I change in compiz has no effect at all....


EDIT: Followed the tutorial step by step, still no luck with the cube or any compiz functions

---

### Post by haqking on 2011-06-20
alot has to do with your graphics card and drivers.

I know there are alot of issues with Nvidia in Natty with desktop appearance and 3d graphics, plenty of threads about it.

I had natty installed since release but it couldnt get my cube to work and there was a lot of other issues too so i went back to my 10.10 build and everything working fine again.

good luck

---

### Post by wildmanne39 on 2011-06-21
> **Mr Nemo said:**
> Thanks for the link, I'm trying it now. As a quick update I've noticed that anything that I change in compiz has no effect at all....


EDIT: Followed the tutorial step by step, still no luck with the cube or any compiz functions
Hi, run this command in a terminal
```
lspci | grep VGA
```also this command.
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Mr Nemo on 2011-06-21
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6740

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


```

there you go.

---

### Post by wildmanne39 on 2011-06-21
> **Mr Nemo said:**
> ```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6740

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


```

there you go.
Hi, that looks good I still need the information from the first command in my last post.

---

### Post by wildmanne39 on 2011-06-21
Hi, make sure if you need restricted drivers that you installed them from additional drivers. You will need to install ccsm to and all plugins including fusion to configure the cube.

---

