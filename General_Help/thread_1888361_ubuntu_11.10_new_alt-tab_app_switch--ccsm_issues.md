---
title: "ubuntu 11.10 new alt-tab app switch--ccsm issues"
date: 2011-11-29
forum: General Help
---

### Post by jodiaq on 2011-11-29
Hello!
I installed ubuntu 11.10,i liked the new  alt-tab switcher and the interface of the system. But the new alt-tab switcher is gone.  How  do i restore the settings to default? Now if i press alt-tab it shows the application switchers in the classical fashion. Though the switching action works i just need that new graphical alt-tab switcher.

Also i installed the ccsm but the changes made in the ccsm are not reflected. They are not implemented. Literally ccsm is not working in my system.

Help me .

Thanks!

---

### Post by jodiaq on 2011-11-30
Common fellas give me some hint...

---

### Post by jodiaq on 2011-12-01
Am i helpless here?

---

### Post by stinkeye on 2011-12-01
If your other ccsm settings aren't being applied you may be in a
Unity 2d session using metacity as the window manager.
If you install wmctrl...
```
sudo apt-get install wmctrl
```

this will tell you what window manager your using
```
wmctrl -m
```

eg
```
glen@Oneiric:~$ wmctrl -m
Name: [COLOR="Red"]Compiz[/COLOR]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

Make sure your logging in to the "Ubuntu" session.
At the greeter select the user then choose the session by clicking on the cog.

---

### Post by jodiaq on 2011-12-05
Thanks for the hint.
Actually my graphics card was not installed properly. So i reinstalled it. Now i can have my google earth also working.
Keeping these things aside as you told me  i logged in using the ubuntu and i applied some settings in ccsm and it worked. i saw using wmctrl also it showed compiz.
But it messed up every thing. 
launcher come after 2min delay close minimize buttons disappeared later every thing,Except the home folder window that was previously opened.
Later i restarted the system again the same problem.
My graphics card is 512mb nvidia geforce. Is it not enough ?
what is the problem. Why is it unable to display animations.

---

### Post by JasonSaras on 2011-12-05
Hi.

I have more or less the same problem. When I installed 11.10, everything was fine since today that window manager or something related to graphics seems to have been degraded. For instance, my alt tab appereance has changed and I cannot drag a window on the left of the screen to be maximized only on the left half of the screen.

I tried wmctrl and it showed that I am currently running metacity. So when I tried: "compiz --replace&" the terminal printed:

```

[1] 2174
jason@ubuntu:~$ Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session

(metacity:2179): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

Can I do something to fix it? Thanks in advance.

---

### Post by stinkeye on 2011-12-05
What does this in terminal give you
```
lspci -k | grep -A3 VGA
```

eg
```
glen@Oneiric:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
	Subsystem: nVidia Corporation Device 066d
	**Kernel driver in use: nvidia**
	Kernel modules: nvidia_current, nouveau, nvidiafb
```

---

### Post by JasonSaras on 2011-12-05
```
jason@ubuntu:~$ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 144a
	Kernel driver in use: i915
	Kernel modules: i915
--
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
	Subsystem: Hewlett-Packard Company Device 144a
	Kernel driver in use: **fglrx_pci**
	Kernel modules: fglrx, radeon
```

it would be weird to be the drivers. What could be changed from one day to another? :S

---

### Post by JasonSaras on 2011-12-05
also when I do sth on terminal (installing a package or sth) it would be printed without a reason:

```
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c00593 (jason@ubun)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

and the terminal needs ctrl+C to be activated.

---

### Post by stinkeye on 2011-12-05
> **JasonSaras said:**
> ```
jason@ubuntu:~$ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 144a
	Kernel driver in use: i915
	Kernel modules: i915
--
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
	Subsystem: Hewlett-Packard Company Device 144a
	Kernel driver in use: **fglrx_pci**
	Kernel modules: fglrx, radeon
```

it would be weird to be the drivers. What could be changed from one day to another? :S

Don't know but if you have the unity panel and launcher but metacity is
your window manager you are being dropped to unity 2d.
Not really familiar with ATI driver issues.
Is this an upgrade or fresh install?

You can try setting compiz back to defaults.
I would log into the Ubuntu 2d session (as shown in previous post)
From there you can set compiz back to defaults with...
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```

Then try log into Ubuntu session.

---

### Post by jodiaq on 2011-12-05
> **stinkeye said:**
> 
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```Then try log into Ubuntu session.
that one helped me............
it removed compiz and used metacity(though i logged in ubuntu2d)
```
jodiaq@jodiaq-nl:~$ lspci -k | grep -A3 VGA
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 83a4
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nouveau, nvidiafb

```
Above is given when i tried lspci.
But ccsm is messing things around. Isn't any way to use it safely.

---

### Post by stinkeye on 2011-12-05
> **jodiaq said:**
> that one helped me............
it removed compiz and used metacity(though i logged in ubuntu2d)

But ccsm is messing things around. Isn't any way to use it safely.
The ubuntu 2d session uses metacity as a fallback if you can't run compiz.
Do yo get compiz when you log back into the ubuntu session.

---

### Post by jodiaq on 2011-12-10
yeah i got. But it is messy only. As i logged in everything appears but after opening one or another windows every thing goes blank. And nothing is visible. Only thing i can do is force restart.

---

### Post by jodiaq on 2011-12-12
one more question is 512mb 32bit graphics card is insufficient... I tried water drops effects using ccsm. it was really slow. waves are not continuous they struck every time.

---

### Post by jodiaq on 2011-12-12
One more thing. when i tried water drops effect using ccsm it was discontinuous. waves were stopping and starting. 
is 512 mb 32bit graphics card insufficient??
or any problem with the settings.

---

