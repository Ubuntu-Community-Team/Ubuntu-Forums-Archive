---
title: "Unity not resonding to CSSM"
date: 2012-03-22
forum: General Help
---

### Post by DracoJesi on 2012-03-22
No matter what plugins I enable or what plugin settings I change - nothing actually happens.

That goes for the Unity plugin as well - I can't even change the icon size on the unity bar - and it needs help.

---

### Post by PhantomTurtle on 2012-03-22
You might not have the proprietary graphics drivers installed or you might just have a unsupported graphics card or one that's too old.

---

### Post by DracoJesi on 2012-03-22
full-Unity works... hmm..

How do I turn of blacklisting?

The motherboard that I have now is newer than my old one and it was able to handle compiz.

Actually, I blame unity - XP

---

### Post by DracoJesi on 2012-03-22
The driver manager shows no available proprietary drivers.

---

### Post by wildmanne39 on 2012-03-22
Hi, what kind of video card do you have?

Did you uninstall old driver or are you using the same card with the new mother board? 

Did you install video card driver in additional drivers?

Please post the output of:
```
lspci | grep VGA
```
```
/usr/lib/nux/unity_support_test -p
```
Thanks

---

### Post by ajgreeny on 2012-03-22
An ability to run full compiz in an older ubuntu version does not mean you can also run unity 3D, as I found out with my ATI 9200SE card.

Full compiz desktop in 10.04 using cube, wobbly windows, zoom, etc etc, but only unity 2D is possible with that card.

---

### Post by DracoJesi on 2012-03-22
Q: Hi, what kind of video card do you have?
A: It's an onboard chip. Here is the motherboard info:

```
 *-core
       description: Motherboard
       product: MS-7312
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.0
     *-firmware

```

I also have an ATI All-In-Wonder 128 however I haven't gotten that card working yet- though I do have ATI drivers installed. 

I think the ATI card might be this as Unichrome sounds familiar and it list the display as unclaimed- and it's under PCI so.... But I don't see the onboard VGA- its there though as I'm currently using it... 

```
 *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:f0000000-f3ffffff memory:f4000000-f4ffffff memory:f5000000-f500ffff

```

Edit: according to the product Id thats the on-board.

Q. Did you uninstall old driver or are you using the same card with the new mother board?
A. New motherboard- but I'm actually trying to use the onboard graphics chipset as I'm not sure how to get the ATI card working - could there bw a possible conflict? 

Q. Did you install video card driver in additional drivers?
A. No additional drivers are lister for either the onboard GPU or the ATI card. I'm thinking that I do need a driver for it but that it's not listed under proprietary drivers. Synaptic shows the drivers for the ATI card as being installed but I can't even get the VGA output on that card working. 

Please post the output of:


```
jesi@TaoDraco:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
jesi@TaoDraco:~$ 

```

```

jesi@TaoDraco:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (K8M800) x86/MMX+/3DNow!+/SSE2
OpenGL version string:  1.2 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: no
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    no
GL version is 1.4+:       no

Unity 3D supported:       no
jesi@TaoDraco:~$ 

```

I don't know why it says Unity 3D unsupported - It logged into the the 3D session no problem and the transparency effect of the unity bar is working.

Thanks.

---

### Post by DracoJesi on 2012-03-22
> **ajgreeny said:**
> An ability to run full compiz in an older ubuntu version does not mean you can also run unity 3D, as I found out with my ATI 9200SE card.

Full compiz desktop in 10.04 using cube, wobbly windows, zoom, etc etc, but only unity 2D is possible with that card.

hmm, Unity has some polish to it but honestly I'd rather have GNOME2 - The dash and lenses are really the only plus IMO. 

The only way I was able to adjust on my laptop was using a lower gnome panel for my menus and all - I was able to live without the traditional window tabs though. 

KDE seems like a cross between fisher-price and Windows to me but I'm sure you can change the appearance. I've even considered moving over to Fedora but- they use KDE right? I'm not sure if theres a GNOME2 variant or not. 

Compiz isn't just pretty, it is functional and really helps with the limited theme support in Unity. Shell needs some work to- I'm not sure that I'm ready to transition but updates are nice as well. 

XFCE is an option I suppose... It seems that there is no GNOME2 package in the repository anymore. I'd even take the time to download the whole DE as a .deb if I could.

---

### Post by wildmanne39 on 2012-03-22
Hi, unity will default to unity 2d which looks exactly like unity to me except the 3d does not work.

It looks like unity is not supported with by your system.

---

### Post by DracoJesi on 2012-03-22
So any hope of installing GNOME2 on my system without having to go searching for a new distro or an old Ubuntu disc?

---

### Post by wildmanne39 on 2012-03-22
Hi, you can download it from ubuntu's website just do a search for 10.04.
Thanks

---

