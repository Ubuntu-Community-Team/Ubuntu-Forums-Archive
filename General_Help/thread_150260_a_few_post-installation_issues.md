---
title: "a few post-installation issues"
date: 2006-03-25
forum: General Help
---

### Post by Latem on 2006-03-25
1. Kubuntu doesn't seem to be keeping my resolution setting at all. I setup my resolution to be 1400x1050 @ 85 Hz.  When I log out, it resets the resolution to something bigger.  When I log back in, it keeps the new big resolution, and never switches to the one I selected.  This also causes the fonts to be messed up somehow, and are larger than they should be (at least the menu fonts) once I switch back to my resolution.

2.  I have Sound Blaster Live! sound card, plus an onboard sound card.  I use the SB card in windows, and I would like to do the same thing in Kubuntu.  However, no matter what, it seems to want to use the NVidia motherboard audio.  In Sound Settings I have 6 choices:

Midi Through Midi Through Port-0 - ALSA device
EMU10K1 MPU401 (UART) EMU10K1 MPU401 (UART) - ALSA device
Emu10k1 WaveTable Emu10k1 Port 0 - ALSA device
Emu10k1 WaveTable Emu10k1 Port 1 - ALSA device
Emu10k1 WaveTable Emu10k1 Port 2 - ALSA device
Emu10k1 WaveTable Emu10k1 Port 3 - ALSA device

No matter what I pick from these, the sound doesn't work through my sound card.  My speakers have to be plugged into the mobo audio.   Even in KMix, in the drop down it says SBLive [Unknown].  There is also NVidia nForce2, but SB is selected.

Related to this issue, my brothers account (which was created later after install) gives error when logging on that he doesn't have permissions for sound and device /dev/dsp or something similar. and KMix is disabled for him.  

I know SBLive should work in Linux, because it worked in Mandriva.  It was Emu10k1.  Although that was a different computer, that didn't have onboard audio.

My system:

CPU: AMD Athlon XP 3200+ 512K 400FSB BARTON SOCKET A CPU
 Motherboard: DFI Infinity NForce2 Ultra400 Socket A Dual DDR AGP 6PCI SATA Sound Lan 1394
 Video Card: ATI Radeon 9800 PRO 256MB
 RAM: 2 x Samsung 512MB PC3200 DDR400 RAM (I can&#8217;t get 3 sticks to work =[ )
 Hard Drive 1: Seagate Barracuda 7200 80GB HD ATA/100 HD with Windows
 Hard Drive 2: Samsung 40GB HD ATA/100 HD with Kubuntu 5.10
 Sound Card: Creative Sound Blaster Live! 5.1
 Monitor: Viewsonic G90FB 19IN
 DVD-RW/CD-RW: Liteon DVD+-RW DUAL 8X4X/8X4X CDRW 40X24X30X
 Mouse: Microsoft IntelliPoint Optical Scroll Mouse
 Speakers: Creative 2-piece speakers
 Power Supply: 350W

Any help regarding these issues is much appreciated. Thanks,

Latem

---

### Post by Barrakketh on 2006-03-25
[QUOTE=Latem]1. Kubuntu doesn't seem to be keeping my resolution setting at all. I setup my resolution to be 1400x1050 @ 85 Hz.  When I log out, it resets the resolution to something bigger.  When I log back in, it keeps the new big resolution, and never switches to the one I selected.  This also causes the fonts to be messed up somehow, and are larger than they should be (at least the menu fonts) once I switch back to my resolution.[/quote]
There's a checkbox that says something like "Apply these settings when I log in", so make sure it's checked.

> 2.  I have Sound Blaster Live! sound card, plus an onboard sound card.  I use the SB card in windows, and I would like to do the same thing in Kubuntu.  However, no matter what, it seems to want to use the NVidia motherboard audio.
Disable the onboard audio either through the BIOS or a jumper on the motherboard.
> my brothers account (which was created later after install) gives error when logging on that he doesn't have permissions for sound and device /dev/dsp or something similar. and KMix is disabled for him. 
He needs to be a member of the audio group.

---

### Post by Latem on 2006-03-25
Thanks for the quick reply.  The resolution issue is fixed now.

> Disable the onboard audio either through the BIOS or a jumper on the motherboard.

That's a bit extreme, is that the only way?  

> He needs to be a member of the audio group.

Ok, I've put him in all the secondary groups as me.  He is able to hear audio now.  However, he can't seem to get to administrator mode in some (if not all) of the settings like the hard disks/mount points config page, or users management page.  How can he be able to get into administrator mode as well?  He is in the same secondary groups as me, including adm and admin secondary groups.

Some more questions:

1.  On my other HD, I have Windows XP.  It is partitioned with NTFS.  Is there any way I can get read access to this.  I've been told it should be possible.  In the Hard disk management settings utility, I can't edit or modify that line.  Do I need to modify fstab manually maybe?  

2. I've read how to do the following somewhere before, but I can't seem to find it now.  How can I put the "Home" and "Trash" on my desktop?

3. To change my home page for my web profile do I do the following: Open Konqueror from the Internet menu, or from the taskbar, then in Tools | Settings change the home URL, and then do Save View Profile "Kubuntu Web"... in Settings?

Sorry for all newbie questions. Thanks for all the help.

Latem

---

### Post by Barrakketh on 2006-03-25
[QUOTE=Latem]That's a bit extreme, is that the only way?[/quote]
That's actually the normal way.  Unless you're using your PC to produce music with two sound cards is something of an oddity (exception: USB headsets).  Onboard audio doesn't like to play nice most of the time.  Plus I'm not sure how ALSA determines which sound card to use :-? 

> Ok, I've put him in all the secondary groups as me.  He is able to hear audio now.  However, he can't seem to get to administrator mode in some (if not all) of the settings like the hard disks/mount points config page, or users management page.  How can he be able to get into administrator mode as well?  He is in the same secondary groups as me, including adm and admin secondary groups.
admin is the group that gives access to sudo, and for some reason the "Administrator mode" button doesn't always work.  A temporary workaround is to launch kcontrol using "kdesu".
> 1.  On my other HD, I have Windows XP.  It is partitioned with NTFS.  Is there any way I can get read access to this.  I've been told it should be possible.  In the Hard disk management settings utility, I can't edit or modify that line.  Do I need to modify fstab manually maybe?
I always edit fstab.  Assuming there is no mount point for it, your fstab entry for it should look something like this:
```
/dev/hda1      /mnt/hda1    ntfs    defaults,user,ro,umask=000     0     0
```
> 2. I've read how to do the following somewhere before, but I can't seem to find it now.  How can I put the "Home" and "Trash" on my desktop?
Open a terminal and switch to your desktop.  Open trash.desktop and change "NoDisplay=true" to "NoDisplay=false".  Save it.

For your "Home", right click on the desktop and Create New -> Link to Location (URL).  Name it home and fill in the path to your home directory.

> 3. To change my home page for my web profile do I do the following: Open Konqueror from the Internet menu, or from the taskbar, then in Tools | Settings change the home URL, and then do Save View Profile "Kubuntu Web"... in Settings?
I actually use Opera for my web browser:-D  Give me a lil while and I'll look up how to do that :)

EDIT:  Visit the page you want to be your home page, and choose Settings -> Save View Profile $foo

---

### Post by Latem on 2006-03-25
Ok, I've tried to add the windows partition to fstab.  I did 
```
kdesu kate /etc/fstab
```
and pasted the line at the end of the file.  Restarted the computer.  Now on bootup the "Mounting local filesystems" line fails, and in the Settings | Disk Management section the line for the partition is disabled.  I am also having serious troubles doing anything as su now.  In the Settings "Administrator Mode..." never seems to work.  If I do 
```
kdesu <command>
```
from terminal it always just hangs, and I have to Ctrl+C.  Afterwards, Administrator Mode... in settings hangs as well.  So I am not sure if I can do anything as su right now. I am not sure what's up.  Any advice is much appreciated.  

Otherwise I got other things  working so far.  SBLive is working after disabling onboard audio in BIOS.  Trashcan .desktop file had Hidden=true, and setting that to false made it appear on desktop.  

Thanks,
Latem

---

### Post by Barrakketh on 2006-03-26
[QUOTE=Latem]Ok, I've tried to add the windows partition to fstab.  I did 
```
kdesu kate /etc/fstab
```
and pasted the line at the end of the file.[/quote]
That's your problem.  I said "your fstab entry for it should look something **like this.**"

Use "fdisk -l" to find out which partition is your NTFS one.  Create a mount point for it in /mnt/ (need to use sudo for it).  Then alter the first part (/dev/hda1) to point to whatever you got from fdisk, and the second part (/mnt/hda1) to whatever you named the mount point.

> I am also having serious troubles doing anything as su now.
Open a terminal and type "sudo -s".  Type in your user password.  If you get the root prompt (# instead of $) you still have "root" access.
> In the Settings "Administrator Mode..." never seems to work.
I never use the "Administrator Mode..." to be honest.
> If I do 
```
kdesu <command>
```
from terminal it always just hangs, and I have to Ctrl+C.  Afterwards, Administrator Mode... in settings hangs as well.  So I am not sure if I can do anything as su right now. I am not sure what's up.  Any advice is much appreciated.
Try "sudo killall kdesu".  Give it a try again.

---

### Post by Latem on 2006-03-26
With regard to my NTFS partition, I think the main problem was that I didn't create /mnt/hda1.  I created /mnt/hda1 as sudo -s, and then did kdesu systemsettings, and enabled the line, and it works now.  /mnt/hda1 gives my windows.  Also it worked on reboot, and there were no error messages.  

sudo killall kdesu and/or relogging seemed to fix my kdesu problem.  However, my Administrator Mode button still doesn't seem to work, although it did seem to work well before.  I am not sure.  So am I always suppose to do kdesu systemsettings?  Or how should I go around this problem?  Do others get it?
When I did kdesu systemsettings it looked all funny and weird and bad, and not in my normal style.  It also printed out a lot of stuff to the console.   Is this normal?

Thanks for all the help.

Latem

---

### Post by Barrakketh on 2006-03-26
[QUOTE=Latem]sudo killall kdesu and/or relogging seemed to fix my kdesu problem.[/quote]
Sometimes some kdesu processes hang around.  Normally when an application that uses it doesn't launch, a second attempt works.  Something intermittent like that is kind of hard to track down =\
> However, my Administrator Mode button still doesn't seem to work, although it did seem to work well before.  I am not sure.  So am I always suppose to do kdesu systemsettings?  Or how should I go around this problem?  Do others get it?
TBH, that's another weird thing.  I'm 99% sure that "Administrator Mode..." just uses kdesu to get permissions, which would explain a few things...Another thing I should mention is that that System Settings is something that is developed for Kubuntu (like Adept) and isn't an official project of the KDE Team.  I personally just stick with KControl because I'm more familiar with it anyway.
> When I did kdesu systemsettings it looked all funny and weird and bad, and not in my normal style.  It also printed out a lot of stuff to the console.   Is this normal?
Yes.  GUI applications normally print information to stdout and stderr, and if you were to have done "kdesu systemsettings" from the run dialog, you would've never noticed.  It happens to help when you're debugging an application :)

The reason why it looked different is because it was reading the preferences (that controls things like the Qt style and font sizes) from root's home directory, not yours.

---

