---
title: "Steam wont launch games, certain .exe files wont launch"
date: 2011-05-22
forum: General Help
---

### Post by JadeTigerVG on 2011-05-22
I have downloaded Dwarfs Demo on Steam, when I go to launch it the "preparing to launch..." window pops up, then nothing. I could wait all day, and the game will not launch

Also, I have tried launching a .exe file through the terminal. This is the message I get

```
****@****-Extensa-5630:~$ wine '/home/****/Desktop/terrariaretail/Terraria.exe' 
WARNING: The runtime version supported by this application is unavailable.
Using default runtime: v1.1.4322

** (Terraria.exe:8): WARNING **: The following assembly referenced from Z:\home\****\Desktop\terrariaretail\Terraria.exe could not be loaded:
     Assembly:   Microsoft.Xna.Framework.Game    (assemblyref_index=1)
     Version:    4.0.0.0
     Public Key: 842cf8be1de50553
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (Z:\home\brandi\Desktop\terrariaretail\).


** (Terraria.exe:8): WARNING **: Could not load file or assembly 'Microsoft.Xna.Framework.Game, Version=4.0.0.0, Culture=neutral, PublicKeyToken=842cf8be1de50553' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.Xna.Framework.Game, Version=4.0.0.0, Culture=neutral, PublicKeyToken=842cf8be1de50553' or one of its dependencies.
File name: "Microsoft.Xna.Framework.Game, Version=4.0.0.0, Culture=neutral, PublicKeyToken=842cf8be1de50553"

```These appear to be windows errors, and I have no idea where to go from here

---

### Post by JadeTigerVG on 2011-05-22
Hello? Anybody alive? I'd understand if there were few replies if this were a less visited forum site, but this place is highly active

---

### Post by linuxinstalledfromhdd on 2011-05-22
Did you install Steam with PlayOnLinux or did you install it some other method into Wine?

---

### Post by JadeTigerVG on 2011-05-22
I installed it using WineTricks

---

### Post by linuxinstalledfromhdd on 2011-05-22
Try this method:

[http://cinderbox.net/2011/05/02/how-to-install-steam-in-ubuntu-11-04-a-game-distribution-platform/](http://cinderbox.net/2011/05/02/how-to-install-steam-in-ubuntu-11-04-a-game-distribution-platform/)

---

### Post by JadeTigerVG on 2011-05-22
I haven't got 11.04 yet, still on 10.11 Will it still work?

---

### Post by linuxinstalledfromhdd on 2011-05-22
PlayOnLinux doesn't have a Natty repo yet.  It's all just Maverick for now, so good ahead and proceed. I'll stand by.

---

### Post by JadeTigerVG on 2011-05-23
I got as far as the 3rd line in the terminal, and got this err

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I dont have any instances of wine open

---

### Post by linuxinstalledfromhdd on 2011-05-23
Restart your system. 

Navigate back to the walkthrough I posted. 

You shouldn't have a problem.

I'll be standing by.

---

### Post by katykat on 2011-05-23
Its not wine that gave you that error. 

You cannot run more than one instance of apt-get, or run apt-get with Synaptic or aptitude in the background.

One package at a time.....

---

### Post by linuxinstalledfromhdd on 2011-05-23
That's why I had them simply restart their system instead.  And then follow the walkthrough to install PlayOnLinux.

---

### Post by JadeTigerVG on 2011-05-23
Well, my computer crashed when I restarted. I have no idea why. I texted someone and told them to tell you guys what had happened. It appears they didn't. They're getting an earful next time I see them...

At any rate, the crash. I restarted the computer, and it turned back on with 6 different start-up choices. The first four gave me the same end-lines

mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys
mount: mounting /proc

Targested filesystem doesn't have requested /sbin/init. 
No init found. 
Try passing init= bootarg

The last 2 start-up options give me a blue screen of death with data on it, not sure what it means

The start-up options are called

Ubuntu, with linux 2.6.35-28-generic
Ubuntu, with linux 2.6.35-28-generic (recovery mode)
Ubuntu, with linux 2.6.35-22-generic
Ubuntu, with linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial consol 115200)

---

### Post by JadeTigerVG on 2011-05-23
Next time will you tell me why I need to restart or do something? That way, if something goes wrong and I can't contact the forum again, I'll have somewhere to go off from, and maybe know why my computer did what it did.

---

### Post by JadeTigerVG on 2011-05-23
Hello? Again, idleness on a highly active forum board...

---

### Post by JadeTigerVG on 2011-05-24
I feel abandoned, doesn't anybody know whats going on?

---

### Post by JadeTigerVG on 2011-05-24
Thanks for all the help. Found out from an outside source that this was a direct kernel error. I'm getting an operating system disc to fix it. I love the sense of community and helpfulness you've shown. I'm going to wipe my drive and reinstall steam, wurm, terraria, minecraft, and whatever, the proper way. I'll start a new thread if I run into more problems.

---

