---
title: "Getting Started"
date: 2011-06-28
forum: General Help
---

### Post by funguygordy on 2011-06-28
Hello all, 

I had used Ubuntu some in the past, and am getting back into it as my main OS.  I have just finished puting 10.04 on my dual partition ssd, (win7), updating with system update, and getting my wireless pci setup.  My current issues revolve around finding the drivers for my other hardware.  Under System>Preferences>Monitors I am still unable to detect my monitor, which is running at 800X600 currently.  I am also wondering if there is anything I need to do in order to take full advantage on my hardware.  The rig is: Sandy Bridge 2600k, Asus p8p67 Pro, and EVGA 560ti.  

Thanks!

---

### Post by wolfen69 on 2011-06-28
You need to go to *additional drivers* section and download the video driver.

---

### Post by FormatSeize on 2011-06-28
I can't detect my monitor, either, on 10.04, but it still works fine. As for taking full advantage of your hardware, you can install proprietary drivers. Go to System -> Administration -> Hardware (or it might be called something like additional drivers), and activate the ones that you have.
 
Then, if you need other drivers, like Nvidia for graphics, you can see [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") for how to install the drivers. Your sound should be working out of the box. Then, you can go to [Adobe.com]("http://Adobe.com") and install Flash Player, a free download. If you want to watch movies, you have to get libdvdread, which the installation process can be found [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"). 
 
That's about as far as I normally go, as I really only use my computer for those sorts of things, and my own projects. I don't have a camera attached to my computer, I don't take enough pictures to warrant storing them on a computer, and all of my artwork is done the old-fashioned way. But if you want to do things like that, and more, there are applications for those things, which are easily findable using the Software Center, which is already preloaded for you. 
 
Finally, if you want pizzazz, you can install Compiz, which can allow you to rotate your desktop like a cube, your windows can wobble when they move, and all sorts of other cool looking things. 
 
Beyond that, it's all customization based on what you do from day to day on your computer.

---

### Post by funguygordy on 2011-06-28
Sorry, but where would that be?  When I go to System>Administration>Hardware Drivers it scans and then informs me that my rt3562sta (network card) driver is proprietary, and gives me the option to deactivate or close.

---

### Post by e79 on 2011-06-28
> **wolfen69 said:**
> You need to go to *additional drivers* section and download the video driver.

+1

System --> Administration --> Additional drivers

If there is any drivers for your graphic card, install it then reboot your machine and to use the full potential of it, go to : Prefferences --> Appearance --> Effects tab

---

### Post by FormatSeize on 2011-06-28
> **funguygordy said:**
> Sorry, but where would that be? When I go to System>Administration>Hardware Drivers it scans and then informs me that my rt3562sta (network card) driver is proprietary, and gives me the option to deactivate or close.
That means that your network card is already activated. The other ones that you may need (depending on your hardware) need to be downloaded and installed.

---

### Post by funguygordy on 2011-06-28
Well, 

I used
```

sudo apt-get --purge remove xserver-xorg-video-nouveau

```

to remove the existing graphics driver, and then downloaded the "current" nvidia driver via the Synaptic Package Manager.  I rebooted, and the driver is not functioning.  I also tried running:
```

sudo nvidia-xconfig

```
But it was unable to locate/run the x config.  Any thoughts?

---

### Post by funguygordy on 2011-06-28
I have tried multiple guides now, with nothing working.  I always end up having to boot in "low graphics mode" because the driver does not work.  It will say "activated" in hardware drivers, but for some reason does not work.

---

