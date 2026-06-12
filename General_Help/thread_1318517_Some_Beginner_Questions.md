---
title: "Some Beginner Questions"
date: 2009-11-07
forum: General Help
---

### Post by lovemylady on 2009-11-07
Hey,


first of all Id like to know how to change the keyboard layout?
Eg to german layout (of course i installed it in german)
But it still seems to use the american layout cause y=z and z=y the !£()"!$(/ etc are located at the wrong keys etc.. T.T

my second problem is the resolution..

it gave me 1680x1200 or something like that.. this resolution is too big i would like to use 1024x 800 or so.. but i cant figure out how to..
when i click on systemconfiguration and then on this thing where you ehm should be able to handle this i got no other possibilities than 1680x...
It says my monitor is a "LVDS"  and then i saw in programms/system/ ah programm wich might be called monitorsizeing etc.. blabla in english (KRANDRTRAY)


jup i think thats it for now.. ;)

---

### Post by wieman01 on 2009-11-07
Servus!

As for the first question, you would go to...

System Settings->Regional & Language->Keyboard Layout

...and add languages as you prefer. Not sure about the 2nd question though.

---

### Post by SuperSonic4 on 2009-11-07
If you're getting the £ key you may have the British keyboard installed (which is fixed as above)

For the second question what video card do you have [manufacturer will do] and can you post the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by lovemylady on 2009-11-07
Wonderfull  atleast the I can type corrently now. ***Thanks***

Now there is still the 2nd problem perhaps somebody else got an idea

Perhaps I needa tell that i got a dual notebook Winvista / Kubuntu.

The actual resolution is really ..shice  ..

I'm already happy that the widescreen etc. is working perfect, since i read couple people here got problems with that ^^ 


(perhaps you can help me with that too

**Third question**:

Does somebody knows a tool that shows my battery status?!

**4th question**:

For example on windows i got a configuration of my power modes for example Hardcore CPU using/normal mode/ battery saving..

Does that inflict kubuntu also?
I mean when i configured it for example battery saving (20% of the cpu's will be used), then kubuntu will also only use 20% or the whole available hardware? (well difficult question) since I have no idea if that will be saved in the bios or w/e ^^ ..

okay enough for now my biggest problem is still the resolution..




1 Moment I will look at 
/etc/X11/xorg.conf

---

### Post by lovemylady on 2009-11-07
> **SuperSonic4 said:**
> If you're getting the £ key you may have the British keyboard installed (which is fixed as above)

For the second question what video card do you have [manufacturer will do] and can you post the output of ```
cat /etc/X11/xorg.conf
```



***Sorry but it seems i got no such file.***


[IMG]http://www2.pic-upload.de/07.11.09/pa42gnektxt7.png[/IMG]

---

### Post by SuperSonic4 on 2009-11-07
3. **acpi** is a package that can tell you stuff like power and temperature on a laptop. **laptop-mode-tools** is some kernel mods for laptops (although I don't know if it's in kubuntu because I use arch) ```
sudo apt-get install acpi
``` ```
sudo apt-get install laptop-mode-tools
```

4. Powerdevil should already be installed. On my system it is found in ```
System Settings --> Advanced (tab) --> Power Management
```

No idea if it will throttle your laptop's consumption since I'm on a desktop.


-------------

OK, not to worry, I think karmic done away with it. What graphics card do you have? To find out issue ```
lspci | grep VGA
```

---

### Post by lovemylady on 2009-11-07
sudo apt-get install laptop-mode-toolsIs up do date ;)


sudo apt-get install acpi
Here this comes:
julietta @ ubuntu: ~ $ sudo apt-get install acpi  
 Reading package lists ... Finish  
 Dependency Tree  
 Read status information, a ... Finish  
 Package acpi is not available, but from another  
 Package referenced. This may mean that the package is missing, that obsolete  
 or just from another source is available.  
 E: Package acpi has no installation candidate  


I guess i needa download it manually somewhere



Edit:

julietta@ubuntu:~$ lspci | grep VGA
08:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)

---

### Post by wieman01 on 2009-11-07
Battery status? Don't you have the power management widget installed by default? I got it and it works wonderfully well.

---

### Post by SuperSonic4 on 2009-11-07
That could be due to any number of things. You could try enabling universe and backport repos if you haven't already or if it's a very fresh install an update may work ```
sudo apt-get update
```

OK, you have an nvidia card which is good news :p. Unless you want only free [as in speech software] you may be able to get the **nv** driver via KPackageKit. If you don't mind non-free software then I'd install the nvidia drivers via Hardware Drivers/KPackagekit

If you install the non-free driver then next install nvidia-settings: ```
sudo apt-get install nvidia-settings
``` and launch it as root ```
kdesu nvidia-settings
``` and hopefully you can pick your resolution from there

---

### Post by lovemylady on 2009-11-07
Let's give it a try I'll try to handle this now ;)

& Yep it's a fresh install I just installed it ~2 hours ago and yea.. :p


Ps.: Any suggestion for a Anti-Virus, is there even one for linux?


Pss.: I'll write it down later, since i got UMTS downloads always may take a bit =P


Edit:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

How to run nvidia-xconfig as root?

ps by me it is without kdesu just "sudo nvidia-settings"



__

julietta@ubuntu:~$ sudo nvidia-xconfig
[sudo] password for julietta:
sudo: nvidia-xconfig: command not found
julietta@ubuntu:~$

---

### Post by SuperSonic4 on 2009-11-07
> **lovemylady said:**
> Let's give it a try I'll try to handle this now ;)

& Yep it's a fresh install I just installed it ~2 hours ago and yea.. :p

Wilkommen :p. I like KDE :D

> 
Ps.: Any suggestion for a Anti-Virus, is there even one for linux?

Not necessary - Linux's obscurity and permissions don't need it. Just be aware it does not protect against phishing et al


> Pss.: I'll write it down later, since i got UMTS downloads always may take a bit =P

Fair enough (no idea what UMTS is)




> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

How to run nvidia-xconfig as root?

ps by me it is without kdesu just "sudo nvidia-settings"

Did you install the nvidia driver before running nvidia-settings? kdesu is the proper way of launching GUI apps as root in KDE but sudo does work for some cases

---

### Post by lovemylady on 2009-11-07
ehm, you didn't tell me anything about installing nvidia drivers >.<
Everything is so complicated :D

UMTS/GRPS/HSDPA/EDGE = Wireless internet.. some stick you put in your notebook/pc an you have internet everywhere.. park,city,forest or where ever ^^

---

### Post by hal10000 on 2009-11-07
> I guess i needa download it manually somewhere

No, you just need to activate some software repositories
**K-Menü--->Programme--->System--->Software-Quellen**

tick main, restricted, universe and multiverse
then, on a command line do
```
sudo apt-get update
sudo apt-get install acpi acpid acpi-support laptop-mode-tools jockey-kde

```

You have a nvidia card, you can install the 3D accelerated driers with
```
 kdesudo jockey-kde
```

---

### Post by lovemylady on 2009-11-07
Could you tell me what you meant with "**Software-Quellen" **in english?

Cause I didn't find such a "topic"

I got Datamanager "dolphin"
and Softwaremanager "Kpackagekit" wich you could have meant?

---

### Post by wieman01 on 2009-11-07
Software-Quellen = Repositories?

---

### Post by lovemylady on 2009-11-07
Ok that didn't help me either xD 

But i think those things are already activated when I used

Sudo apt-get update
I got

> OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-de
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-de
OK   [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Translation-de [412kB]
;)

---

### Post by hackerlife on 2009-11-08
I think what they mean by 
K-Menü--->Programme--->System--->Software-Quellen
in english would be
Menu > System > Administration > Hardware drivers

Or at least that is how you would activate the "non-free" (proprietary) drivers

Edit:
I just realized that this might make no sense. 
I don't think "software -Quellen" could possibly equal "HARDWARE - drivers" in English lol.

---

### Post by lovemylady on 2009-11-08
> **hackerlife said:**
> I think what they mean by 
K-Menü--->Programme--->System--->Software-Quellen
in english would be
Menu > System > Administration > Hardware drivers

Or at least that is how you would activate the "non-free" (proprietary) drivers

Edit:
I just realized that this might make no sense. 
I don't think "software -Quellen" could possibly equal "HARDWARE - drivers" in English lol.


Well "hal" solved it.. everything is fine now ;)

But do I still need this Nvidia X-config or X-server or however its called again, if not how to uninstall/delete it?!

---

### Post by SuperSonic4 on 2009-11-08
I find it easiest to configure resolution using nvidia-settings but I still use an xorg.conf file so it goes beyond my expertise now

---

### Post by hal10000 on 2009-11-08
@hackerlife: 

> Edit:
I just realized that this might make no sense.
I don't think "software -Quellen" could possibly equal "HARDWARE - drivers" in English lol.

"software -Quellen" is equal to repositories

---

### Post by lovemylady on 2009-11-08
But there ain't a Topic called "repositories" :p

Anyway everything is fine since long now ;)

---

### Post by hal10000 on 2009-11-08
> But there ain't a Topic called "repositories"

I wonder that you don't have a menu entry for managing your software repositories.

But does'nt matter if you use synaptic as your package manager. It can do this job too.

---

