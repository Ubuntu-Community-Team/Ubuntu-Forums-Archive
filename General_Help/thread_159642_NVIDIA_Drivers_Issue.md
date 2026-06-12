---
title: "NVIDIA Drivers Issue"
date: 2006-04-13
forum: General Help
---

### Post by Mr_Welfare on 2006-04-13
Hi Everyone,

I'm very new to Ubuntu and very new to Linux. When I tried to install the latest NVDIA Driver acording to this thread: 

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) (method 2)

I ran into some problems. I followed the steps exactly and everyting seemed to work. The driver installer came up and everything worked. Then, like it says in the steps, the installer will ask if it can go and fnd a precompiled kernal on the NVIDIA ftp website. Since I haven't gotten my internet up and running yet, it couldn't connect. After pressing ok to the message saying the installer couldn't connect, I got a message saying that my CC version couldnt be verified. It later went on to say that if I didn't know what I was doing, I should abort the install. If I did, I should press no to continue. I dcided to try pressing no, and when I did, an error message came up saying that my the installer couldn't find my current gcc version. (gcc-3.4) When I tried to install gcc-3.4 (sudo apt-get install gc-3.4), it said that the package didn't exist ](*,)  I'm going to download gcc-3.4 later on today from the Ubuntu packages site. Is this what I should do? Or am I rnning into a problem with an easy fix? Any help would be great.

Thanks,

Mr_Welfare

---

### Post by dermotti on 2006-04-13
Why not just get the nvidia driver Ubuntu provides?

**sudo apt-get install nvidia-glx**

once its installed run

**sudo dpkg-reconfigure xserver-xorg**

select the nvidia driver.
Restart X

---

### Post by NoNo_231 on 2006-04-13
You have to follow the instructions **fully**. In method 2 say 
```
sudo apt-get install build-essential gcc gcc-3.4
```

Do not forget this part
```
cd &#8220;directory where you have the nvidia installer&#8221;
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```

What you are trying to do is to compile an nvidia-kernel which must be compiled by the same version of gcc, in this case 3.4.

Good luck!

---

### Post by Mr_Welfare on 2006-04-13
The only thing is that I'm running a 256mb NVIDIA 6200 (AGP). In order to prevent the brown screen after logon, I had to add in some code to
sudo nano /etc/X11/xorg.conf
to disable 3D accel. Will this default driver. posted by dermotti support my card and 3d accel? (I have the default driver "nv" installed right now.

---

### Post by Sutekh on 2006-04-13
I'm afraid not.  The xorg nv driver is an open source driver created with the limited specs released by NVIDIA.  If you want 3D acceleration you need to install NVIDIA's official binaries.

You need to follow method 2 again, making sure that you really do follow each step.  You need gcc-3.4 so that the NVIDIA installer can use that to compile its driver.  Like NoNo said the kernel was compiled with gcc-3.4, so the NVIDIA must be compiled with gcc-3.4.  Use the instructions in that post to get gcc-3.4 with apt-get (it should be available)

If you still can't use apt-get to install gcc-3.4, then download these packages (not just gcc-3.4)

[Ubuntu Packages - gcc-3.4](http://packages.ubuntu.com/breezy/devel/gcc-3.4)

[Ubuntu Packages - gcc-3.4-base](http://packages.ubuntu.com/breezy/devel/gcc-3.4-base)

[Ubuntu Packages - cpp-3.4](http://packages.ubuntu.com/breezy/interpreters/cpp-3.4)

Install them using ```
sudo dpkg -i <name of package>.deb
```

---

### Post by Mr_Welfare on 2006-04-13
Yes, I have followed the directions exactly, but still nothing seems to happen. I still get errors saying that the installer can't find gcc-3.4. I'm gong to download that package later on today, as when I try to install it,
sudo apt-get install gcc-3.4
I get a message saying that the package couldn't be found.

---

### Post by dermotti on 2006-04-13
nvidia-glx using the "nvidia" driver WILL support 3-d

---

### Post by Mr_Welfare on 2006-04-13
Ok, but to use the "nvidia" diver I'm going to have to install the package gcc-3.4 right?

---

### Post by Mr_Welfare on 2006-04-13
Ok. I have installed the gcc-3.4 package as Sutekh has said to do. I followed **all** the steps in method 2 of the NVIDIA Driver install HOWTO.

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) 

When I run the installer now, I get the following message.

gcc-version-check failed:

Could not compile gcc-version-check.c. Please be sure you have your distributers libc development package installed *(what is this?)* and that 'gcc-3.4' is a valid C ompiler name.

If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation, otherwise, select "Yes" to abort the installation, set the CC environment variable to the name of your compiler used to cmpile the kernel, and restart he installation.

Note: I think I have done this by entering the following code:

cd &#8220;directory where you have the nvidia installer&#8221;
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC

Anyways, if I press "Yes", it aborts the installaton. If I press "No", an error message appears. This error messag reads:

Error: Unable to find the development tool `cc` in your path; please make sure you have the package 'gcc' installed. If gcc is installed on your system, then please check that `cc` is in your path.

If I press "Ok" to that error message, it says that the installation failed, and aborts the install.

I'm completely stumped here. Any help would be appreciated.

Thanks

One last note: I have changed some settings in this directory.

sudo nano /etc/X11/xorg.conf

The following has been added in the section "device"

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;

EndSection

---

### Post by Sutekh on 2006-04-13
I think you'd be better off if you posted your problems in the NVIDIA HOWTO thread.  Tseliot (the author) is far more knoweldgable on the topic than I.

---

### Post by dermotti on 2006-04-14
My question is, why dont you just download "nvidia-glx" from synaptic? That IS the nvidia 3-d driver.

---

### Post by Sutekh on 2006-04-14
[QUOTE=dermotti]My question is, why dont you just download "nvidia-glx" from synaptic? That IS the nvidia 3-d driver.[/QUOTE]
I think my brain is skipping tracks today; you're absolutely right.  The nvidia-glx package (Method 1) contains the v7667 NVIDIA driver.  Method 2 is to get the latest drivers (or any other).
#-o

---

### Post by Mr_Welfare on 2006-04-14
I tried method 1, but nothing seemed to be working there like Sutekh said I should do, I posted my probelm on the NVIDIA HOWTO and got an answer there. Thanks to all who posted here for their help too.

Mr_Welfare

---

