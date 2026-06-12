---
title: "Nvidia, Unity, glxinfo couldn't find RGB GLX visual"
date: 2011-04-05
forum: General Help
---

### Post by Mozai on 2011-04-05
Distro: Ubuntu 11.04-beta1 'natty'
Problem: 'your hardware does not support Unity; you will be using Ubuntu Classic.'

Installed: [FONT="Courier New"]nvidia-common 0.2.28,
           nvidia-current 270.30-0ubuntu3,
           nvidia-settings 270.29-0ubuntu1,
           linux-image-generic-pae 2.6.38.7.21,
           linux-headers-generic-pae 2.6.38.8.22[/font]

Symptoms:
[font="Courier New"]moses@deunan:~$ glxinfo
  name of display: :0.0
  [COLOR="Red"]Error: couldn't find RGB GLX visual or fbconfig[/COLOR]

  moses@deunan:~$ lsmod |grep nvidia
  nvidia               9736626  34 

  moses@deunan:~$ egrep '\((EE|WW|NI)\)' /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
  [  1882.609] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
  [  1882.609] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
  [  1882.609] (WW) Disabling Keyboard0
  [  1882.609] (WW) Disabling Mouse0
  ... (that is to say, no errors)

  moses@deunan:~$ egrep -i 'glx|nvidia' /var/log/Xorg.0.log
[  1882.611] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  1882.611] (II) LoadModule: "glx"
[  1882.611] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  1882.636] (II) Module glx: vendor="NVIDIA Corporation"
[  1882.637] (II) NVIDIA GLX Module  270.30  Fri Feb 25 14:51:42 PST 2011
[  1882.637] (II) Loading extension GLX
[  1882.638] (II) LoadModule: "nvidia"
[  1882.638] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1882.639] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1882.639] (II) NVIDIA dlloader X Driver  270.30  Fri Feb 25 14:36:05 PST 2011
[  1882.639] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1882.654] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1884.656] (II) Loading extension NV-GLX
[  1884.702] (II) [COLOR="Red"]Initializing extension GLX[/COLOR][/font]
  ... (again, no errors.  Xorg says the glx module is loaded just fine.)


[font="Courier New"]moses@deunan:~$ dmesg |grep unity
  [ 1894.457837] [COLOR="Red"]unity_support_t[/COLOR][5990]: [COLOR="Red"]segfault[/COLOR] at 48 ip b761f473 sp bfd8ec60 error 4 [COLOR="Red"]in libGL.so.1.2[/COLOR][b75ed000+58000]

  moses@deunan:~$ locate libGL.so.1.2
  /usr/lib/mesa/libGL.so.1.2[/FONT]
  (... so unity_support_t is linking in the mesa library, not /usr/lib/nvidia-current/libGL.so.1 as I would expect)

After reading a few other threads on the matter, I suspect the problem is with the 'nvidia-current' package more than the libgl1-mesa-glx or unity packages.  ... though it does seem odd that Unity doesn't have a non-OpenGL verison.

If I find a solution, I'll come back.  I hope the answer isn't "ditch nvidia-current for the binary install script from nVidia direct."
If someone found this thread in a search, the nVidia driver install scripts can be found at [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

---

### Post by Mozai on 2011-04-05
Came back from the nVidia website.  Here's what I found:

Over there, version '260.19.44' is most recent, but I remember that Ubuntu's packages mention version '270.xx.xx' so I also grabbed 'Version: 270.18'.  Results were the same for both.

Switched to one of the consoles, logged in and 'sudo -i' to root.
'service gdm stop'
'rmmod nvidia'
'dpkg --purge nvidia-current'
'sh NVIDIA-Linux-x86-260.19.44.run'
 ... it will warn that the distro pre-install script failed. That's just a speed-bump that Ubuntu put in to make sure you don't install unsupported drivers by accident.

'startx'  ... failed.
[FONT="Courier New"][  4290.628] (II) LoadModule: "nvidia"
[  4290.629] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  4290.629] (II) Module nvidia: vendor="NVIDIA Corporation"
[  4290.629]    compiled for 4.0.2, module version = 1.0.0
[  4290.629]    Module class: X.Org Video Driver
[  4290.629] ================ WARNING WARNING WARNING WARNING ================
[  4290.629] This server has a video driver ABI version of 10.0 that is not
supported by this NVIDIA driver.  Please check
[http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X
server with a supported driver ABI.
[  4290.630] =================================================================
[  4290.630] (EE) NVIDIA: Use the -ignoreABI option to override this check.
[  4290.630] (II) UnloadModule: "nvidia"
[  4290.630] (II) Unloading nvidia
[  4290.630] (EE) Failed to load module "nvidia" (module requirement mismatch, 0)
[  4290.630] (EE) No drivers available.
[/FONT]

'sh ./NVIDIA-Linux-x86-260.19.44.run --uninstall' to clean it out.
Tried the same with 'NVIDIA-Linux-x86-260.19.44.run' and got the same 'ABI version 10' error.

So looks like I'm stuck with package nvidia-current 270.30-0ubuntu3 , which Xorg happily thinks has OpenGL / GLX support, until it actually tries to use it.  Bleah.

I'll keep trying with Ubuntu 11.04 'natty', and report back to this thread if I find anything.

---

### Post by Mozai on 2011-04-05
Found it.

Since glxinfo was one of the programs having trouble, I tried 'ldd /usr/bin/glxinfo' to see what libraries it was loading.

[FONT="Courier New"]moses@deunan:~$ ldd /usr/bin/glxinfo
 linux-gate.so.1 =>  (0xb7776000)
 libGL.so.1 => /usr/lib/libGL.so.1 (0xb768e000)[/FONT]

Checking on that, I tried 'dpkg -S /usr/lib/libGL.so.1' and discovered it was part of package 'libgl1-mesa-dev'.  So I removed it.

Still didn't work -- ldconfig remade the file.  (?!)  ldconfig made it as a softlink to libGL.so.1.2, so I asked 'dpkg -S /usr/lib/libGL.so.1.2' and I got "no path found matching pattern', so that means this library didn't come from an Ubuntu package. :???:(???)  I couldn't just remove it either, because then /usr/bin/vi would stop working because it couldn't find libGL.so.1 (!!!):confused:

On a hunch, and after seeing the contents of /etc/ld.so.conf.d/GL.conf = '/usr/lib/nvidia-current/', I deleted /usr/lib/libGL.so.1 and /usr/lib/libGL.so.1.2, and re-ran 'ldconfig' to remake the LD path.

[FONT="Courier New"]/bin/rm /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2
ldconfig
ldd /usr/bin/glxinfo
...linux-gate.so.1 =>  (0xb78a7000)
...[COLOR="Red"]libGL.so.1 => /usr/lib/nvidia-current/libGL.so.1[/COLOR] (0xb77bf000)
...libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb76a4000)
[/FONT]

So things seem better now, and I was able to restart the X server with 'sudo service gdm restart' and log in using Unity again.

---

### Post by lithopsian on 2011-04-05
Very common problem.  libGL.so.1.2 occurs in at least two Ubuntu packages, neither of which are the GLX driver you want with nVidia proprietary drivers.  ldconfig attempts to create symlinks to the "most recent" version of each driver but doesn't always get it right, especially with this type of driver where objects are kept in different directories.  It is always best to try and uninstall whatever you had before you install nVidia drivers, but keep an eye on those symlinks anyways.

---

### Post by Mozai on 2011-04-17
> **lithopsian said:**
> Very common problem. ..with nVidia proprietary drivers.

Ah, thanks, I figured that would be the case.

I woudln't have installed the non-Ubuntu drivers, except when I upgraded to 11.04 natty, all of the Nvidia drivers were gone, and thus I had no X-windows.  The documentation on installing video drivers always says to use the GUI tool... which is impossible to use when I have no X-windows (catch-22).  I was forced to use /usr/bin/lynx to get the drivers from the Nvidia website and install those into the kernel and initrd.  Un-installing the nvidia drivers from nvidia seems to be an awful mess, since I've re-un-installed them three times, installed the drivers from ubuntu twice, and apport still complains to me that I'm using nVidia drivers that didn't come from Ubuntu.

---

### Post by quequotion on 2011-07-06
Thanks for this post!
I was having this problem after several drastic configuration changes.

---

### Post by fizikz on 2011-08-05
What is the solution? I have exactly the same problem as the OP. To give some background, I had the proprietary nVidia drivers installed manually, and then tried to uninstall them and use nvidia-current from jockey. glxinfo, glxgears, and unity do not work. An explanation of the solution would be appreciated!

---

### Post by jcdoll on 2011-10-15
@Mozai

Thanks for your posts. They fixed a longstanding problem (since 11.04) I've had with an ATI 5750 using both the binary and open-source drivers. I'm replying with more details in the hopes that someone with similar problems can find it.

My desktop machine has never supported unity. When I ran "/usr/lib/nux/unity_support_test -p" it always returned "gl vertex buffer object: no". So in 11.04 I stuck with the gnome-shell, but after installing 11.10 I decided to try solving the problem. After poking around online, I tried running "glxinfo | grep rendering" and found out that direct rendering was disabled (direct rendering: no).

After some more poking around online, I found that /usr/lib/fglrx/dri/swrast_dri.so didn't exist and that it should. So I ran "sudo apt-get install libgl1-mesa-swrast" and added a symbolic link to /usr/lib/fglrx/dri/.

But then, running glxinfo returned "Error: couldn't find RGB GLX visual or fbconfig", which is how I came across your post. At this point, I was willing to try just about anything, so I followed your tip and deleted usr/lib/libGL.so.1 and /usr/lib/libGL.so.1.2 and reran "sudo ldconfig".

And lo and behold, it finally worked. So thanks for that. This was an *extremely* frustrating problem to solve and I'm a little giddy that it's finally gone.

---

### Post by gmiller1018 on 2011-12-01
Thanks Mozai, this was also the problem in Fedora.  I ended up with libGL.* in /usr/lib/ , /usr/local/lib, and /lib. Once all of those were removed, and a new run of ldconfig all was working again.
:KS

---

### Post by deceaseddolphin on 2011-12-24
> **jcdoll said:**
> @Mozai

Thanks for your posts. They fixed a longstanding problem (since 11.04) I've had with an ATI 5750 using both the binary and open-source drivers. I'm replying with more details in the hopes that someone with similar problems can find it.

My desktop machine has never supported unity. When I ran "/usr/lib/nux/unity_support_test -p" it always returned "gl vertex buffer object: no". So in 11.04 I stuck with the gnome-shell, but after installing 11.10 I decided to try solving the problem. After poking around online, I tried running "glxinfo | grep rendering" and found out that direct rendering was disabled (direct rendering: no).

After some more poking around online, I found that /usr/lib/fglrx/dri/swrast_dri.so didn't exist and that it should. So I ran "sudo apt-get install libgl1-mesa-swrast" and added a symbolic link to /usr/lib/fglrx/dri/.

But then, running glxinfo returned "Error: couldn't find RGB GLX visual or fbconfig", which is how I came across your post. At this point, I was willing to try just about anything, so I followed your tip and deleted usr/lib/libGL.so.1 and /usr/lib/libGL.so.1.2 and reran "sudo ldconfig".

And lo and behold, it finally worked. So thanks for that. This was an *extremely* frustrating problem to solve and I'm a little giddy that it's finally gone.
"sudo apt-get install libgl1-mesa-swrast"

that line worked for me... thanks!

---

### Post by DomRuf on 2012-01-01
Thanks, deceaseddolphin, this line seems to have helped also to me. :)

---

### Post by rsvancara on 2012-01-01
Great solution.  Thanks for posting this!

:p

---

### Post by bodymind on 2012-01-14
he problem is that when u remove the nvidia drivers.. the files in /usr/lib/xorg/modules/ are removed... but if you reinstall the intel driver it will copy the files back again and everything will be fine! :)

$ sudo apt-get remove xserver-xorg-video-intel

$ sudo apt-get install xserver-xorg-video-intel


[http://askubuntu.com/questions/87149/intel-hd-3000-sandy-bridge-3d-games-problem/95441#95441](http://askubuntu.com/questions/87149/intel-hd-3000-sandy-bridge-3d-games-problem/95441#95441)
[http://askubuntu.com/questions/67808/getting-gnome-shell-working-on-nvidia-optimus-notebook](http://askubuntu.com/questions/67808/getting-gnome-shell-working-on-nvidia-optimus-notebook)

---

### Post by Luz77 on 2012-03-10
> **deceaseddolphin said:**
> "sudo apt-get install libgl1-mesa-swrast"
thanks! due to your post I found the package I needed:
```
sudo apt-get install libgl1-mesa-swx11
```
(I installed this because it provided the libgl1-mesa-swrast and because I haven't found the libgl1-mesa-swrast in the repo. However, the game runs very slow, maybe I need to install other packages :/ )

---

### Post by FakenMC on 2012-04-09
> (I installed this because it provided the libgl1-mesa-swrast and because I haven't found the libgl1-mesa-swrast in the repo. However, the game runs very slow, maybe I need to install other packages :/ )

That's because libgl1-mesa-swrast is an OpenGL software rasterizer, i.e., its using your CPU instead of your GPU, so it's much slower. It's not really a solution.

It's possible to simultaneously have the Mesa OpenGL lib and your graphic driver OpenGL lib. You have to make sure that your graphic driver OpenGL lib takes priority, so that when you run ```
ldd /usr/bin/glxinfo
```, you get something like:

```
libGL.so.1 => /usr/lib/nvidia-current/libGL.so.1
```

and not something like:

```
libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1
```

You can do this configuring your ld paths or by changing your LD_LIBRARY_PATH, so that your graphics driver OpenGL lib takes priority. More info here:

[http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html]("http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html")

---

### Post by manoftao on 2012-11-05
I have arrived here hoping your solutions would help - after hours of scouring the net - only to find this didnt work either. I installed Google Earth - which I had installed and working fine on last system install - but now (fresh 12.04) it doesnt work - due to missing GLX (glxinfo: Xlib:  extension "GLX" missing on display ":0"). Glx works with mesa (after I purge nvidia drivers) but it doesnt render planet Earth except for country lines, all else invisible.. And very slow.. I tried Moses' solution to no avail; that is, after installing latest nvidia-current, Google Earth splashes then nothing, clearly refusing to start due to missing GLX.. Had trouble finding the GL.so.1 and 1.2 files which were in a different dir to Moses' entry. rm them then ldconfig, no effect. Unity menu, and Cairo-dock both work fine except for Google Earth.. which I enjoy exploring. It may be the latest nvidia drivers or latest GE, or both, I cant quite figure out. I am no expert Linux user but have used it for 2 years now and am very happy with it. Any suggestions are welcome. Cheers

---

