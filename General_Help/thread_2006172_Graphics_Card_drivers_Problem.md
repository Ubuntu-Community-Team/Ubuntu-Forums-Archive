---
title: "Graphics Card drivers Problem"
date: 2012-06-18
forum: General Help
---

### Post by RocketPenguin on 2012-06-18
[solved] I have a Compaq 6910p HP laptop, and i am having problems with my graphics card drivers. Infact, i have no drivers for it, and that is the problem. My laptop has a ATI Radion x2300 graphics card, and Ubuntu does not recognize it. When i type lspci, it shows "VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M64-S [Mobility Radeon X2300]" so it knows its there, but no drivers for it. Anyone know of a compatable drivers that would work with it?

---

### Post by Kakers on 2012-06-18
AMD driver support isn't really the best on Linux, but you could try the fglrx driver (ATI Catalyst Driver 12.4):

```
sudo apt-get install fglrx
```

---

### Post by RocketPenguin on 2012-06-18
Hmmm.... it says i already have it....

---

### Post by Kakers on 2012-06-19
I don't really know too much about the ATI side of things on Ubuntu, but you may be fine. Mine shows up as:

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8600M GS] (rev a1)

I does show the model but don't know if it makes a huge difference when using lspci. Do you have a ATI Catalyst control panel you can open up? What does it say in there?

---

### Post by electrojustin on 2012-06-19
First off, do ensure you have no drivers with 
```
lsmod | grep fglrx
```

If that comes up with fglrx and some numbers, you have the driver.

If that comes up nothing, then download and install the drivers from the AMD support site-I've found the fglrx in the repos doesn't work well. [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

That will give you a .run file. Now just cd to your downloads directory and run
```
sudo ./amd-driver-installer-12-4-x86.x86_64.run --force
```
It may not be the same file name, but I'll bet just tab completing after amd-driver will work. Go through the menus, and be sure to choose "Install" instead of "Generate Distribution Specific Driver Packages" when prompted.

After it's done, reboot and all should be good. If it isn't, you may need to run
```
sudo aticonfig --initial
```
then reboot again.

---

### Post by Mark Phelps on 2012-06-19
IF you're seeing a desktop, not a command line, you DO already have the radeon drivers installed.  The old "X"-series have not been supported in restricted drivers for years now.  

IF you download drivers from AMD and force their installation, you're likely to hose up your display -- and will have a lot of work to do, only to remove them and replace them with the same drivers you already have now.

---

### Post by RocketPenguin on 2012-06-19
> **Kakers said:**
> I don't really know too much about the ATI side of things on Ubuntu, but you may be fine. Mine shows up as:

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8600M GS] (rev a1)

I does show the model but don't know if it makes a huge difference when using lspci. Do you have a ATI Catalyst control panel you can open up? What does it say in there?
Thats the problem. I don't have a control panel for it, which is what i want.

---

### Post by QIII on 2012-06-19
ATI driver support is just fine, despite the persistent false rumors.  ATI and Canonical are virtually in bed together.  At every Ubuntu release, Phoronix complains that Canonical gets the new ATI driver before anyone else does.

The problem is that ATI, like NVIDIA, has stopped supporting drivers for many of their older cards - yours being one of them.

The fglrx driver will not work with that card and ATI's legacy driver will not work with X server versions after 2008.  Thus, you cannot have the Catalyst Control Center.

I will reiterate what Mark Phelps said a little more strongly:  do NOT install the fglrx driver unless you want to learn a lot more about fixing your system than you care to.

The open source Radeon driver is installed by default and that is what your card will run on.  It has gotten very good recently, but is limited in functionality at the moment.  To get it as far as they have, the developers are to be commended.

---

### Post by RocketPenguin on 2012-06-19
> **electrojustin said:**
> First off, do ensure you have no drivers with 
```
lsmod | grep fglrx
```If that comes up with fglrx and some numbers, you have the driver.

If that comes up nothing, then download and install the drivers from the AMD support site-I've found the fglrx in the repos doesn't work well. [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

That will give you a .run file. Now just cd to your downloads directory and run
```
sudo ./amd-driver-installer-12-4-x86.x86_64.run --force
```It may not be the same file name, but I'll bet just tab completing after amd-driver will work. Go through the menus, and be sure to choose "Install" instead of "Generate Distribution Specific Driver Packages" when prompted.

After it's done, reboot and all should be good. If it isn't, you may need to run
```
sudo aticonfig --initial
```then reboot again.
Nothing comes up when i do type the first command in, and the website does not have mine.. or i am doing something wrong.

---

### Post by QIII on 2012-06-19
Again:  you do not have the fglrx driver so lsmod will show nothing -  the kernel module does not exist.

The current fglrx driver will not work with your card and attempting to install it presents a very high probability that you will bork your system.

Continue to use the open source Radeon driver.

---

### Post by RocketPenguin on 2012-06-19
> **QIII said:**
> Again:  you do not have the fglrx driver so lsmod will show nothing -  the kernel module does not exist.

The current fglrx driver will not work with your card without the very high probability that you will Bork your system.

Continue to use the open source Radeon driver.
ok then fine... But how do i check to make sure i havn't borked the opensource drivers?

---

### Post by QIII on 2012-06-19
Do you see your desktop?

---

### Post by RocketPenguin on 2012-06-19
yes...
but, if you computer doesn't have a graphics card, do you see the desktop?

---

### Post by QIII on 2012-06-19
Even an integrated GPU will run on the open source drivers, albeit the "nomodeset" kernel option is sometimes required, as with a dedicated card.  If your mobo has no integrated graphics, of course, a dedicated card is required.

You do have a driver.  The open source drivers included by default are very good.

When you first install Ubuntu and you see your desktop for the first time, you are using an open source driver.

---

