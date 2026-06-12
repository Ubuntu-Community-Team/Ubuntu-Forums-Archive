---
title: "USB mouse doesn't power off"
date: 2006-06-02
forum: General Help
---

### Post by Teo on 2006-06-02
Afer Shutting Down Dapper, my USB Optical mouse (Logitech OEM) doesn't power off - it keeps lighting. Why? It's so annoying :/.

In 'sudo dpkg-reconfigure xserver-xorg' I couldn't chose USB-type mouse (got only two PS/2's mouses to set).

ps. I still got my old Breezy and in Breezy mouse do power off.

---

### Post by Patrick-Ruff on 2006-06-02
seems kinda odd, is this a laptop or a desktop? I'm assuming its a desktop, laptops are usually all about the power saving stuff, and I doubt would let devices run while the computer is off. I rarly notice such things because of my computers being on almost 24/7 however, you could just simply unplug the usb mouse, since usb ports are usually very convienantly positioned.

---

### Post by Teo on 2006-06-02
[QUOTE=Patrick-Ruff]seems kinda odd, is this a laptop or a desktop? I'm assuming its a desktop[/quote]
Yes it's a desktop - m/b: Abit AN7.

[QUOTE=Patrick-Ruff]you could just simply unplug the usb mouse, since usb ports are usually very convienantly positioned.[/QUOTE]
USB ports are difficult to access, besides... no way :).


Yes it's kind of odd. Maybe it's because there's no hotplug system or USB-wathever-process isn't turned off when stuting down system?

---

### Post by viciouslime on 2006-06-02
Sounds like a bios issue to me... Does it happen when using another OS? Windows for example...

---

### Post by seanUSXIII on 2006-06-02
is it plugged into a (external) hub?

---

### Post by Teo on 2006-06-02
[QUOTE=viciouslime]Sounds like a bios issue to me... Does it happen when using another OS? Windows for example...[/QUOTE]
USBPOWER jumprs on my m/b were set into "enable" - that was the reason.

Strange is, when shuting down Breezy mouse do power off. Unfortunetly I don't have Windows at all, so I can't check that on this OS.

THX for help everyone :).

---

### Post by finewbie on 2006-09-27
I have the same problem. With my Windows XP the USB mouse is properly powered off but with Debian (sorry, could not get Ubuntu working..) the USB mouse keeps lighted when linux is shut down.

I found from bios setting called "support usb mouse". There were no difference between enabled or disabled. Any other settings that could affect to my usb mouse I could not find.

I have a sealed computer so I am not so interested to make some jumper settings from mother board. Is there any other ways to solve the problem? I think there should be because my XP does the shut down properly.

Suggestions?

-Petteri

---

### Post by bkanuka on 2006-11-08
I'm in the same boat. My USB microphone also stays on. Did not happen in Windows.

---

### Post by firfin on 2006-12-07
Hi there,
I am experiencing a similar problem. My G15 keyboard (all keys are lit from behind) stays on when I 'turn off computer' (as it is calle din kde.

Resorting to unplugging usb devices isn't a very attrative option for me. Anybody out there with some other ideas?

---

### Post by MrWhammy on 2007-04-21
Same problem here with mouse, keyboard and smartcard reader.

---

### Post by firfin on 2007-05-25
I'm still experiencing this phenomenon. Anybody come up with a solution yet?

Shutdown with winXP  ->  all usb shuts down
shutdown with 7.04 Fiesty (had same prob with 6.10 Dapper)   ->  bright usb devices everywhere

asus mobo with nforce chipset

---

### Post by armalite on 2007-05-25
Just tried Gutsy Gibbon with no luck, lights are still powered. Indeed, suspending does proper shutdown lights, weird.

---

### Post by BrendaEM on 2007-05-31
I have that problem too, but my lit keyboard continues to glow. 

The USB ports are not powering down.

On a Asus 8-NE, and Ubuntu Studio, but I've seen this on Dapper.

This problem does not occur on Windows.

---

### Post by chriswyatt on 2007-05-31
Wow, that's interesting.  I guess that's so you can power up using external devices, my old motherboard used to do that with PS/2 devices.

---

### Post by Crinos512 on 2007-08-06
I have the same issue with both My G15 keyboard and External USB drive.

Whenever I shut down I still have my nightlight (the G15's LCD), and like most people I plug my keyboard in to the rear of my PC.

WTF? :confused:

---

### Post by gweaver on 2007-08-14
I have the same thing on Feisty. My mouse and external hard disk do not power down.

Under XP they do.

Odd.

---

### Post by dninja on 2007-09-02
Same here, mouse, usb hub, card reader and external hdd all stay powered on.

I'm not too bothered about most of it but I want the hdd to shut down automatically so I don't have to remember to manually start up and shut it down.

---

### Post by Haiyadragon on 2007-09-18
An older thread about this: [http://ubuntuforums.org/showthread.php?t=206385&highlight=usb+power](http://ubuntuforums.org/showthread.php?t=206385&highlight=usb+power)

A kernel bugreport:
[http://bugzilla.kernel.org/show_bug.cgi?id=5410](http://bugzilla.kernel.org/show_bug.cgi?id=5410)

But they seem to be on the wrong track and in no hurry to fix it.

---

### Post by dcstar on 2007-09-19
> **Haiyadragon said:**
> An older thread about this: [http://ubuntuforums.org/showthread.php?t=206385&highlight=usb+power](http://ubuntuforums.org/showthread.php?t=206385&highlight=usb+power)

A kernel bugreport:
[http://bugzilla.kernel.org/show_bug.cgi?id=5410](http://bugzilla.kernel.org/show_bug.cgi?id=5410)

But they seem to be on the wrong track and in no hurry to fix it.

In XP I have seen two shutdown options:

Shutdown
Shutdown and power off

I would say modern motherboards have an additional BIOS call in addition to the traditional "Shutdown" one that has been around since the original IBM PC, and this new one shuts down all the USB devices as well.

The "normal" shutdown may still allow the Keyboard power-up feature to be used, perhaps if this is disabled in the BIOS then the motherboard may not bother to keep powering USB devices?

It may that the current Linux kernel doesn't bother to call the new "Power off" BIOS call on shutdown, but it seems it should be an option (as it is in XP).

---

### Post by jyank on 2007-09-19
I have this problem as well  (G15 Keyboard, Logitech MX518 and external harddrive all stay powered) - i've tried a bunch of different things, but with no success.  It's rather annoying to have to boot into windows just to power my mouse and keyboard off, but oh well, I'd rather have a small issue like this versus something huge.

---

### Post by dcstar on 2007-09-19
> **jyank said:**
> I have this problem as well  (G15 Keyboard, Logitech MX518 and external harddrive all stay powered) - i've tried a bunch of different things, but with no success.  It's rather annoying to have to boot into windows just to power my mouse and keyboard off, but oh well, I'd rather have a small issue like this versus something huge.

Actually there are some terminal commands people may want to try to see what happens:
```
sudo halt
sudo halt -p
sudo poweroff
```
The second two are supposed to fully power off systems.

I have just noticed that identical Ubuntu installs on different hardware behave differently, a USB device on my new hardware is powered off on shutdown, but a USB mouse on my old hardware isn't!

---

### Post by armalite on 2007-09-19
I tried the above commands with no luck on my asus p5n32-sli se deluxe (core2duo with nvidia chipset). 

Unlike what it is written here [http://bugzilla.kernel.org/show_bug.cgi?id=5410#c22](http://bugzilla.kernel.org/show_bug.cgi?id=5410#c22), my mouse (logitech ifeel) keeps the lights on when i replug it on the usb port.


The real, i mean *REAL*, strange thing is that the mouse & card reader lights turn off when i suspend or hibernate my pc. This lead to other issues anyway, since there's something with nvidia that breaks when i resume (so i can't use these features on feisty).

On Gutsy I have the same behaviour, though suspend and resume work (at least a couple of months ago, last time i tried).

---

### Post by dninja on 2007-09-19
I've got this half solved. My desktop PC has a jumper which says whether to turn off the USB on power down. I've now got that on so all the USB devices power down with the machine. My other box is a Shuttle PC, I emailed Shuttle and they said that there is no way to do it. Unfortunately, that is the machine I really needed it on so I've had to resort to another internal disk which I didn't really want to do but there isn't much else I can do.

---

### Post by jlachovsky on 2007-10-20
I take it there still isn't a solution to this.  Kind of sucks cause I really don't want my G15 Keyboard on when I am not using it.  I'll have to check my mobo documentation and see what it says.

---

### Post by hessiess on 2007-10-20
carnt you just switch off the mains?

---

### Post by armalite on 2007-10-21
This is what I'm forced to do, anyway it isn't the correct behaviour: I can't use usb power to charge mp3 player (note: power line and mouse leds are different things), I can't boot my pc just hitting a key on the keyboard (wake on ps/2), and switching off the mains prevents also wake on lan.

So, this is not the correct behaviour, given that usb correctly powers off when in suspend mode...

---

### Post by dninja on 2007-10-22
> **hessiess said:**
> carnt you just switch off the mains?

I want to keep wake on lan working which is why I don't want to turn off at the mains.

---

### Post by durand on 2007-10-26
Might the WOL feature have something to do with it? Though I really doubt that everyone else on this thread has it enabled....However, it must have something to do with your bios....my usb keyboard and mouse don't have any power when my computer is off.

Slightly off track but is there a way to completely turn off power without resorting the the mains cable? I notice that my ethernet cable is lit up and the power is probably coming from my powered down computer...I don't need WOL, so any ideas? There might be a bios setting, Ill have to check..

EDIT: no options in the BIOS :(

---

### Post by dninja on 2007-10-26
> **durand said:**
> Might the WOL feature have something to do with it? Though I really doubt that everyone else on this thread has it enabled....However, it must have something to do with your bios....my usb keyboard and mouse don't have any power when my computer is off.

On the shuttle, the response from Shuttle themselves is that there is no way to turn power off to USB without turning off mains power. On my other machine, I have turned off USB power in the BIOS so that usb does shutdown when I turn off the machine but WOL still works.

> 
Slightly off track but is there a way to completely turn off power without resorting the the mains cable? I notice that my ethernet cable is lit up and the power is probably coming from my powered down computer...I don't need WOL, so any ideas? There might be a bios setting, Ill have to check..

EDIT: no options in the BIOS :(

I read a while back about some new PC's that never actually shutdown. They run some software so that even with the power off things like the BIOS can be queried. It was designed for remote sys-admin work but it could be used for all sorts of stuff.

---

### Post by FilmAficionado on 2007-10-26
I have the exact same problem. Both my keyboard and mouse remain lit and since my computer is in my bedroom, they both serve as a distraction when I try to sleep at night. 

Microsoft Comfort Optical Mouse 3000 v. 1.0 = USB Mouse
Microsoft Natural Ergonomic Keyboard 4000 v. 1.0 = USB Mouse connected via regular keyboard port (w/ adaptor).

So no solutions then, right?

---

### Post by durand on 2007-10-27
I think my dell computer is like that....I think it stores a bit of power in the motherboard but its kinda annoying.....It's just a waste of energy when I don't need such a feature. I think I see a reason for this, the power button is a soft button, so it needs a bit of power to recognise it... If I could only turn off everything else, that would help.

---

### Post by armalite on 2007-10-27
The problem could be explained [here]("http://bugzilla.kernel.org/show_bug.cgi?id=5410"),  when i'll have some spare time (maybe next week) i'll try to recompile the kernel with the patch shown on that link. 

It seems to be a nasty workaround, but it is really worth a try. If some of you tries the patch, please post the results here down. Thank you.

---

### Post by sliPrix on 2007-11-04
After issuing the command ```
lshal
``` I noticed the line "usb.can_wake_up = true  (bool)"  So I then typed ```
hal-device-manager
``` found my usb mouse, and tried to change the value from true to false.  Every time I did, and clicked outside of the value, the value changed back to true.  I tried running this as sudo, with the same results.  I think this may be a start of a solution, or a good attempt at one to see if changing the value to "false" would have any impact on the situation.  If anybody knows how to go about doing this please reply.  Thanks.

---

### Post by armalite on 2007-11-05
The solution is to recompile the kernel with the patch found [here]("http://launchpadlibrarian.net/9603948/linux-2.6.22-usb-shutdown.diff"). It suspends the usb instead of shutting down the usb.

It works for me, I really hope that it will be included in the ubuntu kernel.

The launchpad bug is located [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/48773").

---

### Post by sliPrix on 2007-11-05
armalite thanks for the suggestion, I appreciate it.  I'm fairly new to Ubuntu, well Linux in general so I'm not really sure how to go about applying this patch to the kernel.  I would greatly appreciate it if somebody would please point me to a tutorial on how to do this, or post some detailed instructions on applying the patch.  I'm having trouble finding a tutorial of any sort on how to do this.  Thanks so much!

---

### Post by sliPrix on 2007-11-05
I found the file that I believe I am looking for to either edit or apply the patch (I'm not sure how this works, the file I downloaded from the previous link was .diff).  When I try to edit the file with gedit I get the following error message "Could not open the file /lib/modules/2.6.22-14-g&#8230;ivers/usb/host/ohci-hcd.c.  gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I have tried the UFT-8 and ISO-8859-15 character codings.  Any suggestions?

---

### Post by armalite on 2007-11-06
I recompiled the kernel using the instructions found here:

[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

The steps are a simpler version of these written on that link.

- I installed all required packages (i did a long ago) to compile, a command like that should be ok:

```
$ sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
```

- in a new directory, i gave (exact version could vary, you can check on synaptic which one you already have installed):

```
$ apt-get source linux-image-2.6.22-14-generic
```

after that, i patched with this command (i don't remember if you have to cd into linux-source-2.6.... directory or not, anyway it fails if it is the wrong directory):

```

$ patch -p1 < /path/to/patch.diff
```

- I copied the config file:

```
$ cp /boot/config-2.6.22-14-generic /path/to/kernel/linux-source-2.6.22-2.6.22/.config
```

- compiled the kernel with (found on link on top of my post):

```
$ sudo make-kpkg clean
$ sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

"-custom" label may be customized;

- finally installed the kernel with (exact deb name may vary depending on kernel version and custom label, the debs are in the upper folder):

```
$ cd ..
$ sudo dpkg -i linux-image... .deb linux-headers... .deb
```

The problem is: if you have restricted drivers such as nvidia drivers, you do need (as I) to recompile the restricted modules package (or to install nvidia manually). I am lazy :) so i still have to do it. Anyway good hints are at 

[https://help.ubuntu.com/community/CustomRestrictedModules]("https://help.ubuntu.com/community/CustomRestrictedModules")

If the problem persists, I am starting to think about to setup a repository and a script to automatize custom kernel patching and packaging.

---

### Post by sliPrix on 2007-11-06
armalite, I successfully did this today!  Thank you so much for your guidence, and taking the time to write a tutorial/provide the necessay links.  I really appreicaite this...this is why the Ubuntu community is so great, because people are willing to help.

---

### Post by jbysmith on 2008-01-26
The USB power not turning off during a system shutdown was driving me nuts for the longest time.  (Logitech G15 and a couple other misc devices)  Using an nForce motherboard as well, which seems to be a trend on the bugtracker.

My problem is that I'm very uncomfortable compiling kernels. I've done it a couple times, just to see if I could (with a lot of help from the Master Kernel Thread), but I'm about as comfortable doing that as doing a self-lobotomy.

On that [bugtracker](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/48773) page, near the bottom, someone has set up a repository (binary and source) with the above patch already included.  For a Linux idiot like me, it worked like a charm. I added his sources to apt and did an update.  (After rebooting I had to comment out his repo again, as it keeps wanting to update it over and over)  Afterwards, I used Envy to build the Linux drivers.  Everything worked perfectly.

Thanks for the information everyone.

---

### Post by armalite on 2008-01-27
You're welcome, jbysmith. I'm the one who set up the repository. I'm glad you found out it useful.

One thing to let everyone know: the latest kernel published in there (2.6.22-14.48~ppa1) is affected by the bug [https://bugs.edge.launchpad.net/soyuz/+bug/165230]("https://bugs.edge.launchpad.net/soyuz/+bug/165230") which generates an endlessly upgrading package. This is why everyone has to remove the repository lines from sources.list after the kernel upgrade.

This bug is fix committed, so it should go away when i'll upload the next kernel version, which will happen when another kernel pops up in ubuntu-security. I don't want to upload too many kernels because kernel compile is a lot of work and a lot of space for the Launchpad. This is the main reason why there's not yet the Hardy version, because kernels are still changing too fast.

I'll try my best to keep this repository up-to-date even when hardy will be released (or some days before), since I too need this patch (and i'm not gonna change my pc for the time being :) ).
BTW, I'm not a kernel hacker, so if the kernel has too many non-trivial changes in source code maybe I could be stuck trying to patch the kernel. I hope this doesn't happen.

---

