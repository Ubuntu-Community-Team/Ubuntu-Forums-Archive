---
title: "Compiz grid not working"
date: 2012-06-18
forum: General Help
---

### Post by Anteino on 2012-06-18
Hi all,

today I tried what "sudo chmod 754" does to the system.. After reinstalling I couldn´t get some functions to work. One was the grid function from Compiz. Before the crash I had it perfectly working and don´t remember doing anything to achieve that. Now when I drag a window to a side of the screen nothing will happen. I visited like 50 links on google describing what to do. But all of them are about writing scripts and downloading stuff from sources I don´t trust. The main idea was starting ccsm with a terminal and next scroll to window preferences and checking "grid". I even opened grid to check if the function was on in the menu: edges > resize actions. All of them were default like when dragging to left edge resize to left side of the screen. But when I then close CCSM nothing will happen when I drag windows all over the screen trying every edge. This really got me frustrated because I love this function so much for its time efficiency. I just want it to work like it did the last two days..

Please advise me on this.

---

### Post by Anteino on 2012-06-19
Bump.

---

### Post by stinkeye on 2012-06-20
Possibly your being logged in to the **ubuntu 2d** session where compiz isn't the window manager but has the same appearance.
Terminal...
```
echo $DESKTOP_SESSION
```
With some gfx cards you will be dropped back to the 2d session if you don't have the necessary drivers.

If you are in the **ubuntu 2d** session, enter additional drivers in the dash 
and see if there are any gfx drivers available.

---

### Post by Anteino on 2012-06-20
When I perform the echo @DESKTOP_SESSION command an empty line will appear :S 

> **stinkeye said:**
> If you are in the **ubuntu 2d** session, enter additional drivers in the dash 
and see if there are any gfx drivers available.

How do I do that?

---

### Post by stinkeye on 2012-06-20
Copy and paste the command in to the terminal.
eg my output...
```
[COLOR="Olive"]glen@Precise:~$[/COLOR] echo $DESKTOP_SESSION
**ubuntu**
```

To look for drivers hit the Super (windows) key and type in 
additional drivers.

---

### Post by Anteino on 2012-06-20
```
echo $SESSION_DESKTOP
ubuntu-2d
```

This is what it sometimes says, but most of the time the second line will be empty, although I changed the lightdm.conf with 

```
nano /etc/lightdm/lightdm.conf
and then changing the user-session to:
user-session:ubuntu.desktop
```

and save the file and make sure the file has changed, I read somewhere ubuntu.desktop was the parameter for starting the 3d-session. 

I remember coming from an older ubuntu distro last time, I upgraded from 10.04 to 12.04 (yes I skipped 11.04 because I needed windows for some school related stuff and didn´t find the time to test 11.04, anyway) and I also remember reading something about videocard drivers, they must have been installed automatically in 10.04. Now, I don´t know how to install the correct driver anymore, and I do not even know if this is even the problem here.

---

### Post by stinkeye on 2012-06-20
You just choose session at the login screen.
If you choose ubuntu at the login screen but are being dropped back to ubuntu 2d, check for drivers as stated before.

Run this  for unity/compiz support.
```
/usr/lib/nux/unity_support_test -p
```
eg my output
```
glen@Precise:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 302.17

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

For gfx info and driver in use run...
```
sudo lshw -c video
```
eg
```
glen@Precise:~$ sudo lshw -c video
[sudo] password for glen: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Magenta"]driver=nvidia[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```

---

### Post by Anteino on 2012-06-21
> **stinkeye said:**
> You just choose session at the login screen.
If you choose ubuntu at the login screen but are being dropped back to ubuntu 2d, check for drivers as stated before.

Run this  for unity/compiz support.
```
/usr/lib/nux/unity_support_test -p
```
eg my output
```
glen@Precise:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 302.17

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

For gfx info and driver in use run...
```
sudo lshw -c video
```
eg
```
glen@Precise:~$ sudo lshw -c video
[sudo] password for glen: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Magenta"]driver=nvidia[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```

I'm new to ubuntu, seriously, you could say I'm really stupid. At the login session there is just the field for me where I give in my password. What do I do to manually choose my login session. Also: ```
Error: GLX is not available on the system
```

---

### Post by stinkeye on 2012-06-21
Have you checked for additional drivers?

See pic to choose session.
[ATTACH]220056[/ATTACH]
Select the **ubuntu** session.
After logging in, check your session in the terminal...
```
echo $DESKTOP_SESSION
```

If it outputs **ubuntu 2d**, check for additional drivers.


Also post the output of this terminal command...
```
sudo lshw -c video
```
When posting the output use the code button '#'
eg
[CODE ] [COLOR="Magenta"]copy and paste here[/COLOR] [/ CODE]
[ATTACH]220058[/ATTACH]

---

### Post by Anteino on 2012-06-22
Allright, I didn about the login session thing. Thank you for that!
I could choose between these two:

ubuntu-2d
ubuntu

I chose ubuntu, but when I then put echo $SESSION_DESKTOP I just get an empty line back :s

Then, the sudo lshw -c video command gave me this output: ```
anteino@s116561:~$ sudo lshw -c video
[sudo] password for anteino: 
  *-display               
       description: VGA compatible controller
       product: GF108 [Quadro 1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:54 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:6000(size=64)
```

I knew about the NVIDIA Quadro 1000M and I fount a driver. First I get the error message "you appear to be running an X server", I found out that one can stop this by going to init 3 mode and "service lightdm stop". This will stop your graphical interface and take you to a full screen terminal. Then I get the error the driver can find any precompiled kernels or codes. I found in the readme from NVIDIA you have to save the kernel code used to compile your system somewhere on the system. I chose the same directory as where the driver is, but I still get that error. How to proceed?

[EDIT] When I check for additional drivers, none will be found, while they WERE found on my previous version of ubuntu on this same computer (ubuntu 10.4). I'm running ubuntu 12.04 LTS now.

---

### Post by stinkeye on 2012-06-22
> **Anteino said:**
> 
I chose ubuntu, but when I then put **echo $SESSION_DESKTOP** I just get an empty line back :s


The correct code is
```
echo $DESKTOP_SESSION
``` 

Unfortunately I'm not an expert on video driver issues.
It may be as simple as disabling nvidia optimus in the bios.

You said you installed a driver. How?
On a fresh install, my older nvidia card (GeForce 9400 GT) will log into the **ubuntu** session using the included **nouveau** open source drivers.
I then install the proprietary nvidia drivers through additional drivers.

I suggest you start a new thread about installing drivers with **GF108 [Quadro 1000M]** in the title,
giving the output of these 2 commands.
```
sudo lshw -c video
/usr/lib/nux/unity_support_test -p
```

---

### Post by Anteino on 2012-06-22
Thanks man I will. But thank you so far :)

---

