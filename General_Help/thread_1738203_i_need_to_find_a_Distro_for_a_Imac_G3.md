---
title: "i need to find a Distro for a Imac G3"
date: 2011-04-24
forum: General Help
---

### Post by cain071546 on 2011-04-24
I just bought a blue imac g3 slot loader and i need to find a distro to run on it for my sister

500mhz
2X 128 mb pc 133
cd drive

Debian ppc
Arch ppc
and xubuntu ppc
ubuntu 9.10 ppc

all fail to install at some point 
so i figured id ask around someone has to have a imac G3 running

any suggestions?


heres my imac
 [http://www.everymac.com/systems/apple/imac/stats/imac_500_indigo.html]("http://www.everymac.com/systems/apple/imac/stats/imac_500_indigo.html")

---

### Post by Joe of loath on 2011-04-24
With that little memory I'd want to use a minimal distro, maybe the distros you tried were too heavy. What options did you use to install each one?

---

### Post by cain071546 on 2011-04-24
i have used both desktop and the alternate install discs for
debian ppc
arch ppc
xubuntu ppc
ubuntu 9.10
ubuntu 8.10 
suse 9 ppc

all of them except 8.10 boot and begin the install process
and they all freeze at a diffrent spot
8.10 begins to boot but screen goes blank cd drive spins down

it was running osx 10.3 panther 
but it was soooooo slow that i had to dump it

---

### Post by cain071546 on 2011-04-24
I started thinking about bad RAM after having a similar problem on a PC

so i through in 2X 256 PC133 and it seems to boot and run even faster but still hangs randomly through out the install =(

---

### Post by 3Miro on 2011-04-24
Try using alternate install, the liveCD takes a lot more RAM to install. I would also try only Xubuntu and Lubuntu. If those don't work, you can try Debian.

If you feel like you can handle Arch, you can try that. It is much harder than the other distros, but it will let you build a really minimal system.

---

### Post by Joe of loath on 2011-04-25
+1 to arch, but you need some flexibility of thinking and a web browser pointed at the Arch wiki throughout the install :lol:

---

### Post by robert shearer on 2011-04-25
Lubuntu 10.04 worked for me on a G3.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by c4c on 2011-04-30
I recommend the MintPPC OS ([http://www.mintppc.org/](http://www.mintppc.org/)) for this machine if the RAM stays below 512MB - or anyway. MintPPC has gotten right to run well on older PowerPC machines from what I've seen. If you have 512MB RAM or more and want ubuntu, then I recommend Lucid Lucy 10.04. I made the guide below after realizing the problem with a straight install of ubuntu on PowerPC iMacs were three-fold; ubuntu doesn't seem to like less than 512 MB RAM to run nicely, only a straight Debian install in the beginning uses the proper disk partitioning and boot loader for the PowerPC processor and the xorg.config file must be re-tweeked for this machine.
Installation Guide
Ubuntu 10.04 &#8220;Lucid Lucy&#8221; LTS
on a PPC iMac G3 (Slot-Loading Summer 2001 500MHz) via CD
This guide assumes you are NOT making a Dual-boot, or Triple-boot machine; but a Ubuntu-only iMac.
[COLOR=Red]Apologies all - I am quite a linux noob myself and made this *after* installing on two iMacs of this type while expecting a bunch more that never arrived - so, I never actually tested this out step by step.[/COLOR]
1.Download Ubuntu 10.04 Lucid Lucy Maverick Installation .iso for PowerPC
2.Download the Debian Squeeze 6.0.0 Business Card Installer .iso for PowerPC
Why? Because Ubuntu is based on Debian and although we could use another method of properly partitioning the Apple Hard Drive (with Yaboot) for use with Linux &#8211; Debian does it &#8220;out-of-the-box&#8221; and this also allows folks to follow this guide to install a different OS like Debian itself, MintPPC, etc. 
3.Burn the &#8220;ubuntu-10.04-desktop-powerpc.iso&#8221; file to a CD at 8x (or lower)
4.Burn the &#8220;Debian/PowerPC_squeeze.iso&#8221; file to a CD at 8x (or lower)
[COLOR=Magenta]*Install Debian first to allow it to properly partition the hard drive and use the yaboot boot loader.*[/COLOR]
5.Turn on the target iMac (if different than the Mac you used to download and burn the .iso) and as quickly as possible &#8211; insert the Ubuntu 10.04 install CD and hold down the &#8220;c&#8221; key.
If you aren't quick enough (another OS loads) just power-off by holding the Power button on the front down for 5 seconds or so (shut-down properly if you like; but the CD needs to stay in the machine) wait 30 seconds to one minute and Power-On again while holding the &#8220;c&#8221; key down.
6.At the black &#8220;Boot:&#8221; screen prompt, type live <enter>, or just hit <enter>, or do nothing
7.Watch the screen go black again, this time you'll see &#8220;Ubuntu 10.04&#8221; with 4 white dots underneath that turn red-then-white-then-red. Just after this, the screen goes completely black
8.Hold down <control> + <option> + <F1>
You might have to do this more than once. You are trying to bring up a Terminal.
9.At the black &#8220;Terminal&#8221; screen prompt, type wget [http://mac.linux.be/files/xorg/imac6.txt](http://mac.linux.be/files/xorg/imac6.txt) <enter>
If following these directions for another iMac, get the Xorg.config file appropriate for your system
10.Then type sudo nano /etc/X11/xorg.conf <enter>
11.Then type <control> + <R>, then <return>
12.Then type imac6.txt <return>
If following these directions for another iMac, type in the imacX.txt file name appropriate for your system
13.Then type <control> + <O>, then <enter>
14.Then type <control> + <X>
15.At the prompt, type sudo /etc/init.d/gdm restart
16.Wait (sometimes a good long while) for the Ubuntu Desktop to appear &#8211; and fully load
17.Double-click the Install Ubuntu 10.04 LTS icon and wait...
The icon looks like a Hard Drive being attacked with an arrow by the Ubuntu symbol above it. If you don't see a spinning circle where your cursor was (for at least a second), double-click the Install Ubuntu 10.04 LTS icon again until you do. Sometimes it takes a couple of double-clicks for the installer to start. It then takes up to a minute before you actually see the installer.
18.Install.

Installing Linux on Apple PowerPC (G3-G5) Machines

1. First and always (when it doubt if it's been done - do it) hold down
Command (Apple) + Option + P + R at startup before the first chime and
until you hear a second chime. This "Zaps the PRAM" (reseting the date
and time) and Open Firmware.

2. Holding down Command(Apple) + Option + O + F... keep holding those
keys down and you'll see a white screen with some text and the 0>
prompt. This will get you into Open Firmware. This will work to get into
Open Firmware no matter what the OS is on the hard drive (it seems this
works even with a wiped hard drive with no OS at all) and whether or not
there is anything in the CD drive.

4. If there is more than one OS available - holding down the Option key
at Startup will give you boot options. Any OS on the Hard Drive(s)
should be selectable. If there is an OS CD in the CD Drive - that will
be one of the options.

5. Holding "c" with an OS CD in the CD Drive will boot the Mac from the
CD.

6. PRAM is Parameter RAM. Unlike an Intel machine, what you/others might
expect to find in the "BIOS" is found in the PRAM on Mac PowerPC

Note about the PRAM Battery - the time and date info (and not much else)
is stored in the PRAM Battery. The PRAM Battery is charged by the
computer being plugged-in. The PRAM Battery is a "1/2 AA" and it's 3.6
Volts. If you have a volt meter to test (it will HAVE to be removed
before testing) it should show between 3.64v to 3.69v or it's on it's
way out. The life expectancy of this battery is 5 years to forever if
the computer is constantly plugged in to a reliable power source. Two
popular batteries of this type are the Maxell ER3S LS14250 SBAA02 1/2 AA
Lithium Battery, or SAFT Lithium 3.6 Volt Battery LS 14250 1/2 AA -
though there are at least 6 different battery manufacturers of this
type. You CAN find these at places like Radio Shack and Batteries Plus
as long as you describe it with the actual specs, and/or bring one in to
show them. BTW, some will look different than others, but all should
measure the same size tip-to-tip. DON'T ask for a Mac or Apple battery
(this will only confuse the sales person and make it highly likely they
will tell you they don't carry it).

Note about Firmware updates. This can be a catch-22 without the proper
OS as to install the Firmware. It usually has to be running OS 9.x to
install the Firmware update. A firmware update will always reset PRAM.

Note about Debian/MintPPC/Ubuntu installs and Zapping (resetting) the
PRAM. Whenever the computer reboots before/during/just after an OS
install, hold down Command (Apple) + Option + P + R to reset the
date/time. This will avoid errors where things are being installed "in
the future."

---

