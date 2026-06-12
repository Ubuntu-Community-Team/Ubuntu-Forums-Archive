---
title: "Need help installing!"
date: 2010-04-30
forum: General Help
---

### Post by hitman0042 on 2010-04-30
I am trying to install Ubuntu 10.04 LST or whatever it is.

I boot it up and click "Install Ubuntu", but then the screen goes blank, no sound, disc isn't spinning or nothing!

Whats the problem?

32bit OS 4GB of RAM

---

### Post by chessnerd on 2010-04-30
> **hitman0042 said:**
> I am trying to install Ubuntu 10.04 LST or whatever it is.

I boot it up and click "Install Ubuntu", but then the screen goes blank, no sound, disc isn't spinning or nothing!

Whats the problem?

32bit OS 4GB of RAM

I'm not sure. Try going into the LiveCD demo mode and see if that works, if so, try the installer from there. If that doesn't work then there are two possibilities:

1. The disk image wasn't properly burned (it happens, burning at a lower speed helps)
2. Ubuntu doesn't play nice with your computer

Posting a more complete list of specs would help. What is the computer's:

Brand and Model?
Graphics card type and model number?

---

### Post by hitman0042 on 2010-04-30
Ok thanks for your reply. 

I burnt the image at 4x speed.

The system specs are as follows:
Pentium 4 3.2ghz
4GB DDR 226 RAM
ATI Radeon 9800xt (but not in use)
OS: Windows Server Edition

I want to be able to boot from CD so i can format the drive for a fresh install. It boots from cd, and come with a Optiion first asking what language, then continues to the option page where it says, "Boot Ubuntu without installation" or "Install Ubuntu". I want to install it, so i click on it, then it goes blank screen, and my monitor goes on stanby and screen goes blank!

---

### Post by vader95 on 2010-04-30
> **hitman0042 said:**
> 

ATI Radeon 9800xt (but not in use)

I want to be able to boot from CD so i can format the drive for a fresh install. 

By not in use you mean that there is another graphic car that is being used.

Also if you just want to format the drive for windows, or even ubuntu, try parted magic [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

---

### Post by robert shearer on 2010-04-30
> where it says, "Boot Ubuntu without installation" or "Install Ubuntu"

Try "Boot Ubuntu without installation" and it will boot up to a desktop environment (you can **install from there as well**, it just uses more resources as it does it)

Trying first will give some troubleshooting info as well as some extra tools that we may need.

---

### Post by dino99 on 2010-04-30
you need the "alternate" image to perform a custom install and create 3 partitions:
- / which is root and might be bootable with ext3 or ext4 format (about 12 go)
- a swap about twice your ram
- /home where all your data will be stored, with format ext3 or ext4 (no limit space)

install the bootloader Grub on / ( path named /dev/sda or so, you have to take note of its path when you format it)

---

### Post by hitman0042 on 2010-04-30
lol i have no idea what you just said!

I will try to boot it normally and install it through that. If it still does not work, what are the other solutions?

---

### Post by robert shearer on 2010-04-30
> If it still does not work, what are the other solutions? 

**We** don't know until **you** try it and can report back with details.

You have the first step = boot from live cd and try the desktop environment to see if your hardware works.
If not, report back the faults encountered.
If all is ok (screen, network, peripherals etc etc   try using it as you would any other o/s for a few hours, surf the web, play music, et al) then it should be fine to install.

You have enough ram and fast enough processor that installing while running the live cd desktop environment should be a breeze.

---

### Post by hitman0042 on 2010-05-01
ok i did it. 

I moved the computer and connect it to anotherm monitor. Now, i could see everything working, and installed linux. although, after it installed, it had some error. Seems okay now, went to desktop and etc.

So now i moved it back to its original area and monitor. Once again, i can not see anything. Screen just turns off to stand by. I know it boots up and goes to desktop, i just can't see it.

so what's wrong with it? How can i fix it?

---

### Post by hitman0042 on 2010-05-01
Anyone? Im pretty desperate!

---

### Post by dino99 on 2010-05-01
alt+f2 to open a terminal, then:

sudo rm -f /etc/X11/xorg.conf

---

### Post by hitman0042 on 2010-05-01
when do i do this when the screen is blank on standby lol?

can you please be more specific

---

### Post by dino99 on 2010-05-01
> **hitman0042 said:**
> when do i do this when the screen is blank on standby lol?

can you please be more specific

yes, dont be so shy, try :P

---

### Post by hitman0042 on 2010-05-01
how can i! the screen is blank! its on standby, the screen turns off! its wrecked lol!

---

### Post by dino99 on 2010-05-01
if the system is hanged, then reboot, have you the grub menu at boot time ?
if not hold down the "shift" key at the end of bios process and boot in recovery mode

---

### Post by Brad J on 2010-05-01
Did you say it worked on the other monitor and you installed it? If so I think the problem is the default resolution of Ubuntu isn't compatible with your monitor. 

A way I fixed this when I had this problem was to change the resolution using your other monitor (**System - Preferences - Monitor**) to one that is compatible, this may be trial and error however. 

You then want to make it that when you turn your computer on it automatically logs you in, this is because (In 9.10 anyway) the login resolution screen doesn't change, so with auto-log in on it loads the gnome desktop with the resolution you had previously. 

I hope this helps :)

---

### Post by hitman0042 on 2010-05-01
when you say grub menu? What do you mean? Linux has no been installed and now boots to desktop, but i can not see it boot.

---

### Post by hitman0042 on 2010-05-01
yer i might have to try this tomorrow. Ill report back on how it goes....

---

### Post by Brad J on 2010-05-01
The grub menu is the menu what displays after you turn the computer on if you have 2 operating systems installed, if you only have Ubuntu installed then you won't see this :) 

And ok, I'll check back tomorrow to see how it went :)

EDIT: BTW using my method, if the problem is what I think it is, you won't see ubuntu boot, the screen will be off until you have logged in.

---

### Post by hitman0042 on 2010-05-01
ok reporting back. Here are some of the things i did:

1. I put it onto the otherm onitor and changed the resolution, as the compouter was turned on, i changed monitors, and whola, it worked! So then i tested it, by turning itt off, and rebooting (with the monitor that originally doesn't display) and, once again, NO DISPLAY. The only way i can display it, is if i connect the VGA cable with the "working" monitor, then unplug it and connect to the original monitor. Even then, the computer must be on and once i restart, i wont see it again. This needs to be fixed, how i do not know?

2. Second, i installed teamviewer on this computer, please note, this pc is going to act as a "server" type of thing, more of a storage computer. So i want to be able to access this pc,  from my own personal pc in my study. With the windows teamviewer, it will auto run at start up, therefore, when i turn it on, i can just leave and itll auto run meaning i can access it remotely. But Linux did not do that! I had to go in some "autorun" options of the OS and make a new line of code for it so that runs. Does it work? i do no know cause i am still working on the monitor issue. Also, when the linux locks, i cnt access this teamviewer anymore. 

3. Lastly, if i am using the computer as a storage pc, where we can transfer files to it, i need to be able to "see" the hardrives and be able to access them. But how do i do this? i go into network and try to enable some file sharing thing. But i cant because it says you need the right packages. So i go to update linux, and it says all updated, but still can not share the files. 

4. My solution, go back to windows unless you guys knows whats going on?

---

### Post by 3rdalbum on 2010-05-01
> **hitman0042 said:**
> 1. I put it onto the otherm onitor and changed the resolution, as the compouter was turned on, i changed monitors, and whola, it worked! So then i tested it, by turning itt off, and rebooting (with the monitor that originally doesn't display) and, once again, NO DISPLAY. The only way i can display it, is if i connect the VGA cable with the "working" monitor, then unplug it and connect to the original monitor. Even then, the computer must be on and once i restart, i wont see it again. This needs to be fixed, how i do not know?

That's quite an unusual problem, but it might be solvable.

With the "non-working" monitor plugged in, boot up Ubuntu. Press Control-Alt-F2 to switch to a non-graphical terminal; the monitor should turn on and display a textual screen.

Use your login details on this textual screen. Now type:

```
sudo service gdm stop
sudo X -configure
sudo rm /etc/X11/xorg.conf
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start
```

This turns off the graphical desktop temporarily, tells the system to find out as much information as possible about your graphics card and monitor, removes all information that it previously had (if any), moves the new information to the correct location, and then restarts the graphical desktop.

> 3. Lastly, if i am using the computer as a storage pc, where we can transfer files to it, i need to be able to "see" the hardrives and be able to access them. But how do i do this? i go into network and try to enable some file sharing thing. But i cant because it says you need the right packages. So i go to update linux, and it says all updated, but still can not share the files.

Ubuntu doesn't come with the packages needed to share files (this is by design) but they are easy to add. You can use Synaptic Package Manager to install the "samba" package, or type the following into the terminal which does the same thing:

```
sudo apt-get install samba
```

---

### Post by hitman0042 on 2010-05-01
yer didn't work. The coding says "unknown" and the samba thing didnt even do it either. 

Solution: Go to windows. Linux is terrible. Why can't it display on the monitor! Whats the big deal! What a weird problem, windows has never done that.

---

### Post by Brad J on 2010-05-02
Did you make it so when your computer turns on then it will automatically log you in? Because the log in screen resolution doesn't change, only once you have logged in, so by putting auto log in on it will hopefully solve your problem.

---

### Post by hitman0042 on 2010-05-02
Yer i did do that.

Anyway thanks for all your help but i got rid of linux went back to windows. It wad un fixable

---

