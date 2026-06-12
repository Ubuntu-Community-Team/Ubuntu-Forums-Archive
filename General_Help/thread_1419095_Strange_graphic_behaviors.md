---
title: "Strange graphic behaviors"
date: 2010-03-01
forum: General Help
---

### Post by Fallonsnest on 2010-03-01
Hey,

I'm new to running ubuntu as main operating system.
Long time ago (about 10 years) i done some experimenting with FreeBSD and used it for about a month.

Recently i started using Ubuntu in VMWare on Windows and found myself spending more time using the virtual machine instead of windows.
So this weekend i have decided to format my pc and make dual boot system (Windows7/Ubuntu)

After few hours messing around with Ubuntu the first day, i allready had to reinstall everything cause i had screwed up the graphics :D

I installed the latest ATI drivers from the ATI website without any problems. After that i did the Ubuntu updates and could not startup no more with an error in fglrx. I been messing around with the driver install and finally was not able to fix the issue no more (seems the config file had changed location)

After re-install, i did the same thing and run into the same problem after the update. This time i went to the root console and just removed the config file, allowing me to re-install the ATI driver and have no further issues with it.

But now when i try certain things, there still seem to be something wrong with my graphics.

I have installed Cairo-Dock & Compiz. This is running fine most of the time, except when i just booted the OS. I'm also running aMSN which startup automaticly.
9/10 times, when i boot and close the aMSN window, the Cairo-dock widgets get a black background, my 4 desktops become 2 and my visual effects are turned off.
It seems something crashes on the background, but i have no clue where to find log files or anything to start searching for a solution.
I can fix the issue by right click the Compiz icon in the application bar on the bottom (Cairo-dock) and choose "Switch Window Manager"
Would be nice to know what this exactly does ... i see it fix my issue with visual effect, but it switches to what???

My second problem is running DX based games using Wine. I can run non DX windows app's without a problem, but not DX apps.

This is the message i get:
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  967
  Current serial number in output stream:  967

Im not sure where to search for fixes on these 2 issues or find log's that can help me fix it, so any help would be much appreciated ;)

---

### Post by lidex on 2010-03-01
It's probably Compiz crashing. ATI graphics are known to be not well supported in linux. You can try running cairo-dock with the cairo backend. Command:
```
cairo-dock -c
```

You should take a run-through of this page to optimize your graphics in any case:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I'm pretty sure DX doesn't work in wine.

---

### Post by namluc on 2010-03-01
the compiz icon switches between two window managers - compiz and metacity, compiz is the pretty one, metacity is the more stable one.

take amsn off auto start up for now
try and find that config file, it may be important, i don't know
there should be something called a driver backport, which stops your drivers from getting updated if you don't want them to be. 

other people will know more than me. 

i'd coax people on to skype or something so you don't have to rely on amsn, which is **** anyway

---

### Post by Fallonsnest on 2010-03-01
> **lidex said:**
> It's probably Compiz crashing. ATI graphics are known to be not well supported in linux. You can try running cairo-dock with the cairo backend. Command:
```
cairo-dock -c
```You should take a run-through of this page to optimize your graphics in any case:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I'm pretty sure DX doesn't work in wine.


eewww ... i tried follow the steps on that webpage
Result is pretty bad. After reboot it said it cannot find ati driver.
So again i removed the xorg.conf file, but it does not allow me to boot anymore.

instead it crash my entire system or even just turn off my pc. then i need to pull out the power cable for few sec before i can turn it on again.

looks like another re-install :cry:

---

### Post by Fallonsnest on 2010-03-01
Finally got my system up and running again

reinstalled the ATI drivers trough command line using the --buildpkg flag

Strange thing was, when i tried install the packages using dpkg, it said DKMS was not installed.

So after installing DKMS, i was able to install the ATI driver and boot my system again.
Now wine also working with DX apps ;)

 
Just a quick question about the Compiz. If i switch manager, how i know which one i'm in?

---

### Post by lidex on 2010-03-01
> **Fallonsnest said:**
> Finally got my system up and running again

reinstalled the ATI drivers trough command line using the --buildpkg flag

Strange thing was, when i tried install the packages using dpkg, it said DKMS was not installed.

So after installing DKMS, i was able to install the ATI driver and boot my system again.
Now wine also working with DX apps ;)

 
Just a quick question about the Compiz. If i switch manager, how i know which one i'm in?

Great. Glad to hear that. If not in compiz, you should be in metacity. Cairo-dock glx version won't run and you won't be able to enable desktop effects. In your system monitor (processes tab), you will see either compiz or metacity to confirm.

You really did well. ATI graphics can be a huge pain and some never get it figured out. Good to know I was wrong about DX/wine. It would be helpful to others with the same problem if you would explain what you did more concisely and marked the thread as "solved" using "thread tools" at top of page.

---

### Post by Fallonsnest on 2010-03-02
i have done some testing with the steps i performed to fix my issue on a clean install and it seems to work very well this way.

All these steps i done trough the terminal window.
After messing with the video drivers and could not startup Ubuntu no more, step 3-7 of the "Install ATI drivers" part fixed my issue.

To use this for fixing a crash that prevent u from start Ubuntu, in the boot loader (not sure if this is standard), choose the recovery mode and goto the root terminal.
If u start normally u should also be able to goto the terminal to fix all by command lines

[SIZE=3]**Install ATI drivers**[/SIZE]

**1) Download the driver**
[http://www.amd.com/uk/Pages/AMDHomePage.aspx](http://www.amd.com/uk/Pages/AMDHomePage.aspx)

On the top right, choose the driver u need. 
In my case
-> Graphics
-> Linux x86_64
-> Radeon
-> ATI Radeon HD 3xxx Series
After downloading the driver, change the file permission to make it executable

**2) Enable POSIX shared memory**
These steps can be found back on the ATI website

```
sudo gedit /etc/fstab
```Add the following line to the bottom of the file (new line)
```
tmpfs /dev/shm tmpfs defaults 0 0
```Mount the shared memory
```
sudo mount /dev/shm
```Check the shared memory
```
sudo mount | grep "shm" 
```This should show u something like this
> 
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /dev/shm type tmpfs (rw)
**3) Build the packages (not using GUI install)**
```
sudo ./ati-driver-installer-10-2-x86.x86_64.run --buildpkg Ubuntu/karmic
```This downloaded and installed some additional packages for me on a clean install.
Finally it generated the following files
> 
fglrx-amdcccle_8.702-0ubuntu1_amd64.deb
fglrx-installer_8.702-0ubuntu1_amd64.changes
fglrx-kernel-source_8.702-0ubuntu1_amd64.deb
fglrx-modaliases_8.702-0ubuntu1_amd64.deb
libamdxvba1_8.702-0ubuntu1_amd64.deb
xorg-driver-fglrx_8.702-0ubuntu1_amd64.deb
xorg-driver-fglrx-dev_8.702-0ubuntu1_amd64.deb
**4) Install the packages**
```
sudo dpkg -i *.deb
```Possible error:
> 
(error)
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
Solution:
```
sudo apt-get install dkms
```Possible error:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libamdxvba1: Depends: ia32-libs but it is not going to be installed
  xorg-driver-fglrx: Depends: lib32gcc1 but it is not going to be installed
                     Depends: libc6-i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Solution:
```
sudo apt-get -f install
```If the dkms package was missing, run this again
```
sudo dpkg -i *.deb
```**5) Create the xorg.conf file**
At this point there is no configuration file yet (ls /etc/X11)
so create one by this command
```
sudo aticonfig --initial -f
```**6) Reboot your system**
Scary moment, but this install procedure works fine for me and solve previous crashes/issues with other ATI install methods

**7) Check your drivers**
```
fglrxinfo
```> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3600 Series  
OpenGL version string: 3.2.9551 Compatibility Profile Context
Now the desktop appearance effects are enabled by default (on clean install) and everything run smooth and stable for me. I hope this will be same for others with same problem.
 [SIZE=3][B]
Install Wine
[/B][/SIZE]For wine i just followed the steps on the official Wine website
I allready had my NTFS drives mounted trough ntfs-config

Add an extra install source
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```Update the install sources
```
sudo apt-get update
```Install Wine
```
sudo apt-get install wine
```Config wine (creates the .wine folder in your home dir and seems to be required to have sound enabled)
Running this with sudo doesnt seem to work as it say it has no access to your home folder.
```
winecfg
```Goto the "Audio" tab page and click apply to save the sound settings



now ... try and run some windows game. I have no problem running most games that were allready installed on the driver from within Windows (only tried 3 so far)



I hope this can help some people facing the same problems :)

---

