---
title: "Installing Ubuntu on a Virus Laden with Viruses"
date: 2010-03-30
forum: General Help
---

### Post by Atzeng.Dresith on 2010-03-30
So here is the current situation I'm in I have a 4 year old desktop that I built from the ground up that a while back got heavily infested with viruses, so much so that the OS no longer loads. I am currently trying to fix the computer by doing a clean install of Ubuntu, I have a correctly burned Ubuntu disc, however, when I go to use it I get nowhere. It will start the download(or so it appears) but then it will do nothing. It will eventually just cut the signal to my monitor. I have tried both the Install Ubuntu option and the Try Ubuntu Live Without Changing your OS options but neither will work. I would very much appreciate any help at all.

---

### Post by uRock on 2010-03-31
What are you system spec? CPU, GPU, and RAM

---

### Post by oldfred on 2010-03-31
IF it is turning monitor off it may be a video issue. What video card are you using.

I have not had problems for so long I have forgotten but usually you can hit an f key to add boot options like xforcevesa or noapic, they used to have vga= a number for the max range but the probing is so good now it is rarely a problem.  You may have to search for your video card and the problem to find the setting.

My machine is 3 years old but I have a newer nvidia card that works without any issues ( until lucid then I had it turning off monitor also).

---

### Post by uRock on 2010-03-31
> **oldfred said:**
> IF it is turning monitor off it may be a video issue. What video card are you using.

I have not had problems for so long I have forgotten but usually you can hit an f key to add boot options like xforcevesa or noapic, they used to have vga= a number for the max range but the probing is so good now it is rarely a problem.  You may have to search for your video card and the problem to find the setting.

My machine is 3 years old but I have a newer nvidia card that works without any issues ( until lucid then I had it turning off monitor also).

F4 for safe graphics mode.;)

---

### Post by Atzeng.Dresith on 2010-03-31
First off sorry for ths shitty typing on the title. Second its a older AMD CPU with a ATI graphics card. Also I am currently hooking the monitor up via a s-video cable to a TV, the video works just fine up until I get some garble after hitting the install option. Still even if I leave the computer running for hours nothing will happen. Its almost as if there is a problem with the Installation process itself, after the garble it cuts the monitor signal and the cd stops spinning. In a second I'll try to write down everything that is said before it stops working.

---

### Post by Mark Phelps on 2010-03-31
I'm pretty sure that you can't do an install of Ubuntu with using a S-video cable hookup to a TV.  The installer uses generic drivers which most probably, can't use the s-video port or TV-based resolutions.

You would need to hood up a standard monitor to do the install.

---

### Post by Atzeng.Dresith on 2010-03-31
Actually, Lovely enough it did, I now have a fully operational machine, It only started working after turning on Graphically Safe Mode. Danke to whoever Suggested that.

---

### Post by ricyaun on 2010-03-31
Quick question - I read everywhere there are no known linux viruses in the wild?

Second Point - This is a malware question - so standard procedure in a reinstall due to malware is delete the partitions manually.  Don't rely on automated process.

Third Point - WIPE the drive.  Malware can be located in the area between the partitions which is why the manual delete and then wipe.

Fourth Point - If you still have problems when you previously had a good installation then the only thing left is MBR and BIOS.  Both of which can contain, in the case of Linux, root kits.  If this the case then chances are they are supporting each other.  Remember we are not as much talking about what as who did this.

So do this.  1st use a utility like Recovery Console on a Windows Install CD to rewrite the MBR after the partitions are deleted, and the drive is wiped.  Run fixmbr.  Then set the CMOS Clear jumper for clear and leave it.  Remove the CMOS Battery, and wait for residual charge on the capacitors to die down, 15 minutes.  Also pull the RAM out of their connectors to make sure they clear.  This clears the menus, and forces the BIOS into emergency mode.  Then reinstall the battery,and RAM, and  reset up the CMOS menus, and try to boot up on the Live CD.  Watch the boot process completely.  If you see IO errors indicating buffer overflows then something of the root kit remains, but is likely damaged.  See if the machine will boot all the way into Linux with a desktop.  If it will then try an install.  If you have any problems with the install like your monitor reporting out of range, or the machine wants to reboot at a certain point then boot back up onto the desktop on the Live CD, and install from there.

If any crash report happens then definitely make the crash report because the Ubuntu teams need the info.  Accompany this by going onto launchpad with an explanation.

This hard won info.  If you have any questions my account is setup to have members email me.

Also faulty memory can produce a similar event, but these Linux root kits are big on reconfiguring the memory to produce instability in OS.  So test your memory with the Ubuntu Live CD after going through the process.  

Good Luck:

---

### Post by realzippy on 2010-03-31
*Both of which can contain, in the case of Linux, root kits*

ehm.really?

---

### Post by ricyaun on 2010-03-31
Oops I didn't see the part where you got it working.  What I said though is still relevant.
How do you turn on the graphically safe mode?  I would like to know that.  That may be a way of defeating these root kits.

OK I see F4 on the Installation Menu will do this.  Great news I will try this on the next instance I find where the monitor reports Out of Range when the resolution on the monitor is definately in range.

Thanks iRock

---

### Post by ricyaun on 2010-03-31
> **realzippy said:**
> *Both of which can contain, in the case of Linux, root kits*

ehm.really?

Yeah really.  When in the case of these root kits they can also propogate to other machines that have no other common connection than the router.  I stress are not networked together, and the attacking machine does not need to be turned on.  Only plugged in to the wall socket.

Remember the BIOS is nothing more than the firmware that configures the System Control section of the motherboard.  If modified then the Switched 5VDC power supply can remain on allowing the RAM and the buses, and chip enable lines to stay active.  With no 12VDC active the fans will not run, and neither will the hard drive.  So no external indication the machine is still active.  With the LAN card still running, buses, and enable lines active, and the RAM providing the bulk space needed for the software a machine that appears off can attack another machine.  What I don't know yet is if the target machine also has to be on.  More than l;ikely it has to be because the Switched 5VDC power supply must be up and running.

Ric Yaun

---

### Post by uRock on 2010-03-31
> **ricyaun said:**
> Quick question - I read everywhere there are no known linux viruses in the wild?

Second Point - This is a malware question - so standard procedure in a reinstall due to malware is delete the partitions manually.  Don't rely on automated process.

Third Point - WIPE the drive.  Malware can be located in the area between the partitions which is why the manual delete and then wipe.

Fourth Point - If you still have problems when you previously had a good installation then the only thing left is MBR and BIOS.  Both of which can contain, in the case of Linux, root kits.  If this the case then chances are they are supporting each other.  Remember we are not as much talking about what as who did this.

So do this.  1st use a utility like Recovery Console on a Windows Install CD to rewrite the MBR after the partitions are deleted, and the drive is wiped.  Run fixmbr.  Then set the CMOS Clear jumper for clear and leave it.  Remove the CMOS Battery, and wait for residual charge on the capacitors to die down, 15 minutes.  Also pull the RAM out of their connectors to make sure they clear.  This clears the menus, and forces the BIOS into emergency mode.  Then reinstall the battery,and RAM, and  reset up the CMOS menus, and try to boot up on the Live CD.  Watch the boot process completely.  If you see IO errors indicating buffer overflows then something of the root kit remains, but is likely damaged.  See if the machine will boot all the way into Linux with a desktop.  If it will then try an install.  If you have any problems with the install like your monitor reporting out of range, or the machine wants to reboot at a certain point then boot back up onto the desktop on the Live CD, and install from there.

If any crash report happens then definitely make the crash report because the Ubuntu teams need the info.  Accompany this by going onto launchpad with an explanation.

This hard won info.  If you have any questions my account is setup to have members email me.

Also faulty memory can produce a similar event, but these Linux root kits are big on reconfiguring the memory to produce instability in OS.  So test your memory with the Ubuntu Live CD after going through the process.  

Good Luck:

The viruses were on Windows, not ubuntu. THat said, the HDD was formatted.

When the install disk is first started hit F4 when the menu comes up, then you can use safe graphic mode.

OP, I am glad this worked for you, welcome to the land of ubuntu and feel free to start a new thread if you have any questions.

---

### Post by ricyaun on 2010-03-31
Some how my answer to RealZippy created a new thread.  I am new to this.

It goes like this.  I have witnessed all of this with my own 2 eyes.  

Also a machine with one of these root kits can propagate to other machines as long as they have at least a router connection common.  They don't have to be networked.

The BIOS is just computer lingo for the firmware that configures the System Control section of the motherboard.  If the Switched 5VDC power supply stays on but the 12V power is turned off then no fans or HDD run giving no external indication of the machine still being active.  With malware residing in the RAM instead of the HDD the machine can then spread the malware to other machines.

I have personal experience with this.  Once a machine is infected usually through an app like HP Update which can't be turned off the machine can then infect other machines, and allow hostile penetration without leaving any IDS logs or showing any firewall cracking.  Leaving the home or corporate or government user or IT person wondering where this actually came from.  This creates situatuions like the power blackout in south Forida a couple of years ago where it is known that it was a "Hacker" actually Black Hat, but doesn't know where the person came from.  So it is always assumed that a "Chinese Hacker" did it.  But really the authorities don't know where it came from or who did it.  Just blame the Chinese.

This is not info that has been released by the gov.  I have had an up close and very personal look at this.  I am not a conspiracy nut either.  I sure haven't enjoyed the close look I have had either.  I never wanted to have this knowledge.

Ric Yaun

---

### Post by ricyaun on 2010-03-31
Some how my answer to Realzippy is going into a new thread.  I am new to this.

---

### Post by uRock on 2010-03-31
Why do you keep repeating yourself?

---

### Post by pbrane on 2010-03-31
> **ricyaun said:**
> Quick question - I read everywhere there are no known linux viruses in the wild?

.....

Fourth Point - If you still have problems when you previously had a good installation then the only thing left is MBR and BIOS.  Both of which can contain, in the case of Linux, root kits.  If this the case then chances are they are supporting each other.  Remember we are not as much talking about what as who did this.

.....

Good Luck:

The current consensus is that there are no known malware/virus threats to a modern Linux system at this time in the wild. I think a lot of it has to do with how fast security vulnerabilities are fixed.

On point four, could you explain or provide links to this information. I doubt that linux is the only OS vulnerable to root kits and BIOS re-flashing. The MBR is also not Linux only. There are far more rootkits for Windows than for Linux.

---

### Post by ricyaun on 2010-03-31
BIOS root kits are generic to the OS.  MBR root kits maybe also.  However the MBR root kits may have to be supported by file in Windows called mbr.sys which is not present in a healthy Windows install.  

An attack on a Windows OS can be accompanied by a bug like this to prvent the target from switching over to Linux to escape the the attacks.

I have alot of experience over the last 9 months with all of this, and have alot to communicate to the Linux community.  I am not much of a joiner, but I have joined this forum and I am learning how to get around in the forum before I do create a thread for this discussion.  I have so much to tell the community.  Specially after reading some bug reports on Launchpad.  I recognized alot of what I was seeing as their work.

It will probably be in the next couple of hours I will create the thread, and hopefully have an extensive and intelligent discussion with plenty of smart computer savvy people participating.

---

### Post by ricyaun on 2010-03-31
I am new to this.  In fact this is my first attempt at having a conversation in a forum with anybody.  I am fairly self reliant so tech forums are not something I have any experience with.

Please bear with me while I get the hang of it.

Ric Yaun

---

### Post by uRock on 2010-03-31
Please feel free to start your own thread in the [Security Discussion sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=338").

Thanx,
Ronnie

---

### Post by ricyaun on 2010-03-31
Thanks for the suggestion.  I never heard of xchat before. I will investigate.  I thought I was in ubuntuforums.  By #ubuntu do you mean ubuntu.org?  I would love to give the Ubuntu teams this up close and personal knowledge I have.  I also have about 80GB of these guys data they want back very badly.  I can't open it, and tried to wipe it so they would go away, but they have only gotten worse.  Wish I hadn't wiped it.  Now I need to do a rollback on my hdd to get it so I can somehow open it.  I am certain we will all get a really good loojk at some surprising things.

---

