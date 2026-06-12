---
title: "How to re-install nvidia drivers (8.10) ?"
date: 2010-05-31
forum: General Help
---

### Post by Bob Unitt on 2010-05-31
I have a desktop installation of Ubuntu 8.10 which has somehow lost parts of it's nvidia drivers. Is there some way, short of reinstalling Ubuntu, that I can completely remove the dregs of my nvidia installation, and then re-install it all afresh ?

---

### Post by Bob Unitt on 2010-06-02
> **Bob Unitt said:**
> I have a desktop installation of Ubuntu 8.10 which has somehow lost parts of it's nvidia drivers. Is there some way, short of reinstalling Ubuntu, that I can completely remove the dregs of my nvidia installation, and then re-install it all afresh ?

Bump, he said more in sorrow than anger....

---

### Post by cryptotheslow on 2010-06-02
How did you install them in the first place?

And what NVidia card / chipset do you have?

---

### Post by Bob Unitt on 2010-06-03
Hi, thanks for responding.

Nvidia card is GeForce 7800 GS with 2 MB. All was working OK until I used Grub to shrink the partition to make room for a dual-boot. It's a long time since I originally installed it, but I *think* it was a download and install from the nvidia website. The problem is that half my system seems to think it's installed, but the other half doesn't...

Symptoms :-

I have 2 screens duplicating the same image at 1024*768.

'Admin', 'Hardware Drivers' says "No proprietary drivers are in use in this system'.

'Preferences' 'Screen Resolution' says I have a single 1024*768 screen, where I actually have 2 screens with maximum of 1280*1024 - and the 'Detect Displays' button does nothing.

When I run 'Nvidia Xserver Settings' it says I'm not not using the nvidia X-server driver, and that I should run 'nvidia-xconfig' as root - but doing so makes no difference whatsoever.

Incidentally, it's not the hardware - the dual-boot I installed (ubuntu 10.04) runs the nvidia drivers and dual screens perfectly. I'd switch over to 10.04 completely, but I need access to the old 8.10 for now, for legacy purposes.

I'm hoping there's a config file somewhere I can set back to a default condition to get rid of the nvidia stuff so I can start again...

---

### Post by cryptotheslow on 2010-06-03
That config file you are looking for is /etc/X11/xorg.conf

It also contains information about other aspects of your X environment  (mouse, keyboard etc.). However, even with 8.10 most of that stuff  should be auto-detected - so you could try simply making a backup of  that file (in case you need to put it back) then remove it - restart and  with a fair wind behind you the system will come up using the open  driver rather than the NVidia proprietary one.

From a Terminal prompt:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
 sudo rm /etc/X11/xorg.conf
```

Then reboot. If it fails to come up correctly and you find you can't get  a working X session at this point, boot into recovery mode and from the  terminal:

```
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
```

...to put the original config file back in place and get back to where  you are now!


If it does come up OK then you can grab a copy of the latest NVidia  driver installer (it lists the 7800 GS as supported) from here - this is  the link to the 32bit version:

[http://www.nvidia.com/object/linux-display-ia32-195.36.24.html](http://www.nvidia.com/object/linux-display-ia32-195.36.24.html)


If you have a 64-bit OS install, use this route to find the right file:
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

Save it somewhere handy!

To install it, the desktop environment must be stopped, so save anything  you are working on and Ctrl+Alt+F1 to get a virtual tty and login. The  basic steps are - stop the desktop, install the driver, start the  desktop..... or from the command line:

```
sudo /etc/init.d/gdm stop
sudo sh  /pathtowhere/yousavedtheinstallerfile/NVIDIA-Linux-x86-195.36.24-pkg1.run
```

Run through the installer. It will probably find the remnants of your  previous driver install and offer to remove them.. say yes. Then towards  the end of the install it will ask whether to update your X  configuration... again say yes. Once it's done and you're back at the  command line:

```
sudo /etc/init.d/gdm start
```

You should now be back at a graphical desktop login screen, if nothing  much happens try Ctrl+Alt+F7 to switch to the tty the desktop runs on  manually.

---

### Post by Bob Unitt on 2010-06-03
Thank you very much for that. I'm too hot, tired and sweaty atm to concentrate that hard, But I'll try it first thing tomorrow and report back.

---

### Post by coskierken on 2010-06-03
The best, and easiest, way to install Nvidia drivers is at the command prompt at boot.  I keep a copy of the current driver in the root directory just in case something like this happens.  Then, I boot to a command prompt, make sure you are the admin logged in, and then "sh Nvidia_driver" (whatever the driver file is insert after sh.  It will see the install driver and as if you want to load (erase it) over it (forget exact wording).  Even though my equipment is different, it whould work.  Every so often, a certain upgrade occurs which screws up my Nvidia driver and I have to do this.  It takes all of 20 seconds or so.  I hope this helps.

---

### Post by cryptotheslow on 2010-06-03
+1 to coskiernen's post.

Always keep that driver install file somewhere handy. When manually installing like this you often have to reinstall it after a kernel update.

---

### Post by Bob Unitt on 2010-06-04
Not winning yet...

Got at far as :-
> **cryptotheslow said:**
> ```
sudo sh  /pathtowhere/yousavedtheinstallerfile/NVIDIA-Linux-x86-195.36.24-pkg1.run
```

After accepting the licence, it came back with :-

"ERROR: You do not appear to have the libc header files installed on your system. Please install your distribution's libc development package."

I searched synaptic for 'libc development package' but didn't find anything that looked appropriate. I'm also pretty sure I didn't have to load any such package last time I installed the nvidia drivers, or it would still be there.

I also tried to search for an alternative download on the nvidia site, but got a 'server too busy' error.

---

### Post by bodhi.zazen on 2010-06-04
8.10  is no longer supported so you may be out of luck.

It sounds as if you need to install some development packages , you can try installing build-essential and your kernel headers.

With that said, I suggest you either re-install or upgrade to a supported version of Ubuntu.

---

### Post by cryptotheslow on 2010-06-04
You can use this to ensure the installer knows what kernel you are using:

```
sudo sh /pathtowhere/yousavedtheinstallerfile/NVIDIA-Linux-x86-195.36.24-pkg1.run -k $(uname -r)
```

Might be useful to post back the contents of /var/log/nvidia-installer.log if that still fails.

---

### Post by Bob Unitt on 2010-06-04
> **bodhi.zazen said:**
> 
With that said, I suggest you either re-install or upgrade to a supported version of Ubuntu.
As I stated above, I've successfully installed a dual-boot with 10.04, and the nvidia drivers work perfectly on that boot (except Second Life frame-rates would appear to be lower than 8.04, I don't know why).

After a very bad experience attempting to upgrade to ubuntu 9, I decided that in future I would install any new versions as dual-boots, and transfer the applications and data I need to the new version item by item, deleting the old version only when I was completely happy that the new one was safe and stable - that way the old version would still be be available if I again encountered problems like my ubuntu 9 nightmare.

Unfortunately it didn't quite work out that way - although I still don't know just what clobbered my existing 8.04 nvidia, as I deliberately hadn't changed anything except the partition size.

---

