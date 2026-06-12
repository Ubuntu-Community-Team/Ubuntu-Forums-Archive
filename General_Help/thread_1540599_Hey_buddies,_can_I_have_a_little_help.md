---
title: "Hey buddies, can I have a little help?"
date: 2010-07-28
forum: General Help
---

### Post by Mr Mouse on 2010-07-28
Im kinda new on the Linux scene and I'm having some problems that I don't know how to solve.

I'm trying to run a "Habbo Hotel" game server on Ubuntu, it's an executable windows file, I tried with Wine, but it asked me for Mono (just because its a .NET based program), it's ok.

But now when I try to run the .exe with Mono im having theese messages:

[b]root@root:/var/www/vhosts/jj14.us/habbo/emulador_habbo# mono PrimusEMU.exe
WARNING: The runtime version supported by this application is unavailable.
Using default runtime: v1.1.4322

** (PrimusEMU.exe:21825): WARNING **: The class System.Collections.Generic.KeyNotFoundException could not be loaded, used in mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

** (PrimusEMU.exe:21825): WARNING **: The class System.ConsoleKeyInfo could not be loaded, used in mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'System.ConsoleKeyInfo' from assembly 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.[/b]


I really don't know what to do, can you guys help me?

Best regards,
Mr. Mouse

---

### Post by dino99 on 2010-07-28
on linux you need to install wine (from winehq) to run .exe progs

goto synaptic repo tab and add this ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

then update, upgrade

to run any exe file, only double-click it to make the installation under wine, that it

---

### Post by Mr Mouse on 2010-07-28
> **dino99 said:**
> on linux you need to install wine (from winehq) to run .exe progs

goto synaptic repo tab and add this ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

then update, upgrade

to run any exe file, only double-click it to make the installation under wine, that it

It's a Ubuntu Server, and I have already tried Wine :(
But in my case I'll have to use Mono, because it's a .NET based application.

---

### Post by dino99 on 2010-07-28
mono works with wine: see winetricks into a console: sh winetricks

---

### Post by Mr Mouse on 2010-07-28
> **dino99 said:**
> mono works with wine: see winetricks into a console: sh winetricks

root@root:~# sh winetricks
sh: Can't open winetricks

---

### Post by Mr Mouse on 2010-07-28
No? :(

---

### Post by Mr Mouse on 2010-07-28
Please?

---

### Post by Mr Mouse on 2010-07-28
:(

---

### Post by slooksterpsv on 2010-07-28
sh ./winetricks

You'll have to download it first, so type in:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Then type in:

sh ./winetricks mono26

I think its mono26 you want... I could be wrong.

---

### Post by Mr Mouse on 2010-07-28
> **slooksterpsv said:**
> sh ./winetricks

You'll have to download it first, so type in:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Then type in:

sh ./winetricks mono26

I think its mono26 you want... I could be wrong.

root@jj14:~# sh ./winetricks mono26
Executing wine /root/.winetrickscache/mono-2.6.4-gtksharp-2.12.10-win32-3.exe
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 21/02/2010, dlt (d/m/y): 17/10/2010
fixme:reg:GetNativeSystemInfo (0x33fe40) using GetSystemInfo()
fixme:msg:ChangeWindowMessageFilter c03d 00000001
fixme:win:DisableProcessWindowsGhosting : stub
------------------------------------------------------
Note: command 'wine /root/.winetrickscache/mono-2.6.4-gtksharp-2.12.10-win32-3.exe' returned status 1.  Aborting.
------------------------------------------------------

---

### Post by oldos2er on 2010-07-28
I don't know anything about Mono or .NET, but this error, "Make sure that your X server is running and that $DISPLAY is set correctly" is telling you mono-2.6.4-gtksharp-2.12.10-win32-3.exe expects to be run in a graphical environment, specifically Gnome (hence the "gtk"). At a minimum you will need to install ubuntu-desktop and xserver-xorg-core.

---

### Post by Mr Mouse on 2010-07-29
> **oldos2er said:**
> I don't know anything about Mono or .NET, but this error, "Make sure that your X server is running and that $DISPLAY is set correctly" is telling you mono-2.6.4-gtksharp-2.12.10-win32-3.exe expects to be run in a graphical environment, specifically Gnome (hence the "gtk"). At a minimum you will need to install ubuntu-desktop and xserver-xorg-core.


root@jj14:~# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.




root@jj14:~# apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xorg-core is already the newest version.
xserver-xorg-core set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.




And again, when I try the sh ./winetricks mono26 I'm having the same error.

---

### Post by slooksterpsv on 2010-07-29
Is GDM running (Gnome Display Manager)? Pretty much you have to be in the graphical UI before you can install mono26.

---

### Post by Mr Mouse on 2010-07-29
I don't know, how can I install this GDM?

I'm doing everything via SSH.

---

### Post by slooksterpsv on 2010-07-29
> **Mr Mouse said:**
> I don't know, how can I install this GDM?

I'm doing everything via SSH.

That's the issue then, the installer is GUI based so you need to vnc into the computer. Ubuntu-desktop should have included GDM.

Do you have a Linux Desktop computer? If so there's a way to pipe the display through SSH; it was a long time ago that I did it, but it's possible.

---

### Post by Mr Mouse on 2010-07-29
> **slooksterpsv said:**
> That's the issue then, the installer is GUI based so you need to vnc into the computer. Ubuntu-desktop should have included GDM.

Do you have a Linux Desktop computer? If so there's a way to pipe the display through SSH; it was a long time ago that I did it, but it's possible.

No :(
Actually I'm using Windows, I don't have any Linux at home.

---

### Post by slooksterpsv on 2010-07-29
> **Mr Mouse said:**
> No :(
Actually I'm using Windows, I don't have any Linux at home.

VNC Server and Client is going to be the easiest.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

TightVNC is a good one for Windows.

---

### Post by Mr Mouse on 2010-07-29
> **slooksterpsv said:**
> VNC Server and Client is going to be the easiest.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

TightVNC is a good one for Windows.

Ok, I'm connected.

Now where's mono26?


[IMG]http://i28.tinypic.com/34jaslu.png[/IMG]

---

### Post by slooksterpsv on 2010-07-29
open a terminal, navigate to the folder and run:
sudo ./winetricks mono26

---

### Post by Mr Mouse on 2010-07-29
> **slooksterpsv said:**
> open a terminal, navigate to the folder and run:
sudo ./winetricks mono26

Ok, Mono26 installed.

But now how do I run the app? I can't find it :oops:](*,)

---

### Post by slooksterpsv on 2010-07-29
> **Mr Mouse said:**
> Ok, Mono26 installed.

But now how do I run the app? I can't find it :oops:](*,)

Is it an app on a cdrom? Did you download it? And what application?

---

### Post by Mr Mouse on 2010-07-29
> **slooksterpsv said:**
> Is it an app on a cdrom? Did you download it? And what application?

I need to run a .exe with Mono26, how should I do it?

---

### Post by sarloth on 2010-07-29
Assuming you have WINE installed, all you need to do is run the .exe. WINE should take over and do the rest.

---

### Post by Mr Mouse on 2010-07-29
Again, on Terminal:



[email]root@jj14:/var/www/vhosts/jj14.us[/email]/habbo/emulador_habbo# wine PrimusEMU.exe
WARNING: The runtime version supported by this application is unavailable.
Using default runtime: v1.1.4322

** (Z:\var\www\vhosts\jj14.us\habbo\emulador_habbo\PrimusEMU.exe:25): WARNING **: The class System.ConsoleKeyInfo could not be loaded, used in mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'System.ConsoleKeyInfo' from assembly 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.

---

### Post by slooksterpsv on 2010-07-29
Looks like we need mono 2.8 or 3.0 which hasn't been released yet, but it looks like we need .NET 4.0 to run the program.

[http://www.mono-project.com/Roadmap#Upcoming_Releases](http://www.mono-project.com/Roadmap#Upcoming_Releases) - information on upcoming releases.

---

### Post by Mr Mouse on 2010-07-29
> **slooksterpsv said:**
> Looks like we need mono 2.8 or 3.0 which hasn't been released yet, but it looks like we need .NET 4.0 to run the program.

[http://www.mono-project.com/Roadmap#Upcoming_Releases](http://www.mono-project.com/Roadmap#Upcoming_Releases) - information on upcoming releases.

Oh, Game Over :(

But anyway, thanks you guys VERY MUCH, I've learned a lot.
This forum will help me a lot.

---

### Post by slooksterpsv on 2010-07-29
> **Mr Mouse said:**
> Oh, Game Over :(

But anyway, thanks you guys VERY MUCH, I've learned a lot.
This forum will help me a lot.

You're welcome, that's what we're here to do is help people out and obtain help as well. WINE can be tricky, but is rewarding when it works.

---

