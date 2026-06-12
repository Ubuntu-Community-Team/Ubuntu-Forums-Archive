---
title: "how to go back to 32-bit"
date: 2010-12-07
forum: General Help
---

### Post by listvon9 on 2010-12-07
I am considering going back to 32-bit linux due to this issue.
[http://ubuntuforums.org/showthread.php?t=1626418&highlight=monitor+flicker](http://ubuntuforums.org/showthread.php?t=1626418&highlight=monitor+flicker)

Why do I think that might be the answer, well nothing else seems to work and I want to use my computer even though 64-bit use is what I bought it for. Also a work colleague of mine got some hardware working simply by doing the same.

So the question is, is there a way to go to 32 bit without doing a install from a scratch? I think I am clutching at straws here, I shall have to bite the bullet and do an install from scratch.

---

### Post by ContagiousIdea on 2010-12-07
As far as I know there is NO method to go back to 32-bit w/o a re-image. Well I say that... but I really mean without spending many many hours replacing every component with a 32bit version which would be so incredibly tedious you would never attempt it.

---

### Post by oldos2er on 2010-12-07
> **listvon9 said:**
> I am considering going back to 32-bit linux due to this issue.
[http://ubuntuforums.org/showthread.php?t=1626418&highlight=monitor+flicker](http://ubuntuforums.org/showthread.php?t=1626418&highlight=monitor+flicker)


If you have an Nvidia video card, try the drivers here (if you haven't already): [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by Slim Odds on 2010-12-07
Using the 32 bit version is no guarantee that it will work any better. Just so you know, many of us use the 64 bit version with Nvidia cards without issue.

Perhaps you could give more information about your system and setup. Like hardware, etc. 

And, yes, the only way is to reinstall!

---

### Post by listvon9 on 2010-12-07
Thank you guys for your quick reply. I will try some of the links I have been sent and hopefully can report success.

As far as hardware is concerned, I have and nvidia (GeForce 7050 PV / nForce 630a) video card, an AMD athlon 7500 dual core and 4GB RAM. Would you need any more harware info? 

So far I have tried all kinds of versions of nvidia driver, the default installation, the "latest" download via synaptic package manager and even the latest 64 bit driver from the GeForce website. 
(though after that last install, I have stopped finding nvidia driver under System->Admin->"Additional Drivers".

Thanks.

---

### Post by efflandt on 2010-12-07
What video card/chip do "you" have, and what did you try for drivers other than the default.  What is the output of **lspci | grep VGA**, or the section of **sudo lspci -v** related to your video?

You should not have to install binary drivers from scratch.  If you want something newer than nvidia-current for a newer nvidia card, x-swat usually has the most recent drivers (currently 260.19.26 for Lucid or Maverick).  If you want those, and you have not mucked about manually installing downloaded drivers, you should be able to:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
```Then go to System > Administration > Additinal Drivers (or Hardware Drivers in Lucid), "remove" nvidia, reboot, "activate" nvidia from Additional Drivers, reboot.

---

### Post by coffeecat on 2010-12-07
> **listvon9 said:**
> So far I have tried all kinds of versions of nvidia driver, the default installation, the "latest" download via synaptic package manager and even the latest 64 bit driver from the GeForce website.

You've tried various drivers but have you considered that the problem might be a hardware one either with the video card or with the monitor? You need to exclude all the variables.

Can you try the monitor on another system? It might be an idea to try it with both Ubuntu and Windows on another computer if you have access to such. Do you have access to another monitor? Can you borrow one? Try that with your present setup. If you can do all this you might narrow down where the flickering is coming from.

---

### Post by listvon9 on 2010-12-07
Thanks all for reply. I guess I have my homework set for the next couple of evenings. 

Coffee Cat, than you for proposing the hardware check.  Before I moved, I was using another monitor on the same linux box. I had no problems. The current monitor works flawlessly as dual monitor on my XP running MSI wind.

---

### Post by listvon9 on 2010-12-07
Since some of you helpful guys asked...

 lspci | grep VGA
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)


sudo lspci -v
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    Subsystem: Elitegroup Computer Systems Device 2609
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-

There is of course reams more, but I don't want to clutter this board unless necessary. 

Incidently I do see some outputs like this :

Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]....

---

### Post by argedion on 2010-12-07
When my dad got a new computer he had the same problem with Windows 7 we tried installing and reinstalling new video card drivers and spent a couple of hours on the phone with the techs we did all this work for a 10 dollar cable that was faulty so the moral of the story is to CHECK THE CABLE

---

### Post by samborambo on 2010-12-07
I suggest you continue investigating hardware problems with the graphics chipset / card.

To rule out OS corruption, boot another OS from live CD or USB stick etc, using either the default SVGA driver or the nouveau driver.

If you still have flickering issues, it could be grounding / RFI issues. If it's an add-in card, pull it out, wipe the edge contacts (take anti-static precautions) and try again.

Sam.

---

### Post by listvon9 on 2010-12-07
The flickering is clearly linked to activity. If I click the mouse (anywhere) the screen flickers. Open a new terminls/webpage, creen flickers. Download something, there you go. 

So I do not believe it is related to any cable/ connection issues.

---

