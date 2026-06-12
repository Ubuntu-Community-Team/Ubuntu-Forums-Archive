---
title: "Dual monitors in maverick"
date: 2010-10-12
forum: General Help
---

### Post by le-foot on 2010-10-12
Hi,

Does anyone know of problems where 10.10 doesn't recognise more than one monitor? I've got nVidia 8500GT and I have the 'recommended' proprietary driver installed. I upgraded from 10.04, and dual monitor was working -> restarted -> dual monitor not working.

Cheers

---

### Post by Rittsel on 2010-10-12
Same problem here just after updating from 10.04 to 10.10 today.

I'm using Dell D430 laptop.
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

The second monitor is activated but it's like the resolution is wrong. I can see the mouse on my second monitor but just on the edge of the monitor. Can't move it around on that screen.

I just noticed that screenshot tool doesn't detect the second display as well.

I've changed back and forth between the monitors in System > Preferences > Monitors.

They all detect, and all have the correct resolution, i can use one at a time and both work well.


xrandr -q
```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       59.8 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
TV1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by Antimethod on 2010-10-12
Same here, I have an Intel Corporation Mobile 945GM and it recognizes the second monitor, but fails to set the proper resolution.

---

### Post by Antimethod on 2010-10-12
I found a solution for this.
The bug seems to have been known for a while now, but the fix has not been included in the final release of Ubuntu Maverick(10.10).

Here's the link to the bug:
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663)

In the bug comments I have found that installing the "xorg-edgers" fixes the problem.
So all you have to do is install the ppa from xorg-edgers and update the packages.
The link for the "xorg-edgers" ppa page:
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)


[noparse]sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
Logout or restart and everything should work fine.[/noparse]

---

### Post by Rittsel on 2010-10-12
Confirming ppa, works like a charm.

But i don't like the idea running bleeding edge just because of this bug.

---

### Post by ean5533 on 2010-10-12
> **Rittsel said:**
> Confirming ppa, works like a charm.

But i don't like the idea running bleeding edge just because of this bug.

Without trying to be rude, I don't think you have much of a choice. The bug fix hasn't been merged into stable yet. Either you run bleeding edge, or you're stuck with the bug. Your decision.

---

### Post by messner on 2010-10-15
I have also the same problem. I have one external monitor attached to my notebook. When I want to use only the external monitor, the screen gets distorted ...

I have installed your upgrade and the problem is still the same ;(

Any help ?

--------------------------------
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
--------------------------------
xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1920x1200      60.0 +
   1600x1200      60.0  
   1680x1050      60.0* 
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050      60.7*+   60.0  
   1600x1024      60.2  
   1400x1050      60.0     60.0  
   1280x1024      59.9     60.0  
   1440x900       59.9     59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   840x525       120.0    119.8  
   800x512       120.3  
   848x480        59.7  
   700x525       120.0  
   720x480        59.7  
   640x512       120.0  
   720x450       119.8  
   640x480       120.0     59.9     59.4  
   680x384       119.6    119.9  
   576x432       120.1  
   512x384       120.0  
   400x300       120.6  
   320x240       120.1  
S-video disconnected (normal left inverted right x axis y axis)

---

### Post by jvpgomes on 2010-10-16
Please check the last comments in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663)

But summarily:
the problem is solved, select the maverick-proposed repository and update the system.

---

### Post by dunwich42 on 2010-10-19
That worked for me. 
I enabled maverick-proposed updated only the appropriate update & then disabled proposed.

---

### Post by atozer on 2010-10-19
I am on a eee 1000H with res 1024x600 60Hz and an extended Acer 23" at 1920x1080 60Hz. In maverick netbook I cannot 
run both resolutions simultaneously. Configuring extended desktop allows a max res of 1024x800 on the acer monitor, 
however running only the Acer monitor I get 1920x1080. 
I performed;
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
and restarted,

I also followed [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) to enable maverick-proposed updates and ran an update but there weren't any updates.

Anyone else running dual monitors exended @ 1024x600 and 1920x1080?

---

### Post by gyterpena on 2010-10-19
Tried maverick-proposed and it failed miserably. Now I have windows darkened with some sort of shadow and if I right click sometimes secondary menus are displayed under the main window all I can see is dark square. Going back to 10.04.1
This is on GMA945

---

### Post by scottyab on 2010-10-25
Still struggling with this, trying to run dual 22" at 1650x1050, in ubuntu 10.10 (was fine in 10.04)

Tried as suggested:
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
and restarted,
Then enabled maverick-proposed updates [via update manager]
Ran system update, updated and restarted.  

I still don't get the option in monitors to select higher resolution than 1400x1050 and it always sets to mirror screens. (even if i select option, system requests log off/on)

Anyone else upgraded to ppa:xorg-edgers/ppa and it not fix the issue?

---

### Post by Dropperbr on 2010-10-25
Had the same problem but solved on Nvidia Display properties. Now my problem is firefox when I try to make a video full screen on second monitor, it fullscreen but on main monitor.

---

### Post by sjatkins on 2010-11-10
> **ean5533 said:**
> Without trying to be rude, I don't think you have much of a choice. The bug fix hasn't been merged into stable yet. Either you run bleeding edge, or you're stuck with the bug. Your decision.

Well, I am very pleased it has a fix.  However, pulling so much stuff for one simple problem certainly seems a tad suboptimal.  Does some hack to the proper config files also get us back to dual monitors.  Or is it really so deep as to require all of this stuff (which would amaze me).

---

### Post by sjatkins on 2010-11-10
> **sjatkins said:**
> Well, I am very pleased it has a fix.  However, pulling so much stuff for one simple problem certainly seems a tad suboptimal.  Does some hack to the proper config files also get us back to dual monitors.  Or is it really so deep as to require all of this stuff (which would amaze me).

Not pleased. The suggested fix does not fix it.  I am on a Dell tower with Radeon 4870 graphics card.  Everything was fine with my dual 1920x1200 monitors in 10.04.  In 10.10 the Preference->Monitors tool appears to never change whatever files it is meant to change.  If I open it, change out of mirror mode. Apply and close it, and then open it again it still says mirror mode.  Logging out as it suggests with or without closing the Monitors screen doesn't change it.  Rebooting doesn't help.  So how the heck do I get non-mirrored monitors back?

I think it really is as simple as the right config files not being written but I am not enough of a linux guru to validate that.  Just a hunch from the behavior.

---

### Post by netopalis45 on 2011-01-23
just tried this and it didnt work. it also somehow broke compiz and i cant figure out how to fix it even after reinstalling. help?

---

### Post by parovelb on 2011-01-28
I run maverick on a Dell D400 with an intel integrated video card (VGA out). Before upgrading and updating it was working extremely well. Detection of the external monitor was working too. Now, I don't get the option in monitors to select higher or different resolution when pluggin onto a LG flat screen TV.

The suggested solution below:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```resulted a total meltdown of the xserver! It took me the whole day for resetting to a previous configuration.  

xrandr result:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 

```and lspci result:
```
parovelb@parovelb-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```

Any ideas?

---

### Post by uniquegeek on 2011-03-12
First rule: check layer 1.  D'oh.

My cable was partially unplugged.

---

### Post by beercz on 2011-03-13
I'm having a problem with dual monitors in my Dell 3100 desktop with the following display adapters installed:

```
lspci | grep VGA
```Output from the above command:

> 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
03:01.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)In the PC's BIOS if I set the primary display to either adapter, I can see Ubuntu as normal.  Therefore I assume I have all the necessary drivers installed and working correctly.

But the problem I have, regardless of which graphics adapter I use as the computer's primary display, I am unable to get the dual monitor feature working.

When I do System->Preferences->Monitors, only the current monitor is displayed.  I click the 'Detect monitors' button, but the secondary display is not found.

I have spent the last three hours trying to find a solution for this to no avail.

Can anyone help me?

Thanks in advance.

---

### Post by Pathagoras on 2011-04-04
I found a solution for the average user that seems to work well.
 
In my /etc/X11 file, I did not find any xconfig file, which was the first method I attempted. I agree with using the xrandr method, however, I highly suggest installing the arandr graphical interface for the program. I did the following steps, and I hope it will work for you too!!
 
1. Open the synaptic package manager (>system>synaptic package manager)
 
2. Type "arandr" into the search box
 
3. Check "mark for installation" on the package
 
4. Once completed, ArandR will appear in >settings>Arandr from your start menu
 
5. Open Arandr, which should recognize both the monitors, but they will probably appear overlapped. Grab one of the monitors and move it to the side. This is where you can configure each monitor (right click) for resolution, height position, etc.
 
6. Once you have it set the way you would like, click the "save" button on the top. Name it something you will remember, and take note where the profile is saved. This will be a **.sh file, where ** is the name you give the script.
 
7. Open >Ubuntu Settings Manager>System and Startup. Click to add a command, and locate the script you just created using Arandr. I called mine "Monitor Settings"
 
8. Save and restart the computer. It should load the script for using the two monitors.
 
Although I was able to get this working, I have yet to resolve several issues.
 
1. COMPIZ does not play nice with the dual monitor setup. I only get functionality of about 60% of the secondary monitor, and wierd artifacts abound.
 
2. I can't get the second monitor to have a specific wallpaper. It just shows the stock "Ubuntu 10.10" wallpaper.
 
I hope this works for you. Since this is not a driver manipulation, it should work with both ATI and NVidia chipsets (I am using ATI). I have one monitor on VGA and the other on DVI. They appeared as such in Arandr.
 
If you have a solution for COMPIZ and wallpaper, please reply!

---

