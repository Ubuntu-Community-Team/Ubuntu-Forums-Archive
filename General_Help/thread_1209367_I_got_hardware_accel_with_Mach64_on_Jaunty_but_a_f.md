---
title: "I got hardware accel with Mach64 on Jaunty but a few Q's..."
date: 2009-07-10
forum: General Help
---

### Post by b@sh_n3rd on 2009-07-10
Hi, I've posted a couple of threads before on how to get hardware acceleration on Jaunty for my ATI 3D Rage Pro video adapter. I found a rather old [thread]("http://ubuntuforums.org/showthread.php?p=3264969#post3264969") on the forum itself, answering my Q though, for a much older version of Ubuntu. It seems to have worked on Jaunty without any problem but I have two questions if anyone would be knowledgeable and kind enough to answer them :D

The fix states me to manually build DRI from source which I did. What I did was actually build the **xf86-video-ati-6.12.2** package into Jaunty. Previously, **# glxinfo | grep render** gave me,
```
[COLOR=Green]direct rendering: yes
OpenGL renderer string: Software rasterizer[/COLOR]
```Now I get,
```
[COLOR=Red]do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.[/COLOR]
[COLOR=Green]direct rendering: yes
OpenGL renderer string: Mesa DRI Mach64 [Rage Pro] 20051019 AGP 2x x86/MMX[/COLOR]
```I'm rather puzzled by what I've marked in red. Any info on that would be much appreciated. My second Q is, after I built the package, "configure:" printed that I should also install the "**mach64**" or, to be more precise, the "**xf86-video-mach64**" (6.8.1=latest) package, for cards based on Mach64. I got that package to double check on it and I thought I'll ask a Q on that here, coz it seems to be somewhat similar to the "**xorg-xserver-mach64**" package I see in synaptic. Simply put, should I or shouldn't I compile *this* package too? Thanks to anyone for any feedback on this topic.

#b@sh_n3rd#

---

### Post by b@sh_n3rd on 2009-07-10
Well, it so happened that I thought, "might as well build the mach64 driver" and I did. So the next time I booted my PC (5mins ago to be exact), I couldn't boot into Ubuntu. Strangely I had a feeling that would happen... Anyways, I was prepared for this and how? I built the driver into the linux-2.6.30 kernel, leaving Ubuntu's default untouched. Well now I know the answer to my second Q :D. What's left is the first. What does it mean by that red line? It would be great if I'd get the answer now coz I have to rebuild the driver if I am and that'd enable me to make any corrections in the way I build it if need be. Thanks for any replies on this...

---

### Post by b@sh_n3rd on 2009-07-11
So.......anyone know about this?? I mean, this error? Thanks...

---

