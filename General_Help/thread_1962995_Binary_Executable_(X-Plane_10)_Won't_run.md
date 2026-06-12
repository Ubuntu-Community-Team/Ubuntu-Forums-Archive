---
title: "Binary Executable (X-Plane 10) Won't run"
date: 2012-04-21
forum: General Help
---

### Post by alex-paulsen on 2012-04-21
I purchased X-Plane 10 and installed it fine by dragging the installer from the 1st disc over to the desktop, everything was running fine and the simulator worked well until the next time I tried starting it, the loading screen showed up, waited a while then crashed.

I did some reading about and in the end updated the AMD Video drivers (Catalyst).

Afterwards, I still had no luck so I removed the install and decided to install it again, only this time, the install file does not want to open at all, no error messages, nothing, just a small amount of system lag and a blank screen.

Can anyone explain this? I'm running the simulator through Windows at the moment and I'm not so happy about it's video performance there, which is why I'd rather it installed in Ubuntu.

A fresh install could probably do my system well, but after all the months of adjustments and installs etc etc, I'm not so keen on starting over, besides, I shouldn't see why I would have to.

Thanks
Alex

(The system is 64 bit)

---

### Post by alex-paulsen on 2012-04-21
Ok, so I dragged the installer into Terminal and loveingly tapped enter, after sitting there confused for a moment it gave me this message

LINUX: I saw filesystem type "iso9660", but I wanted "udf"

---

### Post by dummy910 on 2012-05-17
the file you need on the following page-link is titled &quot;Linux DVD Installer&quot;, listed about 1/2 down on the page.  Download, rename the file from &quot;X-Plane DVD Installer Linux.zip&quot; to this to remove the spaced between names &quot;X-PlaneDVDInstallerLinux.zip&quot;, then unzip, make executable(if its not already once its unzipped) and of course run the file and follow the directions-screens...  Enjoy!  [http://wiki.x-plane.com/DVD_Installers](http://wiki.x-plane.com/DVD_Installers)

---

### Post by jwbrase on 2012-05-17
> **alex-paulsen said:**
> 
I did some reading about and in the end updated the AMD Video drivers (Catalyst).

<SNIP>

Can anyone explain this? I'm running the simulator through Windows at the moment and I'm not so happy about it's video performance there, which is why I'd rather it installed in Ubuntu.

What exact video card do you have? X-Plane has issues with certain AMD/ATI cards, and my (limited) experience with ATI cards is that they're pretty crappy for anything using OpenGL, whether on Linux or on Windows.

X-Plane 9 won't run under either operating system on our desktop, which has an ATI card, but it runs well under Linux on my laptop, which has an NVidia card. (My laptop came with Ubuntu pre-installed, so I've not tried X-Plane under Windows on it).

So you may very well not find that you get any better video performance under Ubuntu than Windows. It may just be a graphics card issue.

As to the installer, why are you dragging it to the desktop and then to the terminal? Why not just run it straight from the CD?

---

