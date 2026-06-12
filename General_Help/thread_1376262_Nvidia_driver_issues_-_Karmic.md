---
title: "Nvidia driver issues - Karmic"
date: 2010-01-09
forum: General Help
---

### Post by sr_guy on 2010-01-09
I recently did a fresh install of Karmic 9.10. When I attempt to install Nvidia drivers I get errors either via repo or Nvidia drivers from Nvidias website. If there is a solution I'm all ears. See below details:

```

My Video Card info:
-------------------------

lspci | grep nVidia
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)



Current Kernel
----------------------------


kg@karmic-mythbox:~# uname -r
2.6.31-17-generic-pae


Errors with envyng
--------------------------------

envyng -t

190.53-0ubuntu1~karmic~nvidiavdpauppa8


Downloading the packages...
dpkg-exec: Running dpkg

Selecting previously deselected package nvidia-190-kernel-source.
(Reading database ... 167230 files and directories currently installed.)
Unpacking nvidia-190-kernel-source (from .../nvidia-190-kernel-source_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb) ...
nvidia-190-kernel-source: Installing nvidia-190-kernel-source

nvidia-190-kernel-source: Preparing nvidia-190-kernel-source

nvidia-190-kernel-source: Unpacking nvidia-190-kernel-source

nvidia-190-kernel-source: Preparing to configure nvidia-190-kernel-source

Unpacking nvidia-glx-190 (from .../nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb) ...
nvidia-glx-190: Installing nvidia-glx-190

dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
nvidia-glx-190: Preparing nvidia-glx-190

dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-190' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb
Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 164, in install
    self.cache.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText))
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 318, in commit
    raise SystemError("installArchives() failed")
SystemError: installArchives() failed






```

---

### Post by sr_guy on 2010-01-09
Anyone else have this issue?

---

### Post by lyall on 2010-01-10
have you tried to use the Hardware Drivers app?

from the System > Administrator > Hardware Drivers
it should show you if you which device you have installed

did you check to see which card are supported for 190.53?

I have a Quadro4 980XGL card and I have to use 96.43.13

You might not try such a new driver,  test some of the older ones before trying the latest one

good luck and have fun learning

---

### Post by SamD42 on 2010-01-12
While attempting to upgrade to 195 from 190.22 similar to this I had horrific dpkg divert errors like these, and was unable to find a fix anywhere until I stumbled across this:

sudo dpkg-divert -&#8211;remove -&#8211;rename -&#8211;package nvidia-glx-185 -&#8211;divert /usr/lib/nvidia/libGL.so.1.xlibmesa /usr/lib/libGL.so.1
sudo dpkg-divert -&#8211;remove -&#8211;rename -&#8211;package nvidia-glx-185 -&#8211;divert /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2
sudo dpkg-divert -&#8211;remove -&#8211;rename -&#8211;package nvidia-glx-185 -&#8211;divert /usr/lib/nvidia/libglx.so.xserver-xorg-core /usr/lib/xorg/modules/extensions/libglx.so
sudo dpkg-divert -&#8211;remove -&#8211;rename -&#8211;package nvidia-glx-185 -&#8211;divert /usr/lib/nvidia/libGLcore.so.xlibmesa /usr/lib/xorg/modules/extensions/libGLcore.so

Taken from [http://blog.mymediasystem.net/uncategorized/the-nvidia-glx-180-opengl3-divert-problem/#comment-2273](http://blog.mymediasystem.net/uncategorized/the-nvidia-glx-180-opengl3-divert-problem/#comment-2273)

I was then able to install normally

---

### Post by w00d1 on 2010-01-12
I'm on a fresh install of Karmic, hitting the same wall. 

If I'm not mistaken, there are at least three different options for a driver to run. There's the one from NVIDIA, an restricted one, a non-restricted one, and several revisions of each. Is that right?
 I'm going in circles here. Something that keeps coming up is disabling the x server before I can install a driver. If someone could dumb some of this down for me I would be eternally grateful. 

Sorry for the n00b questions.

---

### Post by rausuar on 2010-01-28
Thanks! I was also having the same problem, but the solution given in the post solved it for good!

---

### Post by irishwoody on 2010-02-03
Yes thanks - was having the same issue until this post solvd it.
BTW if you copy nad paste the code from this post in the terminal there is a small error the text "--" look like "-_" - you need to fix this before the command(s) will work.
Woody

---

### Post by Fitch on 2010-09-10
I have no GUI screen at all, and have no idea how to find out which driver I am using via the text console.

Can anyone help me with this?  I had to replace the motherboard, and, of course the new nVidia chip will not work with the old driver.  Not even changing to "vesa" in the xorg.conf works

---

