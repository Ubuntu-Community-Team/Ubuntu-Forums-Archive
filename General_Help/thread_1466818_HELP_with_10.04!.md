---
title: "HELP with 10.04!"
date: 2010-04-30
forum: General Help
---

### Post by JPeterguy on 2010-04-30
I installed 10.04 last night, but I guess something happened during installation, and now I have no idea how to fix it.
 
The computer starts up as it normally would, and gets to the splash screen (black screen with Ubuntu logo in the middle), before it goes to a black screen with a command prompt to enter my username and password.
 
Once I do that, it says "Welcome to Ubuntu" and lets me type in commands and stuff. 
While researching online, I found this thread:
[[COLOR=#22229c]Ubuntu 9.04 doesn't boot into GUI[/COLOR]]("http://forums.techarena.in/operating-systems/1241547.htm")
 
I tried the first thing,
 
```
sudo /etc/init.d/gdm restart
```
 
and that brings me to the GUI login prompt (what I want), but then my mouse doesn't work. I even tried plugging in a normal USB optical mouse and that doesn't work either (though it's definitely connected because the red light beneath the mouse turns on, it just doesn't do anything.
 
I also tried the second suggestion,
 
```
startx
```
 
and it booted me into the desktop, but neither the keyboard OR the mouse worked. 
 
Anybody have any idea what I did, and how I can fix it? Thanks!

---

### Post by P4man on 2010-04-30
is this a laptop? Is it possible the battery died while it was upgrading?

---

### Post by JPeterguy on 2010-04-30
Yes, it is a laptop. and it did turn off while I was upgrading...but I restarted the upgrade after turning it back on and it finished and told me to restart...and then I ran into these issues.

---

### Post by P4man on 2010-04-30
Are you sure it finished? You mention a black screen with a logo, ubuntu 10.04 has a purple splash screen,

What kernels do you see in grub?

---

### Post by JPeterguy on 2010-04-30
I'm seeing:
 
Ubuntu 9.10, kernel 2.6.31-20-generic
" ", kernel 2.6.31-19-generic
" ", kernel 2.6.31-17-generic
" ", kernel 2.6.31-16-generic
 
and so on. 
 
but the strange thing is, after that black screen with the ubuntu logo, when it boots into the command prompt, the top of the screen reads:
 
Ubuntu 10.04 LTS Jguy tty1
 
So...are both 9.10 and 10.04 installed right now?

---

### Post by P4man on 2010-04-30
those are 9.10 kernels. The upgrade didnt finish.
try this in a terminal:

```
sudo dpkg --configure -a
```

(note the double dash before configure and single dash before a!)

That might take a while (I hope). After that you can try

```
sudo apt-get install -f
sudo apt-get dist-upgrade

```

---

### Post by pcura on 2010-04-30
Just a suggestion though, I think its better if you do a fresh install instead of upgrading. Just backup your files. Have your laptop connect to AC outlet, and set your sreensaver to NONE. Nowadays laptops tend to hibernate or turn off after 10-20 mins.

Just my two centavo.

---

### Post by JPeterguy on 2010-04-30
> **P4man said:**
> those are 9.10 kernels. The upgrade didnt finish.
try this in a terminal:
 
```
sudo dpkg --configure -a
```
 
(note the double dash before configure and single dash before a!)
 
That might take a while (I hope). After that you can try
 
```
sudo apt-get install -f
sudo apt-get dist-upgrade

```
 
 
Tried
 
```
sudo dpkg --configure -a
```
 
and nothing happened.
 
The battery on my laptop is dead (waiting on a new one to come in), and I had accidentally put some tension on the cord and it unplugged, which was why the computer turned off.
 
Any other suggestions?

---

### Post by P4man on 2010-04-30
try the other 2 commands. Also, do you have any other OS's installed? separate /boot partition? If you are unsure, check 

```
sudo fdisk -l
```

Just wondering if grub is not managed by a different linux install and feeding the wrong kernels.

---

### Post by cespinal on 2010-04-30
Sorry about this man. I would try to go for a fresh install...

---

### Post by P4man on 2010-04-30
one more thing you can (and should) try:

```
sudo update-grub
```

---

### Post by JPeterguy on 2010-04-30
Tried
```
sudo apt-get install -f
```
it read package lists, built dependencies and read state information, then said
0 upgraded, 0 newly installed, 0 to remove and 380 not upgraded
 
next i tried 
```
sudo apt-get dist-upgrade
```
and it had A LOT of errors. Lots of "**failed to fetch**" and "**could not resolve**". I guess it can't connect to the internet in this mode?
SIDE NOTE: when I ran "startx", and it went into the desktop, it connected to my wireless network...so its definitely able to. is there a way to connect to the network through the command prompt? would that work?
 
Next I tried
```
sudo fdisk -1
```
and it said: **fdisk: invalid option -- '1'**
 
i finally tried
```
sudo update-grub
```
and it updated and i rebooted, but nothing changed
 
 
If there are no other ideas...whats the best way to do a fresh install? to make things incredibly worse, my CD drive is broken, so I can't install it from a CD. Are there other ways?

---

### Post by cespinal on 2010-04-30
live usb stick?

---

### Post by JPeterguy on 2010-04-30
I don't have a USB stick. Is there a way of getting internet access in this command prompt that I am in, and installing it that way?

---

### Post by P4man on 2010-04-30
The upgrade command does require internet connection, and possibly you need it to be wired. We'll figure that out later.


Right now id like to see fdisk -l. That is FDISK -L in lowercase, not 1. You havent replied if you have any other OS's installed. Do you?

When you ran update grub, did you get to see the same kernels you posted earlier, or did it detect a 2.6.**32** kernel?

---

### Post by JPeterguy on 2010-04-30
I only have Ubuntu installed.
 
running fdisk, this is what comes out:
 
Disk /dev/sda: 120.00 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x182f182e
 
Device Boot Start End Blocks ID System
/dev/sda1 * Linux
/dev/sda2 Extended
/dev/sda5 Linux Swap / Solaris
 
*there are plenty of numbers for boot, start, end, blocks and ID...but I figured they werent necessary.  If they are I can post them.
 
 
 
and no, there was no 2.6.32 kernel.

---

### Post by CharlesA on 2010-04-30
It would probably be better to use a wired connection when doing the upgrade, since it will be simpler to configure:

```
sudo ifconfig eth0 down && sudo ifconfig eth0 up
```

You can configure wireless from the command prompt, but it's a bit of a pain.

Suggestion: Plug an ethernet cable in and reboot, then try to ping google.com and see if it gets a response.

If it does, try running this again:

```
sudo apt-get dist-upgrade
```

---

### Post by P4man on 2010-04-30
oookay.. this is becoming a challenge.
If you run 

```
ls /boot
```

do you see lucid kernel(s) like 

vmlinuz-2.6.32-etc

or only karmic like

vmlinuz-2.6.31-etc

---

### Post by JPeterguy on 2010-04-30
ls /boot only brings up .31, no .32

There are a few .30 too

---

### Post by P4man on 2010-04-30
then clearly the upgrade didnt complete. You are going to need to get connected. See CharlesA's post if you can get a lan cable.

---

### Post by JPeterguy on 2010-04-30
Alright, when I get home I'll plug it in and hopefully that will work haha. Thanks for the help.
 
If you couldn't already tell, I'm pretty new to ubuntu and especially in working in the terminal and stuff, so if it's not too much trouble could you tell me specifically what I need to type in? and if you have any tips for me so I don't end up screwing things up so badly I'd appreciate that too

---

### Post by P4man on 2010-04-30
it was already posted earlier. To turn on the lan its (hopefully) just

```
sudo ifconfig eth0 up
```

You can confirm if that is working by pinging google 
```

ping www.google.com
```

if that doesnt time out, its working (press ctlr+c to end). Which would be good, but since you now have a mix between ubuntu 10.04 with too old kernels, who knows what still works. Id suggest you stop by a store on the way home and pick up an usb stick as well. Something tells me you may need it.

---

### Post by CharlesA on 2010-04-30
It's pretty hard to screw up unless you do something stupid like "rm -rf /" (Don't do it!)

The worst that usually happens is that the command will spit back the part that it didn't like and suggest how to fix it.

Once you get it hooked up to your home network you can just run this:

```
ping google.com
```

See if it gives you something that looks like this:

```
PING google.com (74.125.19.103) 56(84) bytes of data.
64 bytes from nuq04s01-in-f103.1e100.net (74.125.19.103): icmp_seq=1 ttl=55 time=25.0 ms
64 bytes from nuq04s01-in-f103.1e100.net (74.125.19.103): icmp_seq=2 ttl=55 time=25.5 ms
```

If you see something like that, just run this:

```
sudo apt-get dist-upgrade
```

---

### Post by RedNight on 2010-04-30
I have almost the same problems as JPeterguy.

I've done an ubuntu fresh install, and, once I pass the login screen, my mouse and/or my keyboard just get paralyzed. 

With an USB mouse, this happens too. To apparently solve this issue, I just unplugged it and plug it again. Weird thing.

Then, since I installed 10.04, I just cannot connect to my home network. Every time I login, it seems connected but, never reach a website. I've tried
```
sudo ifconfig eth0 down && sudo if config eth0 up
ping www.google.com
```

and then, I got an exclamation mark on network's icon.


I've tried already to upgrade from 9.10 to 10.04 and I got the same issues.

Can you help me up?

Nowadays, without an internet connection, no one live, right? :)

I am seriously considering to back to 9.10... :S

Cheers from Portugal. ;)

---

### Post by P4man on 2010-04-30
rednight, if you did a fresh install, and not an upgrade, you are having a completely different issue. Im pretty sure you will have the correct kernels to name just one thing.

Id suggest you open a new thread explaining your network connection problems under lucid,  providing information like network card type (output of 
```
lspci
``` ). im sure you will get helped, but its not related to this problem (incomplete/aborted upgrade).

---

### Post by JPeterguy on 2010-05-01
OK so here's what happened. 

I went home, the distro upgrade worked, and I rebooted. 

Same issue. It went to the black screen with the Ubuntu logo then the black screen with the text prompt to log me in. 

Only this time when I login it says 2 packages can be updated. I tried running sudo apt-get update, and I thought it did something, but after rebooting I'm brought back to the same screen with the same message

Grub is showing "Ubuntu 10.04 lts, kernel 2.6.31-20 generic

---

### Post by CharlesA on 2010-05-01
Have you tried booting off a livecd and seeing if Lucid will load fine that way?

I have a feeling you will probably be better off doing a clean install then trying to troubleshoot why X isn't loading.

---

### Post by P4man on 2010-05-01
pretty sure x is not loading properly because he doesnt have the correct kernel (and god knows what else he is missing)

Long shot, but maybe try pulling in the correct kernel with:

```
sudo apt-get install linux-image-2.6.32-21-generic
sudo update-grub2
```

requires working internet connection and also assumes your software sources have been updated by the upgrade process.

---

### Post by JPeterguy on 2010-05-01
Ok, so i was able to install the kernel with 

```
sudo apt-get install linux-image-2.6.32-21-generic
```

It even shows up on the kernel list and everything.

but when i tried upgrading GRUB this error came up:

[B]sudo: update-grub2: command not found

[/B]I also noticed when the computer is restarting and the GRUB screen appears (where it says click escape in 3...2....1, the top says GRUB 1.5

Is that outdated as well?

Is it even worth trying to fix this, or should I do a clean install? and..if so...how do i go about doing that? (with a usb stick)

---

### Post by P4man on 2010-05-01
So I take it the new kernel didnt magically make everything work?

As for update-grub2 not working and you seeing 1.5 (?), that aint good (although adding the kernel install clearly triggered update-grub). Sounds like you;re still stuck with the old grub. I dont think it explains all the problems though.

```
Is it even worth trying to fix this, or should I do a clean install? and..if so...how do i go about doing that? (with a usb stick) 
```

i think clean install is probably the best thing to do. Download ubuntu from the website and put it on a usb stick with this:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

you can use windows or linux for that. Then boot from the stick and find out if lucid actually works properly on your hardware ("try ubuntu without changing your pc"). If all seems well, click the install icon and follow the instructions.

---

### Post by JPeterguy on 2010-05-01
OK so just so I have this right:

I'm going to download Ubuntu
I'm going to download UNetbootin
I'm going to run UNetbootin, direct it to the location where I saved the Ubuntu download
I will then take the USB stick, plug it into my laptop, and turn it on
I'll have a fresh install of Ubuntu


Also, since I'm doing this, am I going to have to go back and get rid of anything from my previous screwups? Or does the fresh install take care of that?

And finally, will I have to do anything to get my computer to recognize the USB stick, or is it going to work like a LiveCD and the computer will instantly recognize it?

Thanks again for all the help...

---

### Post by P4man on 2010-05-01
> **JPeterguy said:**
> OK so just so I have this right:

> I'm going to download Ubuntu
I'm going to download UNetbootin
I'm going to run UNetbootin, direct it to the location where I saved the Ubuntu download
I will then take the USB stick, plug it into my laptop, and turn it on

**<some steps missing here>**

I'll have a fresh install of Ubuntu

No. assuming your computer is configured to automatically boot from usb (you may have to configure that in the bios), plugging in the stick and turning it on will start a live session where you can test ubuntu without installing it.  This would be great opportunity to make a backup of any files you want to keep. Copy them to another stick, or the same one if you have enough free space.

In that session, you also have an install icon you can click to start the installation procedure. Just follow the wizard.
[QUOTE]
Also, since I'm doing this, am I going to have to go back and get rid of anything from my previous screwups? Or does the fresh install take care of that?

If you do an install and you tell it to use the entire harddisk, it will wipe it clean and start over. Hence the need to backup your data first.
> 
And finally, will I have to do anything to get my computer to recognize the USB stick, or is it going to work like a LiveCD and the computer will instantly recognize it?

Depends on your computer. You may have to press F11 or F12 during the early stages of booting up to get a "boot menu" where you can select the usb stick,  you may have to enter the bios (usually F2) and change boot device order, I dont know. There is no standard for that.

---

### Post by JPeterguy on 2010-05-01
OK, and finally....
I just realized this file is 699MB, but my USB stick is only 512MB. That just won't work, will it.

---

### Post by P4man on 2010-05-01
> **JPeterguy said:**
> OK, and finally....
I just realized this file is 699MB, but my USB stick is only 512MB. That just won't work, will it.

okay, confess. You are just trying your hardest to make things impossibly difficult lol.

A livecd wont work, but if you must, just to install (and wipe your hdd without a chance to backup!) there is probably a way:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I just dont know how to turn that in to a bootable usb stick easily. unetbootin may not work, or it may, I dont know.

---

### Post by JPeterguy on 2010-05-01
> **P4man said:**
> okay, confess. You are just trying your hardest to make things impossibly difficult lol.

A livecd wont work, but if you must, just to install (and wipe your hdd without a chance to backup!) there is probably a way:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I just dont know how to turn that in to a bootable usb stick easily. unetbootin may not work, or it may, I dont know.


Haha it's sure starting to seem like I'm subconsciously trying to.
I'm going to give that a shot..and if it doesn't work..well, I don't think I can do much more harm to my computer at this point lol

---

### Post by P4man on 2010-05-01
edit: I was wrong, never mind

---

### Post by JPeterguy on 2010-05-01
OK, it's official. I suck at life.

I can't remember my BIOS password. What, if anything, can I do now.

---

### Post by P4man on 2010-05-01
Am I on candid camera? Seriously lol !

Find your laptop (if its a laptop, dont remember) manual.

 You might be in serious pickle here, especially if you cant make the machine boot from usb without entering the bios, and you broke the cd drive and you dont remember the bios password.

Anything can be fixed, but resetting the bios on some machines is easy, on others (some dell laptops come to mind) require you disassemble allmost the entire laptop.

I hope you have more luck in life than you have with your computers!

---

### Post by JPeterguy on 2010-05-01
It's an Alienware laptop...a few years old...but I seem to remember, when I was trying to get into the BIOS once before, finding out that I would have to take it apart and remove some battery attached to the mobo. I think I eventually remembered the password, and promptly chose to change it to something I would remember. (oops)

---

### Post by JPeterguy on 2010-05-01
OK here's my problem now:

I was able to (I think) get it all fully installed. Everything seems to be working fine and it boots into the GUI login screen that's dark purple and fades into light purple. 

However, my touchpad doesn't work. Plugging in a USB mouse also doesn't work. 

Suggestions?

---

### Post by P4man on 2010-05-01
Besides buying a new laptop with windows preinstalled :) ?

Open a new thread. No one is going to plough through this one.

---

### Post by JPeterguy on 2010-05-02
So, I was screwing around trying different things, and I went into the GRUB bootloader, and chose to boot from the second one on the list (recovery mode?), and from there, highlighted the one that said fix missing packages and clicked enter.

after about 10 minutes, it finished, i restarted, and my laptop works again! They keyboard, the touchpad, everything. In fact, I'm typing this post on it right now!

---

### Post by williamqamd on 2011-01-07
> ** said:**
> It saves me a lot time to look for the info, It's very detailed, [[COLOR=#000000]Thanks[/COLOR]](http://www.skyblank.com/nl/self-improvement/the-deceptive-nature-of-spyware.html) for the posting.

---

