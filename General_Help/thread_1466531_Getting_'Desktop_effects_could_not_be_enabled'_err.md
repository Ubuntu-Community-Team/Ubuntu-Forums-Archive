---
title: "Getting 'Desktop effects could not be enabled' error while trying to enable 'compiz'."
date: 2010-04-30
forum: General Help
---

### Post by nayankk on 2010-04-30
Hi All,

I am getting following error while trying to enable 'compiz' in 10.4. 

"Desktop effects could not be enabled"

Output of [http://blogage.de/files/9124/download?compiz-check](http://blogage.de/files/9124/download?compiz-check) script present in [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) is below,

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

So, it looks like my hardware support all what it needs for Compiz. What else is going wrong here?

Any help is much appreciated. Sorry, if I provided less details here. Pls let me know if anymore details about the issue is needed. 

Thanks in advance.

Regards
Nayan

---

### Post by dino99 on 2010-04-30
[http://wiki.compiz.org/Hardware/Intel](http://wiki.compiz.org/Hardware/Intel)

---

### Post by rhy7s on 2010-04-30
I'm also getting this message on an Eee 901, was working fine in 9.10 and was working fine for a while after install but now cannot be enabled. My compiz-check output is:

```
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

edit: realised other startup apps weren't starting, this PC is on auto-login, logged out to see that it was switched to failsafe login.

---

### Post by vratnica on 2010-04-30
same problem here

> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon X1950 GT (rev 9a)
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


---

### Post by vratnica on 2010-04-30
also: 

> desktop:~$ compiz
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager


---

### Post by imiunleashed on 2010-04-30
I am getting this, my card is ATI Radeon 4530
Please help, i am stuck :(


Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by treynolen on 2010-05-01
I'm also having this same issue.  ATI Radeon 4850...Has anyone filed/found a bug report for this?

---

### Post by imiunleashed on 2010-05-01
C'mon guys - help us out
How long are we to wait :(

---

### Post by asvravi on 2010-05-01
Same issue here since after upgrading from 9.10 to 10.04. I am on Intel graphics.

```

> compiz
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager


```

```

> glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

No xorg.conf file.

Any help?

---

### Post by asvravi on 2010-05-01
OK, found the solution.

The problem was with a previous install of nvidia drivers that was removed.
Although I am using the intel driver, the GLX extension from Nvidia was being picked up. This is because the alternatives tool is still linked to nvidia for glx lib.
Fixed it with following commands -

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

---

### Post by vratnica on 2010-05-01
so what would than be solution for: Graphics chip: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]?

---

### Post by GameDog(A) on 2010-05-01
I'm having the same problem.  And update's yet?

---

### Post by imiunleashed on 2010-05-01
> **vratnica said:**
> so what would than be solution for: Graphics chip: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]?

Same question here !

---

### Post by HardWorkinSwaney on 2010-05-01
> **asvravi said:**
> OK, found the solution.

The problem was with a previous install of nvidia drivers that was removed.
Although I am using the intel driver, the GLX extension from Nvidia was being picked up. This is because the alternatives tool is still linked to nvidia for glx lib.
Fixed it with following commands -

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

I had the exact same problem - everything working fine in 9.04 but didnt after upgrade to 10,04.   My gfx card is a crappy onboard intel.   

Thanks heaps for the post!!!

---

### Post by tagno25 on 2010-05-02
> **asvravi said:**
> OK, found the solution.

The problem was with a previous install of nvidia drivers that was removed.
Although I am using the intel driver, the GLX extension from Nvidia was being picked up. This is because the alternatives tool is still linked to nvidia for glx lib.
Fixed it with following commands -

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

That worked for me with my ATI Radeon Xpress 200M.

---

### Post by vratnica on 2010-05-03
I tried it out too,

and it worked!

Thanks, dudes!:popcorn:

---

### Post by nayankk on 2010-05-03
Thanks a lot guys. It worked! :)

---

### Post by adrianhensler on 2010-05-03
Worked for me as well, thanks for the post!

---

### Post by gandhii on 2010-05-07
I use a nvidia chipset, and it worked fine in 9.10.   Not working now in 10.04.   I can't exactly purge nvidia drivers.  That won't fix my problem.  Any ideas for me?

---

### Post by axle_foley00 on 2010-05-18
I am having the same problem as gandhii. I have an nvidia graphics card and am getting this error. Any other ideas?

---

### Post by srcsantos on 2010-05-20
Hello everyone. This is my first post, but i think you'll like it.
I was having problems with 3D acceleration aswell: compiz wouldn't work, neither would glxgears, and both would give me the "error: glxcreatecontext failed" message.
I'm sure most have seen the same solution as i did: adding [FONT=Verdana]'[/FONT]ModulePath      "/usr/lib/xorg/modules/extensions/nvidia"'[FONT=monospace] [/FONT]to your "Files" section in xorg.conf.
I tried that too, but it didn't work. The thing is, that path doesn't exist in my system, but i did find a "/usr/lib/xorg/extra-modules", and adding it solved my problem.

So if (like me) you have tried everything and nothing worked, try doing this:
- edit /etc/X11/xorg.conf as root;
- locate 'Section "Files"';
- add[FONT=Verdana] [/FONT]'ModulePath "/usr/lib/xorg/extra-modules"';
- save the file and reboot.

I have Ubuntu 10.04 and the latest nvidia drivers (195.x).

---

### Post by trevelyn on 2010-05-26
> 
Hello everyone. This is my first post, but i think you'll like it.
I was having problems with 3D acceleration aswell: compiz wouldn't work, neither would glxgears, and both would give me the "error: glxcreatecontext failed" message.
I'm sure most have seen the same solution as i did: adding 'ModulePath "/usr/lib/xorg/modules/extensions/nvidia"'to your "Files" section in xorg.conf.
I tried that too, but it didn't work. The thing is, that path doesn't exist in my system, but i did find a "/usr/lib/xorg/extra-modules", and adding it solved my problem.

So if (like me) you have tried everything and nothing worked, try doing this:
- edit /etc/X11/xorg.conf as root;
- locate 'Section "Files"';
- add'ModulePath "/usr/lib/xorg/extra-modules"';
- save the file and reboot.

I have Ubuntu 10.04 and the latest nvidia drivers (195.x


I am using that driver too.  I have an NVIDIA 3100m DELL Latitude E6410 and am using Lucid (Which I don't recommend).  I see the NVIDIA splash at GDM startup and have proper screen resolution.  I installed the drivers from source.  I had desktop effects enabled fine, but was using pyrit/CUDA for a while and didn't want Compiz getting in the way of CUDA.  I temporarily disabled the effects and now cannot re-enable them.  

When I do the fix mentioned above, I get about 6 or 7 errors about missing modules and Gnome starts with a screen split in half, in low resolution.  removing the lines:

```
Section "Files"
   ModulePath "/usr/lib/xorg/extra-modules"
EndSection
```

Fixes the start up issue, but I cannot load effects.  I see the directory "/usr/lib/xorg/extra-modules" but it's empty.  I also have "/usr/lib/xorg/x11-extra-modules" which is empty and one just labeled "/usr/lib/xorg/modules" which is full of things.  I set the ModulePath in xorg.conf file to:

```
"/usr/lib/xorg/modules"
```

and X starts just fine, but without effects.  I had to really break my back just to get the drivers working properly: 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/556872/comments/16]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/556872/comments/16")

I found this BUG: 

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/506247]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/506247")

Which led me to what seems to be my issue: 

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/506547]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/506547")

Because my glxinfo said: NOT FOUND ERROR etc.  So I reinstalled the glx meas lib:

```
apt-get install --reinstall libgl1-mesa-glx
```

And my glxinfo command output was back to normal.  I restarted gdm and rebooted, but Desktop Effects STILL cannot find the drivers.

I have spent probably 10 hours trying to get ANY type of Linux to run properly on my machine, FreeBSD seems to be the only OS that runs on it out of the box.  but NO version of *nix has a proper working ACPI.  Once I get this video driver working I am remastersys-ing the OS so I don't have to go through this pain again.

---

### Post by srcsantos on 2010-05-30
Hello trevelyn.
I hope you haven't given up on Linux...
Would you please post your xorg.conf?

---

### Post by partingd on 2010-05-31
I had a similar issue but was able to work around it.  I am using the "nvidia-current" driver on Lucid.  After it installed I noticed I could not get any of the special effects I got on 9.10.  I check the xorg.log and saw the following:
        "snip"
        Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
        "snip"

As it turns out the installation of "nvidia-current" puts the correct libglx.so module in /usr/lib/nvidia-current/xorg.  However, the xorg installation process is looking for this module in /usr/lib/xorg/modules/extensions.  So the work around is to delete libglx.so and then copy from /usr/lib/nvidia-current/xorg the libglx.so module which is a link to the nvidia version.

I am not sure how to fix the "nvidia-current" script yet but the work around solved my issue.

---

### Post by Mikokok on 2010-06-01
Hi, i have one problem, i can't enable my desktop effects after upgrading my system Ubuntu 9.10 to Ubuntu 10.4.  
This is my compiz check
> 
mikokok@mikokok-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon 2100
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 



Can you help me please?

---

### Post by Guy Sibley on 2010-06-01
for the radeon I used fglrx driver (which is in the repository i think) and it worked for my compiz settings, gaming in wine, etc..  Unfortunatly ATI HD graphics can be a little tricky in ubuntu.  
good luck

---

### Post by Guy Sibley on 2010-06-01
but you will get compiz to work if you are patient, i have it working on a netbook right now. Don't give up it may take some time but it is worth it.

---

### Post by Mikokok on 2010-06-01
But how can I install him?:P

---

### Post by srcsantos on 2010-06-16
Hello everyone.
Yesterday i did a fresh Ubuntu 10.04 x64 install on a recent laptop equiped with a nvidia vga and adding "extra-modules" to xorg.conf didn't work. So i found another "libglx.so" inside "/usr/lib/xorg/modules/extensions" and renamed it to "libglx.so.bak". After restarting xserver, the problem was solved: glx was working and i could enable compiz.

So i guess the solution is installing the right nvidia driver (and all required libraries), adding ModulePath "/usr/lib/xorg/extra-modules" to xorg.conf AND renaming/removing any other existing libglx.so. I hope this saves someone else the time it took me to solve it...

PS.: this works with the latest nvidia driver, but i suspect older drivers may not use the "extra-modules" folder.

---

### Post by afrodeity on 2010-06-23
> **srcsantos said:**
> Hello everyone.
Yesterday i did a fresh Ubuntu 10.04 x64 install on a recent laptop equiped with a nvidia vga and adding "extra-modules" to xorg.conf didn't work. So i found another "libglx.so" inside "/usr/lib/xorg/modules/extensions" and renamed it to "libglx.so.bak". After restarting xserver, the problem was solved: glx was working and i could enable compiz.

So i guess the solution is installing the right nvidia driver (and all required libraries), adding ModulePath "/usr/lib/xorg/extra-modules" to xorg.conf AND renaming/removing any other existing libglx.so. I hope this saves someone else the time it took me to solve it...

PS.: this works with the latest nvidia driver, but i suspect older drivers may not use the "extra-modules" folder.


I also have the glx module failing to load problem. There is nothing in extra-modules. I've ModulePath "/usr/lib/xorg/modules" instead to xorg.conf.

and moved libglx.so to bak.

contents of the /usr/lib/xorg/modules/extensions folder now:

```

-rw-r--r-- 1 root root   17920 2010-06-09 13:01 libdbe.so
-rw-r--r-- 1 root root   13784 2010-06-09 13:01 libdri2.so
-rw-r--r-- 1 root root   34488 2010-06-09 13:01 libdri.so
-rw-r--r-- 1 root root   92336 2010-06-09 13:01 libextmod.so
-rwxr-xr-x 1 root root 3014344 2010-06-18 18:34 libglx.so.195.36.31
-rw-r--r-- 1 root root  334432 2010-06-09 13:01 libglx.so.bak
-rw-r--r-- 1 root root   26188 2010-06-09 13:01 librecord.so

``` 

Glx module still not loading. The other glx file libglx.so.195.36.31 looks a bit strange. Its quite large, has a number and different permissions.

Xorg Syslog now
```

LoadModule: "glx"
(WW) Warning, couldn't open module glx
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (module does not exist, 0)

```

Maybe it needs to be renamed?

UPDATE: renaiming libglx.so.195.36.31 to libglx.so worked for me. It must me the last round of updates which regressed part of the system back to before I installed the nvidia 195 driver.

---

### Post by srcsantos on 2010-06-23
Hello afrodeity.
My sugestion would be for you to rename "libglx.so" back to "libglx.so.195.36.31" and create a symbolic link named "libglx.so" ponting to "libglx.so.195.36.31".
I think that the nvidia driver installer tried to do that but must have failed because there was already a file with that name in the same folder.
If you don't rename the file back, you will probably get a "missing file" error if you try to uninstall or update/upgrade the current driver.

---

### Post by afrodeity on 2010-06-24
Hi srcsantos, you quite right, I guess it should be a symbolic link.

---

### Post by xaralis on 2010-08-18
Hi, I had similar problems but it always seems to be solved by simply reinstalling proprietary NVIDIA drivers from command-line when not running X server. Try it out!

Link is: [http://www.nvidia.com/object/linux-display-ia32-256.44-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.44-driver.html) for 32bit. You can find 64bit version here as well.

Boot with recovery option, choose to run in low-level grapics mode and window will appear telling you that something's wrong with graphics settings.. Then choose to run without X and run the NVIDIA driver installer accepting everything it offers you.

---

### Post by Franklin383 on 2010-08-23
Hy Thinks asvravi,

This worked great on my Dell Vostro 1000 labtop.

---

### Post by jazzmofo on 2010-09-14
For me it went wrong trying to install ATI drivers for my x1950. In the end, after 5 hours googling.... [this was the only thing which did the trick for me]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch").

---

