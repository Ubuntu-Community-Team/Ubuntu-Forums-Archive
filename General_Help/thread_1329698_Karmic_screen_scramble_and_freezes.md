---
title: "Karmic: screen scramble and freezes"
date: 2009-11-17
forum: General Help
---

### Post by sombrancelha on 2009-11-17
Hello,

I was using Ubuntu 9.04, no problems. When I upgraded to 9.10, a big problem started happening.

Sometimes the screen simply scrambles everything and the system freezes. I tried changing to "text-mode" and restarting through sudo shutdown -r now, but nothing happened. Apparently the system froze.

I have to force a shutdown and when I try to turn it on again, sometimes all the screen is black. And sometimes it just works.

This happened about 5 times now.

Thanks

---

### Post by Vermind on 2009-11-17
Smells like graphics drivers.
Which card and driver do you have?
Paste this in a terminal:
```
glxinfo | grep -i opengl
```
Then paste the output here.

---

### Post by sombrancelha on 2009-11-17
I'm using a HP dv6420la laptop.

This is the output:

```
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6150/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 185.18.36
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

```

---

### Post by Vermind on 2009-11-18
I suggest getting the nvidia-glx-190 and nvidia-settings-190 packages from this ppa:

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

You can also get nvidia's vdpau, nvidia-190-libvdpau. It is another video output option in mplayer, gstreamer, and so on. It uses less cpu than XV and XvMC.

To easily add the ppa, look here: 
[http://ubuntuforums.org/showthread.php?t=1232171](http://ubuntuforums.org/showthread.php?t=1232171)

---

### Post by sombrancelha on 2009-11-19
I can only install nvidia-glx-180

The PPA offers nvidia-graphics-drivers-190, is that it?

---

### Post by Vermind on 2009-11-19
**Edit: Sorry, the PPA I gave you was for Jaunty. Here is the right PPA:**
[https://launchpad.net/~thefirstm/+archive/karmic-testing](https://launchpad.net/~thefirstm/+archive/karmic-testing)

From my instructions in [http://ubuntuforums.org/showthread.php?t=1232171](http://ubuntuforums.org/showthread.php?t=1232171)
1. Save the script ([ppa-add.sh]("http://ubuntuforums.org/attachment.php?attachmentid=123718&d=1251287757"))  anywhere.
2. Make it executable by right-clicking, choosing Properties, Permissions, and Allow executing the file as a program.
3. Double-click it and choose Run.
3.5 The script may need to install zenity to show you dialogs. This will require your password.
4. The script asks for the PPA address. Put in [https://launchpad.net/~thefirstm/+archive/karmic-testing](https://launchpad.net/~thefirstm/+archive/karmic-testing)
5. give your password for adding the ppa and its public key.
6. Open synaptic from System - Administration- Synaptic.
7. Press the Reload button or press Ctrl-R.
8. find nvidia-glx-190, nvidia-settings-190 and install them.
9. If you do not want to update anything else from this ppa, go to Settings - Repositories - Other software in synaptic. Untick thefirstm.

---

### Post by sombrancelha on 2009-11-23
I installed the recommend ppas, but the problem happened again.

---

### Post by Vermind on 2009-11-23
Ok,
the driver is the correct one for your card though; I checked and your card is supported.

Next, I have only guesses, here's one: on my desktop, nvidia did not even boot if I have the bootsplash enabled (this was before karmic). You can try to disable it and see if this has any effect. The way to do this depends on if you have grub2 installed (check this from synaptic).

If You have grub2, then: ```
sudo gedit /etc/default/grub
``` and change the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```
and then run the command ```
sudo update-grub
```

If on the other hand you did an upgrade install and do not have grub2,
```
sudo gedit /boot/grub/menu.lst
```
and change ```
# defoptions=quiet splash
```
to ```
# defoptions=quiet
```
and then run the command ```
sudo update-grub
```.

---

### Post by sombrancelha on 2009-11-23
I didn't have grub2, performed the instructions.

Now let's wait and see if it happens again.

---

### Post by sombrancelha on 2009-12-02
Apparently solved the problem, hadn't had it since.

Thanks

---

### Post by sombrancelha on 2010-02-03
I updated Ubuntu and this problem started happening again, quite frequently.

I still don't have grub2 and I've checked that the instructions given by Vermind are still correct.

Is it possible to check what have been the last updates made to the system? This might provide some hint on what is causing the problem.

It might be that the problem is an update in NVIDIA's driver. The output of

```

glxinfo | grep -i opengl
```

is

```

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6150/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 190.53
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
```

(note the difference in the version string)

---

### Post by Vermind on 2010-02-03
You might try removing / installing the xsplash package (depending if you had it or not).

Also, I use a very new nvidia driver, newer than 190, from the PPA. I did not have issues with my HP dv6500 or my self-built desktop with nvidia graphics.

---

### Post by sombrancelha on 2010-02-03
The newest NVIDIA driver I found is 195.

I've installed nvidia-glx-195. This required uninstalling:
nvidia-190-kernel-source
nvidia-glx-190
nvidia-settings-190

and installing:
nvidia-195-kernel-source
nvidia-settings

Should I install/uninstall anything else?

Regarding xsplash, I had it, so I uninstalled it. (package name: ubuntu-desktop xsplash).

EDIT: Apparently, I have to install something else, because when I run glxinfo | grep -i opengl I get

```

Error: API mismatch: the NVIDIA kernel module has version 190.53,
but this NVIDIA driver component has version 195.30.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6150/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 190.53
OpenGL shading language version string: (null)
OpenGL extensions:

```

---

### Post by Vermind on 2010-02-03
upgrading the nvidia kernel module requires a reboot. Maybe you just need a reboot?

---

### Post by emoguitarist06 on 2010-03-06
BUMP

Was this ever fixed?
I found a bug reported
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/527149](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/527149)
and I have the flickering problems as well on my Compaq Presario Laptop

---

### Post by Vermind on 2010-03-06
A long time ago, I also had the problem that nvidia drivers did not install with DKMS for my kernel, so I used an older kernel for a while. I thought nowadays they are fine.
I have these installed on my x86_64 desktop:

```
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-185-modaliases
nvidia-190-kernel-source
nvidia-190-libvdpau
nvidia-190-libvdpau-dev
nvidia-190-modaliases
nvidia-195-libvdpau
nvidia-96-modaliases
nvidia-common
nvidia-glx-190
nvidia-settings-190
```

Perhaps these can fix the problem?

---

