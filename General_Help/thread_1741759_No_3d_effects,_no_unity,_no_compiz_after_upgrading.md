---
title: "No 3d effects, no unity, no compiz after upgrading to Natty"
date: 2011-04-28
forum: General Help
---

### Post by Ginosal on 2011-04-28
Hi. I've upgraded to 11.04, but something must have been gone really bad.

After rebooting, the first message i've been shown was: "Your hardware doesn't support Unity". First strange thing: Unity was working perfectly on all the Beta live versions I've tried before the upgrade.

Well, not a big problem, I didn't really like Unity. Let's stay with Gnome + Compiz, I said.. but Compiz effects don't work anymore. When I try to do System --> Preferences --> Appearance, the "effects" tab doesn't show anymore. The file named "screenshot1.png" will show you this problem, even if it's in Italian: there are only the Theme (tema), Background (sfondo) and Fonts (Tipo di carattere) tabs. Also look to the strange, fuzzy right corner of the themes previews. This didn't happen on 10.10.

3d rendering should be working, since I get
```
glxinfo | grep rendering
direct rendering: Yes

```
But nothing works.

System->Administration->Hardware is empty, but it has always been empty, even on 10.10 (but Compiz effects were working).

When I try to set Compiz as windows manager in Compiz Fusion Icon, sometimes the title of the windows disappear, along with the minimize, maximize and close buttons. Do you think there's something I can do to fix all these things?

Please, help me! Thank you in advance!

P.S. My video card is the following one:

```
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

```

---

### Post by Hedgehog1 on 2011-04-28
Please run system settings:

[IMG]http://img820.imageshack.us/img820/7027/nattysystemsetting.png[/IMG]

And under the 'Hardware' section select the 'additional drivers' to find the ATI drivers for your GPU.

Once the new video driver is loaded, you should be able to run Compiz effects and Unity, too.  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by Ginosal on 2011-04-28
> **Hedgehog1 said:**
> Please run system settings:

[IMG][/IMG]

And under the 'Hardware' section select the 'additional drivers' to find the ATI drivers for your GPU.

Once the new video driver is loaded, you should be able to run Compiz effects and Unity, too.  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

Hi Hedgehog1. First of all, thank you for your help, but my additional drivers windows is empty (look at the screenshot attached)! It was empty also when I had 10.10, but the Compiz effects were there, working! Thanks.

---

### Post by VanR on 2011-04-28
Perhaps try the ATI website for updated video drivers.

---

### Post by Ginosal on 2011-04-28
> **VanR said:**
> Perhaps try the ATI website for updated video drivers.

I've tried, but I got the problem that you can find **[here too]("http://ubuntuforums.org/showthread.php?t=970059")**. I'll try with fglrx.

Anyway, I've tried to install 11.04 from scratch, instead that upgrading 10.10. On that installation, everything works fine.

---

### Post by Slartius on 2011-04-29
> **Ginosal said:**
> Hi. I've upgraded to 11.04, but something must have been gone really bad.

After rebooting, the first message i've been shown was: "Your hardware doesn't support Unity". First strange thing: Unity was working perfectly on all the Beta live versions I've tried before the upgrade.

Well, not a big problem, I didn't really like Unity. Let's stay with Gnome + Compiz, I said.. but Compiz effects don't work anymore. When I try to do System --> Preferences --> Appearance, the "effects" tab doesn't show anymore. The file named "screenshot1.png" will show you this problem, even if it's in Italian: there are only the Theme (tema), Background (sfondo) and Fonts (Tipo di carattere) tabs. Also look to the strange, fuzzy right corner of the themes previews. This didn't happen on 10.10.

3d rendering should be working, since I get
```
glxinfo | grep rendering
direct rendering: Yes

```But nothing works.

System->Administration->Hardware is empty, but it has always been empty, even on 10.10 (but Compiz effects were working).

When I try to set Compiz as windows manager in Compiz Fusion Icon, sometimes the title of the windows disappear, along with the minimize, maximize and close buttons. Do you think there's something I can do to fix all these things?

Please, help me! Thank you in advance!

P.S. My video card is the following one:

```
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

```

I have same problem after my dist-upgrade, but using NVIDIA GeForce Go 7300 card with proprietary drivers (status says: active but not in use). I am unable to get the 3D effects working or even the compiz starting. Well, I have managed to get at least a glimpse of effects after manually launching fusion-icon, but the graphical part of system froze, so gdm restart was required. Does anybody have a clue at what might be wrong? The effects were working without a glitch in 10.10.

And also starting "System settings" crashes my desktop, if there is any connection.

---

### Post by EddieGal on 2011-04-29
> **Slartius said:**
> I have same problem after my dist-upgrade, but using NVIDIA GeForce Go 7300 card with proprietary drivers (status says: active but not in use). I am unable to get the 3D effects working or even the compiz starting. Well, I have managed to get at least a glimpse of effects after manually launching fusion-icon, but the graphical part of system froze, so gdm restart was required. Does anybody have a clue at what might be wrong? The effects were working without a glitch in 10.10.

And also starting "System settings" crashes my desktop, if there is any connection.

I'm getting this but my card is a 7400. Got Unity to work installing unity-2d, then loading Unity 2d session, logging off and started the Ubuntu session. Still can't get Compiz to work (can't use emerald either but guess this is because Compiz isn't running properly)

---

### Post by 1Nyco1 on 2011-04-29
I have exactly the same problem.

---

### Post by xyphias on 2011-04-29
I had exactly the same problem.  My graphics card is an Nvidia 9400GT.  The driver was showing as installed under Hardware Drivers. All I did was use synaptic to install Unity and Unity-2D and then restart X with a quick ctrl-alt-backspace and all went well.

---

### Post by Ginosal on 2011-04-29
> **xyphias said:**
> I had exactly the same problem.  My graphics card is an Nvidia 9400GT.  The driver was showing as installed under Hardware Drivers. All I did was use synaptic to install Unity and Unity-2D and then restart X with a quick ctrl-alt-backspace and all went well.

The strange thing is that everything works fine if I install 11.04 from scratch. I find these issues only in the upgraded ubuntu install.

---

### Post by jerome1232 on 2011-04-29
> **Ginosal said:**
> The strange thing is that everything works fine if I install 11.04 from scratch. I find these issues only in the upgraded ubuntu install.

I also had video related issues with an upgrade, fresh install was fine.

I smell conflicting settings somewhere.

---

### Post by whitefort on 2011-04-29
> **Slartius said:**
>  NVIDIA GeForce Go 7300 card with proprietary drivers (status says: active but not in use). I am unable to get the 3D effects working or even the compiz starting. Well, I have managed to get at least a glimpse of effects after manually launching fusion-icon, but the graphical part of system froze

Fresh install, same card, exact same problems (Lenovo 3000 n100)

I reckon I'm never going to see Unity on this machine, but I'd at least like to get Compiz running again!

---

### Post by DieterVDW on 2011-04-29
Same here, upgrade, no Compiz.
I miss my wobbly windows!

---

### Post by Ginosal on 2011-04-29
SOLVED for me!

I created a usb live version of Natty, then booted from it. Then I started "Install Ubuntu 11.04" and I chose "Upgrade from 11.04 to 11.04". If you don't find this option, *don't do anything*. Anyway, it took a long time for restoring already installed packages, but in the end: unity, 3d acceleration and so on... good luck!

---

### Post by jerome1232 on 2011-04-29
I wonder if that is in anyway equivalent to booting into recovery mode and repairing packages.

Interesting find though!

---

### Post by Ginosal on 2011-04-30
Bad news first: after the first reboot, 3d acceleration & co. disappeared again.

Good news: I've upgraded again from the USB live, but this time I haven't chosen "import account from ubuntu". Now, it works fine again, but I would like to wait a little more...

---

### Post by Slartius on 2011-05-01
I also did an upgrade, but to no avail. The compiz still does not work. I can not even start it as is. After some playing arround I found out, that it might kind of work if, in Fusion Icon, I enable indirect rendering. Then something starts to behave like compiz is working, although I don't have window decorations and I cannot change between different desktops, but at least there is proper number of desktops (4 vs. 6 if I don't have compiz enabled).

---

### Post by Slartius on 2011-05-01
Well, compiz is working, but for that I have to manually "restart" it by selecting metacity and than compiz in Fusion Icon. Same goes for window decorations, but no matter what I do, I cannot pick and drag window. Now I actually performed clean install of 11.04 but still no luck with compiz.

---

### Post by Ginosal on 2011-05-01
Just finished shifting to Mint. Was this choice of Unity so important?

---

### Post by partofthething on 2011-05-02
Why is this marked solved? It is not solved. Still looking for a solution.

---

### Post by NormanFLinux on 2011-05-02
Old trick is if Compiz doesnt work with your card, turn on the Metacity compositing engine. Cool effects without a heavy resource load.

---

### Post by Slartius on 2011-05-02
For a while it looked like it might be solved so I guess that's why. Btw. do all affected with this bug have NVIDIA cards? I guess that the master poster has ATI, but he reported, that he gets some X Error after glxinfo, which works fine for me, although I saw, that I don't have direct rendering enabled. Will also look into this. Are those two issues maybe same bug or are two completely different bugs?

---

### Post by Slartius on 2011-05-02
> **NormanFLinux said:**
> Old trick is if Compiz doesnt work with your card, turn on the Metacity compositing engine. Cool effects without a heavy resource load.
Well main problem is, that for most of us Compiz worked before without a glitch (for me on this computer since several years ago). Although, where do you get cool effects for metacity? 

P.S. I loaded glx module and now I have direct rendering, but still no difference.

---

### Post by markino75 on 2011-05-02
> **Slartius said:**
> For a while it looked like it might be solved so I guess that's why. Btw. do all affected with this bug have NVIDIA cards? I guess that the master poster has ATI, but he reported, that he gets some X Error after glxinfo, which works fine for me, although I saw, that I don't have direct rendering enabled. Will also look into this. Are those two issues maybe same bug or are two completely different bugs?

I experienced same issue with ATI mobility radeon HD 5000.

---

### Post by ryukent on 2011-05-02
Just ran:
/usr/lib/nux/unity_support_test -p


OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7300/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

Now why would a GeForce Go 7300 be blacklisted? It can run Total War and Crysis so I think unity should be ok.

---

### Post by pescez on 2011-05-02
hi guys, i think i found the solution to this issue.

i just solved it installing the appropriate version ov nvidia drivers for my card (nvidia geforce7200 the driver version suggested was the 173.xx) instead of the recommended version automatically installed by natty.
to do it:

-log in with a ubuntu classic (no effects) session
-open administration -> proprietary drivers
-then you should see a grey light with a version of nvidia proprietary drivers and a number, and another one with the green light.
activate the grey one and reboot.
hope this works for you all! ;)

---

### Post by Slartius on 2011-05-02
> **pescez said:**
> hi guys, i think i found the solution to this issue.

i just solved it installing the appropriate version ov nvidia drivers for my card (nvidia geforce7200 the driver version suggested was the 173.xx) instead of the recommended version automatically installed by natty.
to do it:

-log in with a ubuntu classic (no effects) session
-open administration -> proprietary drivers
-then you should see a grey light with a version of nvidia proprietary drivers and a number, and another one with the green light.
activate the grey one and reboot.
hope this works for you all! ;)
Well I tried it before, but didn't work for me. I tried it again now on a fresh install, but it is almost the same for me, except that indirect rendering is working, meaning that it does not freeze the X. I still have to reload window manager manually (I have to start fusion icon and from menu select Reload window manager). And moving the windows arround still does not work. And i have GeForce Go 7300.

---

### Post by NormanFLinux on 2011-05-02
Open up gconf-editor, applications, go to Metacity and where you see the box for compositing engine, enable it. Its not a replacement for Compiz but if nothing else will work with your computer it will at least make docks, like AWN, Cairo and Docky that require a compositing engine to look presentable.

---

### Post by Slartius on 2011-05-02
> **pescez said:**
> hi guys, i think i found the solution to this issue.

i just solved it installing the appropriate version ov nvidia drivers for my card (nvidia geforce7200 the driver version suggested was the 173.xx) instead of the recommended version automatically installed by natty.
to do it:

-log in with a ubuntu classic (no effects) session
-open administration -> proprietary drivers
-then you should see a grey light with a version of nvidia proprietary drivers and a number, and another one with the green light.
activate the grey one and reboot.
hope this works for you all! ;)

> **NormanFLinux said:**
> Open up gconf-editor, applications, go to Metacity and where you see the box for compositing engine, enable it. Its not a replacement for Compiz but if nothing else will work with your computer it will at least make docks, like AWN, Cairo and Docky that require a compositing engine to look presentable.

Thanx, I will try it. 

I also noticed, that the compiz is actually not starting when I log in and I have to manually start it every time I log in. So the workaround that works for me is, that I added among startup applications the fusion icon, which in turn can start selected window manager. I can now normally log in and out with the 3D effects probably working OK. The problem is, that I still can't grab the window and move it around (Alt+F7 also does not work). Any suggestions how to remedy that? 

NVIDA question: Does the recommended driver work for everyone? I have to use the older driver for direct rendering.

---

### Post by partofthething on 2011-05-02
I have an ATI Radeon Mobility X1400 on a Dell E1505. The ATI proprietary driver doesn't work with this chip anymore, but Compiz has worked very well with the open source driver for years. I have no option to install proprietary drivers and really want my Compiz back. What to do?

---

### Post by Slartius on 2011-05-03
For all of you using GeForce Go 7300/7400 the unity won't run since those cards are blacklisted. See: [URL="http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity"]
GeForce blacklisted[/URL]   and
[Bug in compiz]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/726496").
It seams there are several issues with the NVIDIA cards, this being just one of them. 
There are also some problems with NVIDIA driver being activated but not in use. This apparently slows down the graphics (I would concur with that), but can otherwise work (I still have issues with window grabbing).

---

### Post by afrodeity on 2011-05-03
> **Slartius said:**
> For all of you using GeForce Go 7300/7400 the unity won't run since those cards are blacklisted. See: [URL="http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity"]
GeForce blacklisted[/URL]   and
[Bug in compiz]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/726496").
It seams there are several issues with the NVIDIA cards, this being just one of them. 
There are also some problems with NVIDIA driver being activated but not in use. This apparently slows down the graphics (I would concur with that), but can otherwise work (I still have issues with window grabbing).

System Settings > Control Center > Additional Drivers reports NVIDIA version current is activated but not in use.

---

### Post by partofthething on 2011-05-03
For the ATI open source folks, I've noticed that my Radeon driver is not active. My VESA driver is. When I type compiz --replace on the terminal, I get: 
```
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session

```So the problem here is that the ATI radeon driver is not getting loaded properly and therefore compiz can't activate. The question becomes, why is it not active. [This thread]("http://ubuntuforums.org/showthread.php?t=1699110") may be relevant but there's no good solution.

---

### Post by partofthething on 2011-05-03
Progress! 

Going through the [KMS page]("https://wiki.ubuntu.com/X/KernelModeSetting"), it says:
> **Module loading issues on ATI**

 If you get  "RADEONDRIGetVersion failed" in Xorg.0.log it is because of a race  issue. The radeon module is not initialized in time before X is  starting, and X will falsely believe that there is no KMS support and do  its own modesetting... 
To  make sure the radeon modules is initialized before gdm (and X) is  starting, insert "modprobe radeon" into your /etc/init/gdm.conf just  before the gdm-binary is executed: 
    ...     initctl emit starting-dm DM=gdm      modprobe radeon     exec gdm-binary $CONFIG_FILE end scriptI did have that error, and tried the fix, and (after getting a low-graphics mode at first and then restarting again) it worked! Compiz is back. Hooray!

Perhaps related, I also removed the radeon.conf file from my /etc/modprobe.d folder and deleted my xorg.conf file.

---

### Post by afrodeity on 2011-05-04
This works for the classic desktop. The absense of desktop effects tab in System >> Preferences >> Appearance should provide a clue. Compiz needs a basic set of plugins activated in order to work, they are Composite, OpenGL, Window Decoration, Move Window & Resize Window. You can turn them on using CCSM. 

Then: in the terminal 
```

compiz --replace ccp &

```
to launch compiz and 
```

gtk-window-decorator --replace & 
```
to get window decorations.

---

### Post by timgood on 2011-05-04
> **afrodeity said:**
> This works for the classic desktop. The absense of desktop effects tab in System >> Preferences >> Appearance should provide a clue. Compiz needs a basic set of plugins activated in order to work, they are Composite, OpenGL, Window Decoration, Move Window & Resize Window. You can turn them on using CCSM. 

Then: in the terminal 
```

compiz --replace ccp &

```
to launch compiz and 
```

gtk-window-decorator --replace & 
```
to get window decorations.

You are a star! Finally got compiz working in Classic. Many thanks, and oodles of virtual beer!

---

### Post by ErikZane on 2011-05-05
> **afrodeity said:**
> This works for the classic desktop. The absense of desktop effects tab in System >> Preferences >> Appearance should provide a clue. Compiz needs a basic set of plugins activated in order to work, they are Composite, OpenGL, Window Decoration, Move Window & Resize Window. You can turn them on using CCSM. 

Then: in the terminal 
```

compiz --replace ccp &

```
to launch compiz and 
```

gtk-window-decorator --replace & 
```
to get window decorations.

Unfortunately, this doesn't work for me.  The critical piece of output seems to hinge around the fact that GLX isn't working.

> 
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session


Did the location for loading GLX change in xorg.conf?

---

### Post by stuzart on 2011-05-05
This is marked as SOLVED, but I don't believe it is.

---

### Post by weasel fierce on 2011-05-05
So I am getting the "activated but not in use" on my Nvidia G100 under Kubuntu 11.4 as well

---

### Post by c2006 on 2011-05-06
> **Slartius said:**
> Thanx, I will try it. 

I also noticed, that the compiz is actually not starting when I log in and I have to manually start it every time I log in. So the workaround that works for me is, that I added among startup applications the fusion icon, which in turn can start selected window manager. I can now normally log in and out with the 3D effects probably working OK. The problem is, that I still can't grab the window and move it around (Alt+F7 also does not work). Any suggestions how to remedy that? 

NVIDA question: Does the recommended driver work for everyone? I have to use the older driver for direct rendering.

**glxinfo | grep rendering** shows that direct rendering IS working for me (I have a 9600GT), as does nvidia-settings, and I did notice a flicker (a normal thing when you switch drivers) and *much* crisper fonts after running Nvidia's settings tool and saving the configuration to the Xorg.conf file.

Further, compiz effects are working, and a game I run through WINE is working (with glitches, but this is normal, although interestingly said game's opengl mode actually works under Linux. It doesn't in Windows).

Strangely, despite all this, Additional Drivers is reporting the driver as "activated but not in use". Very strange indeed.

---

### Post by afrodeity on 2011-05-06
My workspace switcher still only shows one desktop in Classic. Changing the preferences doesn't seem to do anything, although I do have a compiz cube.

---

### Post by grahammechanical on 2011-05-06
I believe that the driver activated but not in use message means that 3D is not being used. I installed 11.04 beta Edubuntu and I had that driver not in use message. I was using Unity 2D. But on my 10.10 install I had driver activated and in use as the message. I was using the Nvidia 120 driver on both installs.

I have upgraded 10.10 to 11.04 and I now get the driver activated but not in use message and also no proprietary drivers in use on this system. I am not offered a proprietary driver. I think that I am using a Ubuntu developed driver. Perhaps I need to  deactivate this driver and then may be I will get the option of a proprietary driver.

Regards.

---

### Post by afrodeity on 2011-05-06
Workspace switcher problem solved,
In preferences, columns 2, Rows 1

**In ccsm**

General >> Desktop Size >> Horizontal =4, Vertical =1, Number of Desktops =1

A basic classic setup which can be saved via the ccsm preferences export option is the following:

Window Management: Grid, Move Window, Resize Window, Put, Scale, Place, Ring, Shift

Utility: Regex, Scale, Title Bar, Mouse Polling, Resize, Session

Image Loading: tick which you want

Extras: Annotate, Screenshot

Effects, Annimations, Addons, Window Decoration, 3D Windows, Cubic Reflections/Deformation

Desktop: Rotate Cube, Viewport Switcher, Desktop Cube, Expo, Show Desktop,

Accessibility: Opacity & Brightness, Zoom Desktop, Enhanced Zoom

General: Composite, Gnome, OpenGL

If you experienced trouble you can always try compiling compiz yourself, using this script which works flawlessly.
```

sudo apt-get install git-core

git clone git://anongit.compiz.org/users/soreau/scripts


./build_compiz++

./compiz-addons

```

emerald is no longer being developed, so you will need to use the gtk-decorator

```

compiz --replace ccp &

gtk-window-decorator --replace & disown


```

---

### Post by gidoca on 2011-05-08
Have you guys tried to install unity? I had the same problem after the upgrade, and sudo apt-get install unity solved it.

---

### Post by Bromden on 2011-06-04
> **afrodeity said:**
> This works for the classic desktop. The absense of desktop effects tab in System >> Preferences >> Appearance should provide a clue. Compiz needs a basic set of plugins activated in order to work, they are Composite, OpenGL, Window Decoration, Move Window & Resize Window. You can turn them on using CCSM. 

Then: in the terminal 
```

compiz --replace ccp &

```to launch compiz and 
```

gtk-window-decorator --replace & 
```to get window decorations.

Thank you! That solved my compiz problem on 11.04

---

### Post by afrodeity on 2011-06-04
Just some updates on this issue, because I noticed a regression after the last round of updates. If you compiz fails, check to see if xorg is hogging your CPU. I did a[ manual reinstall of my Nvidia driver]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html"), which corrects any Xorg issues. So manually installing NVIDIA driver may also be a solution for some.:)

---

