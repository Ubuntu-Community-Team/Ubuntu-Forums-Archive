---
title: "Ubuntu won't boot after nvidia driver install"
date: 2010-03-04
forum: General Help
---

### Post by dshippee on 2010-03-04
Hello,

This is my first day with Umbuntu and my first post here at the forums.

I bought a Dell Pentium 4 with a fresh install of Umbuntu 9.10 on it.  Worked well until I decided to do something a newbie shouldn't do and install a graphics card and drivers.  The graphics card worked just fine until the drivers were installed and I tried to reboot the system.  Now it no longer boots.

Some specifics for you.

Since my time with Ubuntu is limited to hours, the nomenclature will probably be wrong.  But I will try to get the point across.
  
The card is a EVGA GeForce FX 5700 Ultra.
On first start up with this card the computer functioned fine.
I went to a place where you could change the screen options.  There were three selections and I don't remember the names (idiot that I am).  I selected the middle one.  The OS stated that in order to utilize all the capabilities of nvidia graphics cards blah, blah, blah, a driver would need to be downloaded and activated.  No name, just a driver.  OK, do it (sounds kinda windows like).  The download seemed to go OK, but now I needed to reboot to activate the driver.

Now:
Ubuntu logo comes up.
Screen goes to a text screen that says:

Ubuntu 9.10 dave-ubuntu tty1
dave-ubuntu login:

This screen flashes and does not take input from the keyboard or mouse.

Next, I removed the graphics card and used the on-board graphics.
Same result with faster flashing.

What have I done?  Apparently Ubuntu and Linux in general don't have a system recovery option?

I read something about the GRUB menu, but the system flasher GRUB loading for half a second and then is on to locking up.  I can't seem to get to a GRUB menu.  What a way to finish the day.

Thanks for any and all input to a new user who screwed up.

---

### Post by marshmallow1304 on 2010-03-04
Pop the nVidia card back in.  And boot up to the
> Ubuntu 9.10 dave-ubuntu tty1
dave-ubuntu login:
Login with your username and password, then issue these commands.
```
sudo nvidia-xconfig
sudo reboot
```
The first command will ask you for your password.  Nothing will display when you type the password; this is normal.

---

### Post by lidex on 2010-03-04
> **marshmallow1304 said:**
> Pop the nVidia card back in.  And boot up to the

Login with your username and password, then issue these commands.
```
sudo nvidia-xconfig
sudo reboot
```
The first command will ask you for your password.  Nothing will display when you type the password; this is normal.

Unfortunately his keyboard doesn't work there.
dshippee: you'll need to boot into recovery mode from a LiveCD. Once you get to the repair options, select the one to fix xserver (something like that). Let it do it's thing, then reboot.

Keep us updated.

---

### Post by dshippee on 2010-03-04
OK, I'll make up a disc sometime today and try it.

I noticed this morning that the no keyboard input is not entirely accurate.  If I type the letter enough times I can get my user name to display on the screen and it will ask for my password.  Nothing displays when I type my password, so I have no idea what I am sending to the OS.  The number of times I must hit a key to make a character display seems sort of random almost like the ability to take keyboard input is flashing at the same rate the display is.  Odd.

Thanks, more later.

---

### Post by lidex on 2010-03-04
Looks like the nvidia 173 driver is the last to support your gpu. When all is said and done either that or the nv driver is what you'll want, I'm thinking.

---

### Post by marshmallow1304 on 2010-03-04
> **lidex said:**
> Unfortunately his keyboard doesn't work there.

D'oh!  Must've been tired.

---

### Post by dshippee on 2010-03-04
After making an Ubuntu Live CD on another computer I was able to make the machine boot up.  I couldn't find the repair or fix xserver anywhere so I assume it is a terminal command.

I tried uninstalling all the drivers I could find for nvidia under the synaptic package manager and rebooted.  No luck.  The best use of my time at that point was a reinstall of 9.1, so that is what I did.  I only had the computer a few hours when I screwed it up, so nothing was loaded onto it.

Everything works.  Now I can tell you where I had the problems.  

Under system/preferences/appearance click on the visual effects tab.  The default setting is none.  I chose normal and a box appeared that said "enable driver?"  nvidia accelerated graphics driver.  Then a description of what the driver does (which sounded good), so I clicked enable and that was the end of a working machine.  This time I clicked cancel and it went back to the default setting of none.  Apparently the driver that Ubuntu picks must not be compatible with my card.  I wish I knew how to figure out what that driver is so I could install a different one and maybe make desktop effects work.  There will be more learning before that can happen.  I am happy the machine works now.

Thanks for the help.

---

### Post by dshippee on 2010-03-05
Fixed!!  

I started reading all kinds of stuff people had written about nvidia drivers and ubuntu.  I tried downloading the latest drivers from nvidia for the x86 linux/ubuntu (173.14.25) and they would not install.  I got an error message about gedit not being able to detect the character coding.  Hmmmm...  So next I tried system/administration/hardware drivers.  Here the OS checked for available drivers for the nvidia card and gave me a choice between installing the 173 drivers or the 96 drivers.  173 was recommended, so I went with it.  

Restart went well until it told me that ubuntu would run in low resolution because a power connection was missing from my video card.  Huh?  Shut down and open the case, well I'll be, there is a power connection on the end.  Rearrange the wiring and power that baby up.  Now system/preferences/appearance/visual effects can be set to extra.  Cool beans!!

Screen resolution and appearance are great but performance off the vga connector on Hulu is a bit jerky yet.  More fooling around necessary or maybe a better graphics card than the one I am using ($20.00 off Craigslist).  ...or maybe using the dvi out?

More playing will be necessary.

Thanks for all the help!

---

### Post by lidex on 2010-03-05
> **dshippee said:**
> Fixed!!  

I started reading all kinds of stuff people had written about nvidia drivers and ubuntu.  I tried downloading the latest drivers from nvidia for the x86 linux/ubuntu (173.14.25) and they would not install.  I got an error message about gedit not being able to detect the character coding.  Hmmmm...  So next I tried system/administration/hardware drivers.  Here the OS checked for available drivers for the nvidia card and gave me a choice between installing the 173 drivers or the 96 drivers.  173 was recommended, so I went with it.  

Restart went well until it told me that ubuntu would run in low resolution because a power connection was missing from my video card.  Huh?  Shut down and open the case, well I'll be, there is a power connection on the end.  Rearrange the wiring and power that baby up.  Now system/preferences/appearance/visual effects can be set to extra.  Cool beans!!

Screen resolution and appearance are great but performance off the vga connector on Hulu is a bit jerky yet.  More fooling around necessary or maybe a better graphics card than the one I am using ($20.00 off Craigslist).  ...or maybe using the dvi out?

More playing will be necessary.

Thanks for all the help!

Awesome. Your Hulu problem may well be a flash issue. You using Firefox? Check this:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by yp2010 on 2010-03-29
Hi all,

> **dshippee said:**
> 
Now:
Ubuntu logo comes up.
Screen goes to a text screen that says:

Ubuntu 9.10 dave-ubuntu tty1
dave-ubuntu login:

This screen flashes and does not take input from the keyboard or mouse.



I have the exact same problem. After trying to update recommended graphics driver for nvidia card on my Asus UL50VT laptop I can no longer boot into gui.

I can boot into recovery console but typing "nvidia-xconfig" and "reboot" did not fix it (same when typed with "sudo" in front).

Any ideas?

---

