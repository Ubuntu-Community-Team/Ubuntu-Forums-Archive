---
title: "Ubuntu 12.04 (Unity) 2D only"
date: 2012-07-20
forum: General Help
---

### Post by SpaceMaster on 2012-07-20
Alright, just installed Ubuntu 12.04 (Precise Pangolin) 64-bit edition.  I'm having some graphics trouble, mainly that (a) I can only run in 2D mode, and (b) I'm experiencing lag (not previously experienced in 11.10) while playing videos, esp. through flash browser plugins.  I figured "alright, just a driver issue, I'll go install those propietary drivers."  Opened up the restricted drivers module in "System Settings" only to find no restricted drivers available.  Not sure what's preventing me from using my optimal graphics capabilities.  here's some background:

```
lspci | grep VGA
05:00.0 VGA compatible controller: NVIDIA Corporation NV38GL [Quadro FX 1300] (rev a2)

```
Desktop Model: Dell Precision 670
CPU: Intel Xeon CPU 3.00GHz 64-bit (2 dual core processors)
Monitors: Samsung SyncMaster710N, Sansung SyncMaster712N
DVI output from Graphics card, converted to VGA for monitors

If there's any other info you need, lemme know.

---

### Post by jmfal on 2012-07-20
Try running this in a terminal.
```
  /usr/lib/nux/unity_support_test -p  
```

---

### Post by Wirephire on 2012-07-20
First check if you already have any installed proprietary nvidia driver:
```
dpkg -s nvidia-current | grep Version
```If it says that the package is not installed, run:
```
sudo apt-get install nvidia-current
```Anyway, my suggestion is to use the latest driver from x-swat ppa. Forget the second command from above and run:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-current
```


*~wph*

---

### Post by SpaceMaster on 2012-07-20
> **jmfal said:**
> Try running this in a terminal.
```
  /usr/lib/nux/unity_support_test -p  
```
ran that, got this:
```

nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV35
OpenGL version string:  1.5 Mesa 8.0.2
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       yes
```

> **wirephire said:**
> First check if you already have any installed proprietary nvidia driver:
```
dpkg -s nvidia-current | grep Version
```If it says that the package is not installed, run:
```
sudo apt-get install nvidia-current
```Anyway, my suggestion is to use the latest driver from x-swat ppa. Forget the second command from above and run:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-current
```


*~wph*
okay, ran the first code, and as you predicted ,it said that package was not installed.  Ran apt-add-respository, update, upgrade, and install nvidia-current.  Now I'm rebooting, I'll edit this post with the outcome.
----
EDIT: rebooted, and Ubuntu 3D works smoothly, but not great. The hitch is my screens are now identical.  Going to "System Settings" then "Displays" reveals that it isn't detecting 2 screens, but instead believes I'm running on a single laptop display. 
EDIT AGAIN: silly me, I forgot to run
```
sudo nvidia-xconfig
gksudo nvidia-settings
```

---

### Post by Wirephire on 2012-07-20
Everything is ok now, right? If so, mark your thread as SOLVED :)


*~wph*

---

### Post by SpaceMaster on 2012-07-20
> **wirephire said:**
> Everything is ok now, right? If so, mark your thread as SOLVED :)


*~wph*

actually, no, it's not.

Upon opening, the Nvidia Settings GUI gives me the error "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
I did exactly as it said, which generated a xorg.conf, restarted, X, and even restarted the computer.  Still gives me the same error.  I went into "Additional Drivers", and it confirms I'm running "nvidia-current".

So currently I do have a graphical desktop, but do not have both monitors working.

---

### Post by SpaceMaster on 2012-07-20
Finally outstubborned this problem to a resolution.  I found some great information that links this to [Bug #982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485").  There, it was suggested to go the the Nvidia website and download the drivers ([http://www.nvidia.com/Download/Find.aspx?lang=en-us]("http://www.nvidia.com/Download/Find.aspx?lang=en-us"))Nvidia gives you many options, so you have to select the appropriate hardware and software configuration.  For me, I had to choose the product Quadro FX 1300, and Operating System is Linux 64-bit.  This downloads a file called
```
NVIDIA-Linux-x86_64-173.14.35-pkg*.run
```
where * is a version number dependant on your previous selection.  Now although this is a self-extracting file, it requires a)to be root, and b)that X is not currently running.  So you have to hit Ctrl-Alt-F# to reach a text-only console, and log in.  Then you have to stop X by typing:
```
sudo service lightdm stop
```
then go to the directory where you downloaded the installer for the drivers (in my case /home/username/Downloads), and run the program:
```
cd $HOME/Downloads
sudo sh NVIDIA-Linux-x86_64-173.14.35-pkg2.run
```
After rebooting, I had to fidget a bit with nvidia-settings, and finally got it worked out.

---

### Post by ncolson on 2013-02-08
I had a similar issue, and was able to fix it by resetting all CompizConfig settings to default while in 2D mode (under Preferences->Profile->Reset to defaults), and then logging out and back in as 3D mode, opening a terminal with keyboard shortcuts, and running "unity --reset".

I also disabled the Gnome compatibility plugin due to key binding conflicts with the Unity plugin, but I'm not sure if that was important.

---

