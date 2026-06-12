---
title: "Remote desktop before login?"
date: 2011-08-13
forum: General Help
---

### Post by taylorkh on 2011-08-13
I have a PC running Ubuntu 10.04 with vino to share the desktop.  After I login to the PC I can connect to it from another PC (again 10.04) with the vinagre Remote Desktop Viewer.  Canonical has made this rather easy to configure.  However, I cannot connect to the remote PC and use the Desktop Viewer to login to the remote PC. 

Short of ripping out vino and installing vnc or tightvnc is there a way to configure Ubuntu's desktop sharing to allow me to connect to the remote PC and then login?

TIA,

Ken

---

### Post by sbraz on 2011-08-13
there was a way, but it has been removed from recent ubuntu distros a long time ago. i tried very hard to reenable **XDMCP** in 10.04 and 10.10 with no success so i gave up. :(

the easy fix is to make your user login automatically.
if you want your screen to stay locked on boot, add a script with **gnome-screensaver-command -l** to start your screensaver and lock the computer. :)

---

### Post by taylorkh on 2011-08-13
Thanks sbraz.  I used to do the autologin thing with my headless 8.04 server. Unfortunately that did not work with 10.04. It would not boot without the monitor and if I left a monitor connected it would not autologin unless I manually unlocked the keyring or some such crap. It is now running command line and I administer it thusly over ssh or with webmin.  As to the PC I am working with autologin is not something I want to do on a portable computer.

That said... I was provided with some instructions here [http://www.linuxquestions.org/questions/showthread.php?p=4442147&posted=1#post4442147](http://www.linuxquestions.org/questions/showthread.php?p=4442147&posted=1#post4442147) which I may try.

Thanks again,

Ken

---

### Post by sbraz on 2011-08-14
ahhhhhhh so there is a way to make xdmcp work after all.
thanks for the link. :)

> **taylorkh said:**
> **It would not boot without the monitor** and if I left a monitor connected it would not autologin **unless I manually unlocked the keyring**
both problems are solvable.

as for the monitor, Xorg _must_ have a screen and i think a keyboard connected.
i've found this link:
[http://forums.whirlpool.net.au/archive/1219956](http://forums.whirlpool.net.au/archive/1219956)
editing /etc/X11/xorg.conf you can create a dummy device.
```
Section "InputDevice"
	Identifier	"Dummy Input"
	Driver		"void"
EndSection
Section "Device"
	Identifier	"Dummy Video"
	Driver		"dummy"
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Dummy Video"
EndSection
Section "ServerLayout"
	Identifier	"DefaultLayout"
	Screen		"Default Screen"
	InputDevice 	"Dummy Input"
EndSection
```
read the link for further info.
you should also try passing **nomodeset** to the kernel boot parameters.



as for the locked keyring you can read this
[http://ubuntuforums.org/showpost.php?p=9048669&postcount=4](http://ubuntuforums.org/showpost.php?p=9048669&postcount=4)
and google for **ubuntu unsafe storage**.

---

### Post by taylorkh on 2011-08-14
Thanks sbraz for the good info on xorg.conf.  After running 8.04 on the server for almost 3 years the install of 10.04 was a total fiasco.  It would not install from a PATA optical drive to an SATA hard drive (that has been documented as a bug). Then the issue of not booting headless and the issues connecting with remotely/autologin.  Enough was enough. 

It works fine now. It is basically just a LARGE hard drive (5 TB) with Samba and a few tightly locked down nfs exports. I may take a look at 11.04 LTS when it comes out. More likely when I need to upgrade it I will go with CentOS. The Canonical philosophy "if it works, break it" is getting a little old.

Ken

---

### Post by mendhak on 2011-08-14
> **taylorkh said:**
> I have a PC running Ubuntu 10.04 with vino to share the desktop.  After I login to the PC I can connect to it from another PC (again 10.04) with the vinagre Remote Desktop Viewer.  Canonical has made this rather easy to configure.  However, I cannot connect to the remote PC and use the Desktop Viewer to login to the remote PC. 

Short of ripping out vino and installing vnc or tightvnc is there a way to configure Ubuntu's desktop sharing to allow me to connect to the remote PC and then login?

TIA,

Ken
I had tried this a while ago, and the solution that worked for me was to first go to my networks and 'share the network with all users'.  You'll see this if you edit connections from your panel.  

Then, I had set up an SSH server on the box I wanted to remote into.  

Finally, when I wanted to remote in, I'd connect via SSH (the main box was logged out at this point), then I'd run 

sudo x11vnc

and then connect over TightVNC.  I realize you don't want to use TightVNC, but figured I'd mention what eventually worked for me.

---

### Post by sbraz on 2011-08-14
> **taylorkh said:**
> It is basically just a LARGE hard drive (5 TB) with Samba and a few tightly locked down nfs exports.

5TB? O__O i don't have that storage available stacking all the new/in_use drives at the computer shop where i work! :D nice.
gpt partition table with a huge partition or a classic mbr with "little" ones?

>  I may take a look at 11.04 LTS when it comes out. More likely when I need to upgrade it I will go with CentOS. The Canonical philosophy "if it works, break it" is getting a little old.
unless proven wrong i think the next LTS will be 12.04.
anyway if you want "solid" i usually recommend debian, but maybe i'm a little attached to apt-get and .deb to name other great distros.
i have debian-testing/unstable or mint-debian-edition in my future: both **rolling distros** (arch is another one) = NEVER to upgrade, always up to date, some hassles here and there, plus i still learn stuff almost 100% compatible with ubuntu for work. :) too bad canonical won't budge in that direction. :(

---

### Post by taylorkh on 2011-08-14
Thanks mendhak.  Been there, done that. I had replaced vino with x11vnc on an old box as vino was sucking up 99.9% of the CPU. For the case at hand I don't really want to go that far. I simply fire up the PC, login and then go over to my main workstation and connect. Just looking to save a step.

Yes sbraz, 5 TB is more than the data center at the Fortune 250 company I used to work at had not too many years ago.  The server is an old Dell Poweredge 400 SC. Got it for $299 after rebate.  It came with 128 MB RAM (now 2.5 GB) and an 80 GB drive.  The 80 GB drive went into my desktop PC and I installed the 40 GB from the PC and a 320 GB Seagate Barracuda in the server. Then replaced the 40 GB with another 320 Barracuda. Then I got a deal on a 1 TB Western Digital Green Caviar and replaced on of the Barracudas then another deal and replaced the second 320 with a 1 TB. 

Then a deal on a 1 TB WD Black Caviar (high performance) which went into my new desktop PC along with a 10K RPM Veliciraptor as an OS drive. Then I got a really good deal on a 2 TB WD Caviar green ($65 as I recall). I purchased a SATA controller card and installed it in the server so I could connect more than 2 drives. I then installed the Black Caviar as the OS drive (+ some storage), the 2 green Caviars as a (manually) mirrored set and the 2 TB for some more storage. 

And now I can get a 3 TB USB external drive for about $100 and could do away with the server. Less space and less power. What can you do?

That said the 5 TB of storage cost me less that my first hard drive. It was a 42 **M**B Seagate MFM drive.  It cost $399 and that was a real deal at the time!

Ken

---

