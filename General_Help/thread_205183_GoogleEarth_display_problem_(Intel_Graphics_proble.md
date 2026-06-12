---
title: "GoogleEarth display problem (Intel Graphics problem??)"
date: 2006-06-28
forum: General Help
---

### Post by mjpoetic on 2006-06-28
Hello,

Just a new ubuntu convert here!!  Enjoying everything about it so far!  Just got GoogleEarth installed on my laptop, but it doesn't display correctly (see [screenshot]("https://home.comcast.net/~mjpoetic/Pictures/Screenshot.png")).  I am just wondering if anyone else has had the same problem.  Here are my laptop specs:
[B]
Sony VAIO FS920
Intel Pentium M (Centrino) 1.73 GHz[/B]
[B]
Display:[/B]
TFT active matrix
Graphics Processor - Intel GMA 900
Chipset: Intel® 915GM
Max Resolution - 1280 x 800 pixels

SCREENSHOT LINK:
[https://home.comcast.net/~mjpoetic/Pictures/Screenshot.png](https://home.comcast.net/~mjpoetic/Pictures/Screenshot.png)

---

### Post by fdimmling on 2006-06-28
By resizing the window you get more of the picture you want but full of artefacts and partly drawn areas. Then you minimize the window and maximize it again to get it redrawn. This gives you perfect sky views. I have the same problems here on my Acer Travelmate which also uses the Intel 900 GMA.

Friedrich

---

### Post by az on 2006-06-28
File a bug report.  Wait!  It's not even free-libre open source software.  Never mind....

---

### Post by mjpoetic on 2006-06-28
Thanks for your replies.

[QUOTE=fdimmling]By resizing the window you get more of the picture you want but full of artefacts and partly drawn areas. Then you minimize the window and maximize it again to get it redrawn. This gives you perfect sky views. I have the same problems here on my Acer Travelmate which also uses the Intel 900 GMA.

Friedrich[/QUOTE]

Thanks for the info on resizing the window.  I never thought to do it for some reason, but it is definitely something I think that is being worked on in their beta of this project.  It works fine on my desktop which uses an NVIDIA 6600 PCIe card.

[QUOTE=azz]File a bug report.  Wait!  It's not even free-libre open source software.  Never mind....[/QUOTE]

I guess this is the best option for now (to never mind) until the next version is out with bug fixes.

---

### Post by Kubunteando on 2006-10-12
I cannot see the screenshot. But here it goes my experience:

- I am using the beta 4 for Linux and I also have the some problems with some rubish appearing on the screen. By resizing the window as mentioned it works fine.

- I was not able to make GoogleEarth work (it hung in the first splash window) when I was using the fglrx drivers. The ones from Ubuntu or the propietary from the ATI web page (my graphic card is an ATI mobility Radeon 9000). When uninstalling the xorg-driver-fglrx package, then GoogleEarth works fine. I have mentioned this to GoogleEarth support. We will see. 

- Without the fglrx drivers the Graphic Card HW acceleration does not work. It seems that only the ATI propietary driver supports 3D HW acceleration. So in this situation the performance is suboptimal. In my case I use the Desktop applications and everything works fine, including GoogleEarth. Probably if you play 3D games you will feel them slow...

---

