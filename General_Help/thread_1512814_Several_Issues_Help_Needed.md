---
title: "Several Issues Help Needed"
date: 2010-06-18
forum: General Help
---

### Post by jchase45 on 2010-06-18
Ok, I have the latest Ubuntu desktop I jsut downloaded from the Ubuntu site yesterday.

1. I'm not sure how to see all my hard ware 
2. My Xonar D2x Doesn't work 
3. Can true Crypt encrypt a system drive like it did in windows? I don't see the option now 
4. How do I take these Hard Drive Icons off my desktop?
5. I keep getting an error message saying that I don't have 3d Acceleration , install and enable it. But there is no option in the message to install it
6. I also can't find my opera speeddial.ini or notes.adr folder for the life of me

---

### Post by oldos2er on 2010-06-18
**lshw** run in a terminal will show you your hardware. It's output will probably be large so you may want to redirect to a text file ```
lshw >lshw.txt
gedit lshw.txt
```
Or if you prefer a GUI program, try **sysinfo**.

To remove the hard drive icons, hit Alt-F2, type in gconf-editor, click apps, nautilus, desktop, and uncheck the boxes.

For your video drivers, click menus System, Administration, Hardware Drivers to see if any are available.

---

### Post by jchase45 on 2010-06-18
Didn't there use to be a hard ware menu?

No my video drivers instaleld fine , they work ok.

My audio drivers are the problem. 

Also why I still keep getting those messages about 3D acceleration

---

### Post by oldos2er on 2010-06-18
> **jchase45 said:**
> Also why I still keep getting those messages about 3D acceleration

What exactly are you doing when you see this message?

---

### Post by jchase45 on 2010-06-18
All sorts of stuff , seems like any time I open a program , I first noticed it when opening up the Play On Linux program , but it happens opening almost any program windows

---

### Post by jchase45 on 2010-06-19
Bump

---

### Post by oldos2er on 2010-06-19
> **jchase45 said:**
> All sorts of stuff , seems like any time I open a program , I first noticed it when opening up the Play On Linux program , but it happens opening almost any program windows

Are you sure you installed the proprietary Nvidia drivers? It sounds like you're still running the 2d open-source driver you get when Ubuntu is first installed.

---

### Post by jchase45 on 2010-06-19
Heres the driver I need , 

[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/195.36.31/NVIDIA-Linux-x86-195.36.31-pkg1.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/195.36.31/NVIDIA-Linux-x86-195.36.31-pkg1.run&lang=us&type=GeForce)


but when I went to DL it , it was a .run file and it wouldn't open in Ubuntu

how can I run that driver in Ubuntu as a .run?

I tried to run it in a terminal but it gave me this error 

  ERROR: nvidia-installer must be run as root

---

### Post by oldos2er on 2010-06-19
It's easier to install the proprietary drivers from the repositories. See post #2.

---

### Post by jchase45 on 2010-06-19
Im already using the recommender driver in the system / admin / hard ware driver menu , i have no idea what proprietary driver means , both drivers say they are proprietary 

3D-accelerated proprietary graphics driver for NVIDIA cards.

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.

---

### Post by jchase45 on 2010-06-19
I uninstalled Play on Linux , but Wine is still in my application list, and it doesn't show up in my installed software list in Ubuntu 10.4 LTS desktop 

How can I get rid of it?

---

### Post by jchase45 on 2010-06-19
bump

---

### Post by oldos2er on 2010-06-19
Maybe this thread will help you: [http://georgia.ubuntuforums.org/showthread.php?p=9288289](http://georgia.ubuntuforums.org/showthread.php?p=9288289) 
I didn't realize the  Nvidia 8800gts was an older card.

---

### Post by jchase45 on 2010-06-20
No that doesn't realy help at all , I already tried to install Ubuntu with the nomodeset and it freezed every time.

I need to know how to install the .run driver I have . I got it to run in a terminal but then it crashed and said I need to close the X server first , which I have no idea what that is .

---

### Post by oldos2er on 2010-06-20
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by jchase45 on 2010-06-20
Ok that helped ;):popcorn:

Now I jsut need to figure out how the hell to install this sound driver 

[http://alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://alsa-project.org/main/index.php/Matrix:Vendor-Asus)

---

