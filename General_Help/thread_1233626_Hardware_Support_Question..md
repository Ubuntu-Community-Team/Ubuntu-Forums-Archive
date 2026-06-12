---
title: "Hardware Support Question."
date: 2009-08-06
forum: General Help
---

### Post by Salliestarr on 2009-08-06
I am interested in switching my PC over from Windows Vista to either Ubuntu or Kubuntu, I haven't decided which yet. I actually really like the way Kubuntu looks but Ubuntu seems to be the more popular choice. 

These are my current specs, does anyone see any foreseeable issue's I may run into with drivers, or support? My biggest concerns are my Video Card, and my WiFi Card. 

Thanks!

System   
--------------------------------------------------------------------------------
 
  Manufacturer Gateway 
  Model DX430 
  Total amount of system memory 3.25 GB RAM 
  System type 32-bit operating system 
  Number of processor cores 2 
  64-bit capable Yes 
 
Storage   
--------------------------------------------------------------------------------
 
  Total size of hard disk(s) 149 GB 
  Disk partition C: 97 GB Free (141 GB Total) 
  Disk partition D: 4 GB Free (8 GB Total) 
  Media drive E: CD/DVD 
 
Graphics   
--------------------------------------------------------------------------------
 
  Display adapter type Standard VGA Graphics Adapter 
  Total available graphics memory 1918 MB 
        Dedicated graphics memory 512 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1406 MB 
  Display adapter driver version 7.15.11.7779 
  Primary monitor resolution 1680x1050 
  DirectX version DirectX 8 or earlier 
 
Network   
--------------------------------------------------------------------------------
 
  Network Adapter Intel(R) 82562V 10/100 Network Connection 
  Network Adapter Microsoft Tun Miniport Adapter 
  Network Adapter Broadcom 802.11g Network Adapter

---

### Post by Vakman on 2009-08-06
> **Salliestarr said:**
> These are my current specs, does anyone see any foreseeable issue's I may run into with drivers, or support? My biggest concerns are my Video Card, and my WiFi Card. 

Thanks!
Graphics   
--------------------------------------------------------------------------------
 
  Display adapter type Standard VGA Graphics Adapter 
  Total available graphics memory 1918 MB 
        Dedicated graphics memory 512 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1406 MB 
  Display adapter driver version 7.15.11.7779 
  Primary monitor resolution 1680x1050 
  DirectX version DirectX 8 or earlier
It seems the driver is not installed for your graphics card at the moment? Am I missing something?
Also Broadcom is really "fun" to get working. No, I kid but not the best to have. Ndiswrapper helps a lot.

---

### Post by Salliestarr on 2009-08-06
> **Thisislaw said:**
> It seems the driver is not installed for your graphics card at the moment? Am I missing something?
Also Broadcom is really "fun" to get working. No, I kid but not the best to have. Ndiswrapper helps a lot.

yeah, I frogot to update my score before I posted. Sorry about that I'm running an Nvidia 9400

Graphics   
--------------------------------------------------------------------------------
 
  Display adapter type NVIDIA GeForce 9400 GT 
  Total available graphics memory 1918 MB 
        Dedicated graphics memory 512 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1406 MB 
  Display adapter driver version 7.15.11.7779 
  Primary monitor resolution 1680x1050 
  DirectX version DirectX 9.0 or better

---

### Post by HermanAB on 2009-08-06
You can install regular Gnome based Ubuntu and then add all the desktop systems you want and pick the one you want to use when you log in.  Some distributions like Mandriva is designed to do that by default and always present you with multiple options.  You can do the same with Ubuntu.

So, you don't have to choose, simply install Ubuntu, then add KDE, LXDE, IceWM, Windowmaker, Blackbox, whatever and then you log into the one you feel like using that day.  This is no big deal - Linux is about having choice - just go ahead!

---

### Post by Vakman on 2009-08-06
nVIDIA is great to have. Broadcom can be tricky if you do not use Ndiswrapper. All in all you should be fine.

---

### Post by Salliestarr on 2009-08-06
> **HermanAB said:**
> You can install regular Gnome based Ubuntu and then add all the desktop systems you want and pick the one you want to use when you log in.  Some distributions like Mandriva is designed to do that by default and always present you with multiple options.  You can do the same with Ubuntu.

So, you don't have to choose, simply install Ubuntu, then add KDE, LXDE, IceWM, Windowmaker, Blackbox, whatever and then you log into the one you feel like using that day.  This is no big deal - Linux is about having choice - just go ahead!

Awesome thanks. Sounds like a new adventure.

So all I really need to do is after installing Ubuntu, do a web search and download Ndiswrapper?

---

### Post by Vakman on 2009-08-06
> **Salliestarr said:**
> Awesome thanks. Sounds like a new adventure.

So all I really need to do is after installing Ubuntu, do a web search and download Ndiswrapper?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Has info about Ndiswrapper. You will also need the windows wireless driver to use Ndiswrapper. A lot if explained on that page though.

---

### Post by Salliestarr on 2009-08-06
Thanks. :D

---

