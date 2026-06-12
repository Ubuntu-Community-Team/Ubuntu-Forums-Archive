---
title: "Older Xubuntu version for a 10 year old notebook?"
date: 2009-08-24
forum: General Help
---

### Post by Don_Nadie on 2009-08-24
I burned a 9.04 Xubuntu Live CD and when I pressed F1 at the first screen, I saw that the system requirements were 384MB of memory. The old notebook I want to install to doesn't have that much RAM; it's maxed out at 256MB.

I wonder if there's some older version of Xubuntu still available that'll work on the hardware in the following living fossil:
[B]
HP Omnibook XE2-DB[/B]
333 MHz Pentium II
4.6 GB ATAPI hard drive (will use entire drive for Xubuntu)
CD ATAPI drive, can't burn CDs
USB 1.1 port -- I intend to put the bulk of my data on a USB flash pen drive
256 MB RAM (it won't accept any more)
800x600 LCD panel
Silicon Motion LynxE SM 811 video card, 2 MB memory, can do 800x600 24 bit
BIOS will boot from CD but not USB

Or am I totally silly to try to get even an old version of Xubuntu running on this thing? It's just for learning Linux; right now I've got Damn Small Linux frugal-installed on it, but it looks like DSL may be defunct and it's got some things about it that I think aren't common to most other distros.

I'm just starting off with Linux and also have wubi 9.04 on a 3 year old machine that has plenty of resources. It's pretty frustrating trying to learn a new OS, but I'm giving it a try.

Thanks to those in the know who can answer my questions.

---

### Post by DeMus on 2009-08-24
> **Don_Nadie said:**
> I burned a 9.04 Xubuntu Live CD and when I pressed F1 at the first screen, I saw that the system requirements were 384MB of memory. The old notebook I want to install to doesn't have that much RAM; it's maxed out at 256MB.

I wonder if there's some older version of Xubuntu still available that'll work on the hardware in the following living fossil:
[B]
HP Omnibook XE2-DB[/B]
333 MHz Pentium II
4.6 GB ATAPI hard drive (will use entire drive for Xubuntu)
CD ATAPI drive, can't burn CDs
USB 1.1 port -- I intend to put the bulk of my data on a USB flash pen drive
256 MB RAM (it won't accept any more)
800x600 LCD panel
Silicon Motion LynxE SM 811 video card, 2 MB memory, can do 800x600 24 bit
BIOS will boot from CD but not USB

Or am I totally silly to try to get even an old version of Xubuntu running on this thing? It's just for learning Linux; right now I've got Damn Small Linux frugal-installed on it, but it looks like DSL may be defunct and it's got some things about it that I think aren't common to most other distros.

I'm just starting off with Linux and also have wubi 9.04 on a 3 year old machine that has plenty of resources. It's pretty frustrating trying to learn a new OS, but I'm giving it a try.

Thanks to those in the know who can answer my questions.

My laptop is 8 1/2 years young and I installed Puppy-Linux on it. It has a P3-600Mhz processor and 256MB ram.
Works very well. Mind you, it's totally different from Ubuntu, but it's "fast".
Also tried Hardy Xubuntu but that is slow. Painfully slow.

---

### Post by snowpine on 2009-08-24
Hi there, the oldest version of Xubuntu that's still supported is Xubuntu 8.04. That might be worth a try. As far as I know, Xubuntu should work fine with 256mb of ram. You might try the Alternate Install CD (a text based installer for lower ram) if installing from the Live CD doesn't work.

If you are not married to the idea of Xubuntu, I think you'll find there are much "lighter" options available as a middle ground between Xubuntu and DSL. For example: Debian+LXDE, SliTaz, Crunchbang, Puppy, etc.

Good luck!

---

### Post by starcraft.man on 2009-08-24
[Puppy Linux ]("http://www.puppylinux.org/")or [Damn Small Linux]("http://www.damnsmalllinux.org/")
Try puppy first in my opinion.

I don't think that would run any Ubuntu variant quite well. Those two are very compact and lean.

---

### Post by Hogosha on 2009-08-24
i have Xubuntu 9.04 running in a virtual machine with 256MB of ram given to it and i have no issue what so ever with it. It is still zippy enough to make me happy. Give it a shot, what is the worst that could happen with trying.

---

### Post by stoneheart on 2009-09-09
I'd suggest Debian 5 Lenny with the LXDE desktop.  I have this running smoothly on a Pentium III 800 mhz with 256 megs of ram.  I have 1 gig allocated on the HD for a swap file but I suspect that is overkill.

---

### Post by br4d on 2009-09-15
If you are a newbie, like me :confused:. 
Then just install the xubuntu. Then install the fluxbox package.
Fluxbox is absolutely fast and lightweight. 

Before you start with it find a tutorial about fluxbox (save it or print it). Because the first you will see after installing fluxbox is an empty screen and you'll start wondering what to do next. 

On login screen click session and choose fluxbox as window manager.

Open a terminal (right click and find terminal in one of the submenu).

Add fbpanel and fbdesk package  (sudo apt-get install fbpanel fbdesk).

Start fbpanel (brad@mypc:/home/brad$fbpanel&).

From there you should know what to do next. (read the tutorial)

---

### Post by oboedad55 on 2009-09-15
You can try moonos 3. or here is a"puplet" that has more stuff than Puppy, like openoffice,etc. You can get it here: [http://www.puppylinux.org/downloads/puplets/puppy-crypt-42](http://www.puppylinux.org/downloads/puplets/puppy-crypt-42)

---

### Post by kerry_s on 2009-09-15
sounds like you have experience, do a cli install & add light stuff, make it to your needs.

i'm just getting my 10 year old vaio laptop back up & running so i can have something to use, my dad snagged my new rig & left me his 7 year old lemon/brick.
:lolflag: 

in my case i have no choice the only installable cd i have is the 9.04 desktop, i don't have no way to burn something right now.

right now, i'm just messing around seeing how well i can get gnome to work.
i working with 450mhz 256mb ram.

---

### Post by Lisimelis on 2009-09-17
Well my friend I have an old laptop which i use for general surfing and stuff. It has 256Mb Ram and i needed i light distro. I looked around and found MoonOs and was pleasantly surprised by its light and beautiful setting and its easy set up of wireless (its based on ubuntu 9.04). look at my screenshot!!!

---

### Post by kerry_s on 2009-09-17
> **Lisimelis said:**
> Well my friend I have an old laptop which i use for general surfing and stuff. It has 256Mb Ram and i needed i light distro. I looked around and found MoonOs and was pleasantly surprised by its light and beautiful setting and its easy set up of wireless (its based on ubuntu 9.04). look at my screenshot!!!

pretty! enlightment looks like its improved a lot since i last used it some years ago.

i been stripping the heck out of gnome to make it light, i wish i had a burner. :(

---

### Post by kedaha on 2009-12-06
Hello!

If your old HP Omnibook XE2 laptop has 256 RAM you can install Xubuntu 9.10 Karmic Koala from the normal installation CD-ROM. 

I also tried PCLinuxOS XFCE desktop Phoenix 2009 Edition the graphics card (VGA compatible controller: Silicon Motion, Inc. SM710 LynxEM (rev A3) is recognised with 1024x768 resolution and, believe it or not, DESKTOP EFFECTS can be enabled including the rotating Compiz Cube, even though it is a bit slow. It is best not to enable them because it uses a lot of memory and CPU. With PCLinux, as with Xubuntu, the laptop doesn't shut dowm properly so it would be necessary to do a bit of tweaking like adding acpi=force to the kermel options with nano /etc/default/grub (please see Karmic Koala documentation). The soundcard also has to be got working.

With Xubuntu, sound works perfectly but I still haven't found out how to enable a higher screen resolution than the default 800X600. You can watch youtube videos although the frame rate is low. Maybe it would be a good idea to use the LXDE desktop to speed things up a little.

---

### Post by edwardp on 2009-12-06
I switched to the 386 kernel on the desktop system listed below in my signature and it's actually running faster overall, than when the generic kernel was used.  After the desktop appeared, I opened the terminal window and ran "top".  It indicated a total of 211Mb of memory was being used.

With the generic kernel and also with the 386 kernel, it is having a Flash-related audio problem, when audio is playing (e.g. Yahoo Radio or AOL Radio) and a new web page is loading in the browser, the audio cuts out and resumes when the web page has finished loading.  

Aside from this, it's working fine with the 386 kernel, so you might want to give the 386 kernel a try.

---

### Post by deathbyswiftwind on 2009-12-06
> **Lisimelis said:**
> Well my friend I have an old laptop which i use for general surfing and stuff. It has 256Mb Ram and i needed i light distro. I looked around and found MoonOs and was pleasantly surprised by its light and beautiful setting and its easy set up of wireless (its based on ubuntu 9.04). look at my screenshot!!!

Dang that doesnt look half bad!

---

### Post by kedaha on 2009-12-06
Have installed Xubuntu (karmic) 386 kermel (thanks for suggestion), on the 10 year old HP Omnibook XE2 Pentium 3 (448 Mhz CPU + 256 RAM) and  there's a definite improvement in peformance. Now only 2 things to be done: a) make the serial mouse work and b) get 1024*768 screen resolution.

---

