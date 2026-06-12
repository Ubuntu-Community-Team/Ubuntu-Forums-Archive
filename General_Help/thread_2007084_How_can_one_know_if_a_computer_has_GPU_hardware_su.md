---
title: "How can one know if a computer has GPU hardware support?"
date: 2012-06-20
forum: General Help
---

### Post by vasa1 on 2012-06-20
Is there some way of knowing?

---

### Post by sanderj on 2012-06-20
What do you mean?

- if it has a GPU?
- if it has accelerated GPU support?
- if it has / uses GPGPU?

---

### Post by black veils on 2012-06-20
they must either mean accelerated graphics, or dedicated graphics card (?)


1.  open **terminal**

2.  type ```
lspci
``` then press the **Enter** key

3.  The lspci command will return a lot of information.  Look for the line  that states "**VGA compatible controller**." Your graphics card should be  listed on the same line.  You may also view a line that states "Display  controller," which might list a secondary controller.

---

### Post by vasa1 on 2012-06-20
> **sanderj said:**
> What do you mean?

- if it has a GPU?
- if it has accelerated GPU support?
- if it has / uses GPGPU?

In this [post]("http://ubuntuforums.org/showpost.php?p=12036881&postcount=4"), there's the comment that "Compiz will eat CPU time if you don't have **GPU hardware support** for some of the compiz effects."

I take that to mean that computation that would be done by the GPU will have to be done by the CPU instead if **GPU hardware support** is lacking. That's why I want to know whether my PC has "**GPU hardware support**".

I had asked in that same thread but thought it maybe better to have a separate thread. Hence the question.

My knowledge of GPU / accelerated GPU support / GPGPU is zero.

I just don't want to stress my PC. If I'm told that "something" requires GPU / accelerated GPU support / GPGPU or the burden will be passed onto my CPU, I'd think twice about using that "something".

I hope I've made myself clear.

---

### Post by vasa1 on 2012-06-20
> **black veils said:**
> they must either mean accelerated graphics, or dedicated graphics card (?)


1.  open **terminal**

2.  type ```
lspci
``` then press the **Enter** key

3.  The lspci command will return a lot of information.  Look for the line  that states "**VGA compatible controller**." Your graphics card should be  listed on the same line.  You may also view a line that states "Display  controller," which might list a secondary controller.

Thanks!
I see this (first three lines):
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)...

```

---

### Post by vasa1 on 2012-06-20
A little more information:
I see this:
```
$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 8.0.2

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

Unity 3D supported:       yes
$ 

```
and I can run Unity 3D quite decently.

However, if I look in Help, Troubleshooting of my Firefox browser, I see the following ...

---

### Post by brainwash on 2012-06-20
> **vasa1 said:**
> However, if I look in Help, Troubleshooting of my Firefox browser, I see the following ...
Well, this is a specific issue. The  implementation of hardware acceleration based on OpenGL isn't very stable and may cause problems on Linux systems (bad drivers). Therefore it's disabled by default.

Try changing the configuration to forcefully enable hw acceleration in Firefox (about:config > layers.acceleration.force-enabled).

---

### Post by vasa1 on 2012-06-20
> **brainwash said:**
> Well, this is a specific issue. The  implementation of hardware acceleration based on OpenGL isn't very stable and may cause problems on Linux systems (bad drivers). Therefore it's disabled by default.

Try changing the configuration to forcefully enable hw acceleration in Firefox (about:config > layers.acceleration.force-enabled).

Thanks for answering! I want to understand this a bit more. I've given the relevant output from **lscpi** and **/usr/lib/nux/unity_support_test -p**. Leaving the Firefox stuff to the side, do the others indicate that I have this GPU stuff? What I really don't want is to have some eyecandy that will burden my CPU (if the GPU stuff isn't doing its share of the wotk).

---

### Post by qamelian on 2012-06-20
> **vasa1 said:**
> Thanks for answering! I want to understand this a bit more. I've given the relevant output from **lscpi** and **/usr/lib/nux/unity_support_test -p**. Leaving the Firefox stuff to the side, do the others indicate that I have this GPU stuff? What I really don't want is to have some eyecandy that will burden my CPU (if the GPU stuff isn't doing its share of the wotk).
 I think what you are seeing in Firefox may relate specifically to hardware-accelerated rendering in Firefox itself. This feature was added a while ago and, unless something has changed, it is turned on in Windows by default, but for technical reasons was not switched on in Linux.

---

### Post by vasa1 on 2012-06-20
Here's a little more from my **Chrome** browser via **chrome://gpu**:```
Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
Compositing: Software only, hardware acceleration unavailable
3D CSS: Unavailable. Hardware acceleration unavailable
CSS Animation: Software only, hardware acceleration unavailable
WebGL: Unavailable. Hardware acceleration unavailable
WebGL multisampling: Unavailable. Hardware acceleration unavailable
Problems Detected
Intel mesa drivers are crash-prone.: 76703
Accelerated 2d canvas is unstable in Linux at the moment.
```

---

### Post by QIII on 2012-06-20
If I may interject, since it was mentioned:  GPGPU is general purpose computing on graphics processing units.  Unless you do computationally intensive scientific computing using CUDA or OpenCL, it doesn't mean anything to you.  If you want to do something like Folding@Home or take part in another distributed computing project that do have GPGPU components, the clients will detect if you have a suitable card and driver.  (I don't think too many of them will have GPU clients for Intel since NVIDA and ATI are the big players.)

---

