---
title: "Running Meego on Virtualbox?"
date: 2010-05-28
forum: General Help
---

### Post by Ric_NYC on 2010-05-28
Is that possible?

---

### Post by dino99 on 2010-05-28
maybe you'll be the first one to try  :P

[http://meego.com/downloads](http://meego.com/downloads)

---

### Post by louij on 2010-05-29
Guys, I an trying to install MeeGo with VirtualBox, but it's weird.
First I convert the .img to .vdi and use it to boot the new virtual machine. I could install MeeGo to a new disk partition, but I can't boot it after the installation. It's always in the splash page. Above is what happened in ubuntu 10.04 and VirtualBox 3.1.8 . While in Windows 7 and VirtualBox 3.2, I don't even see the grub page. So does anyone have suggestions?
Because this guy said he can use MeeGo with VirtualBox 3.2
[http://blogs.computerworld.com/16198/meego_the_new_netbook_linux_arrives](http://blogs.computerworld.com/16198/meego_the_new_netbook_linux_arrives)

---

### Post by Ric_NYC on 2010-05-29
> **louij said:**
> Guys, I an trying to install MeeGo with VirtualBox, but it's weird.
First I convert the .img to .vdi and use it to boot the new virtual machine. I could install MeeGo to a new disk partition, but I can't boot it after the installation. It's always in the splash page. Above is what happened in ubuntu 10.04 and VirtualBox 3.1.8 . While in Windows 7 and VirtualBox 3.2, I don't even see the grub page. So does anyone have suggestions?
Because this guy said he can use MeeGo with VirtualBox 3.2
[http://blogs.computerworld.com/16198/meego_the_new_netbook_linux_arrives](http://blogs.computerworld.com/16198/meego_the_new_netbook_linux_arrives)


I did the same... Renamed it to .vdi... Didn't work.

---

### Post by *stargazer* on 2010-05-29
try this

[http://shoaibmir.wordpress.com/2009/09/13/converting-img-files-to-virtual-box-vdi-format/](http://shoaibmir.wordpress.com/2009/09/13/converting-img-files-to-virtual-box-vdi-format/)

worked for me. I add this vdi to virtual machine and use as an installation media

edit:
it wont boot after installation :(

---

### Post by ciuci on 2010-05-31
i renamed the .img to .iso and tried to boot from it. it showed the splash screen but when i selected any of the options it just froze. i pressed tab in order to edit the boot options. i removed quiet mode in order to see if it would print any errors. it says that the kernel is not the one needed for my cpu. i have a core 2 duo cpu. any thoughts?

here's a screenshot in order for you guys to see the exact message:

[IMG]http://i50.tinypic.com/2v0ycko.jpg[/IMG]

---

### Post by tribester on 2010-06-01
You can get a bit further with VirtualBox by selecting Settings / System, Processor-tab and add checkbox to "Enable PAE/NX" (or something else, I have non-English version of VirtualBox).

After this the MeeGo boots beyond the pae kernel error but stops with a blank screen. Any ideas how to get forward..?

---

### Post by gertoft on 2010-06-01
Have a look at this page [http://wiki.meego.com/MeeGo_1.0_Netbook_VirtualBox](http://wiki.meego.com/MeeGo_1.0_Netbook_VirtualBox).

Seems to be a few issues yet! But at least your not the first! :)

//Niklas

---

### Post by neopeek on 2010-06-08
Hi guys, 

to those who have trouble with Virtualbox you can also use qemu to see MeeGo.


Meego 1.0 (kernel 2.6.33.3-11.1-netbook), image size: 787 MB (extracted: 2.5 GB) 
[http://www.neopeek.com/en/stories/meego/85-meego-10-gui-qemu]("http://www.neopeek.com/en/stories/meego/85-meego-10-gui-qemu")


MeeGo 0.9 (kernel 2.6.33.3-8.1-iv), image size: 282.3 MB (extracted: 1.2 GB) 

[http://www.neopeek.com/en/stories/meego/67-meego-with-ui]("http://www.neopeek.com/en/stories/meego/67-meego-with-ui")

---

### Post by pddel on 2010-07-09
Hi,

I never get Meego into working under VirtualBox, as everyone of you.  Instead, I tried Meego SDK and it works like a charm.  You can follow the link to see how to install it:

[http://wiki.meego.com/Getting_started_with_the_MeeGo_SDK_for_Linux](http://wiki.meego.com/Getting_started_with_the_MeeGo_SDK_for_Linux)

It gives you a good idea of what Meego can do for you.  I didn't get into it so far, but I can tell you I was unable to play MP3 with a plain installation, you have to install some other packages (didn't do it yet).  Once I'm done with it, I can share with you my experiences.

Their wiki and community sites are good sources of information on how to install different packages.

---

### Post by viveknanda on 2010-09-20
Here's a tutorial that explains how you can run MeeGo (with a working UI) on VirtualBox..
[http://www.99bits.com/2010/09/how-to-install-meego-on-virtualbox/](http://www.99bits.com/2010/09/how-to-install-meego-on-virtualbox/)

Enjoy!

Vivek
------------------------------
[http://www.99bits.com](http://www.99bits.com)
Twitter: [@99bitscom]("http://www.twitter.com/99bitscom")

---

### Post by CbrPad on 2010-09-21
I just downloaded the netbook edition (meego-netbook-ia32-1.0.0.20100524.1.img) and have been trying to get this to run today to no avail.  I found this info at the Meego wiki [http://wiki.meego.com/MeeGo_1.0_Netbook_VirtualBox](http://wiki.meego.com/MeeGo_1.0_Netbook_VirtualBox)  and unfortunately as they say all I can seem to get into is X11 with TWM and that's it.  

I haven't tried that tutorial but I don't particularly want to download an old 1.4gb version so I guess I'll give up on it for the moment.

---

### Post by viveknanda on 2010-10-01
The 1.4 Gig version was Meego 0.9. I now have the image of MeeGo 1.0. It's 900 something Mb. MeeGo 1.0 runs much much better than 0.9.

Thanks
Vivek
------------------------------
[http://www.99bits.com]("http://www.99bits.com/")
Twitter: [@99bitscom]("http://www.twitter.com/99bitscom")

---

