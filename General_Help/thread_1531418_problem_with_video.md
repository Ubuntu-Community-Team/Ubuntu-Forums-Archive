---
title: "problem with video"
date: 2010-07-15
forum: General Help
---

### Post by meburke on 2010-07-15
I thought I'd already posted this problem. Pardon me if it shows up twice:

Since I updated my system yesterday, I've had video problems.

When I expect a login window, what I get is distorted white stuff at the top of the screen. I hear the drum beat that usually accompanies the login screen, and I can login blindly, but I can't get a desktop or Xwindows session.

I can CTL=Alt-F1 once, and log into a terminal session. the ps copmmand shows what I expect to be running. When I use Alt-F7 to get back to the Xwindows session I get a black screen. When I try to go back to the terminal session, I get a message "input Not Supported" and I have to reboot.

The lspci command shows: 00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

The xorg.conf file shows:
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"		"uxa"
	Option		"EXAOptimizeMigration"	"true"
	Option		"MigrationHeuristic"	"greedy"
	Option		"Tiling"		"true"
EndSection
I know this is the new format, but I have no idea what the "old format" should be for this selection.

I have tried to fix these problems by changing the sources.list using my LiveCD, and then runnning some updates and suggested fixes I found on the web from the recovery mode command line.

1. What do I need to do to restore my old "Configured Video Device?"

2. Where can I find the repository for the xserver-org-video-intel installation?

3. Is there a dpkg for xserver.org that I can load, install and reconfigure if I have to?

Thanks,

Mike

---

### Post by meburke on 2010-07-15
Updating the problem description:

debian-reconfigure xserver-xorg didn't work.

apt-get install xserver-xorg-video-intel says I have the newest version.

apt-get install xserver-xorg-video-intel-2.4 says there are dependencies that aren't going to be installed. This may be something to work on, but I don't think this is the way to go.

It looks like I'm looking for a way to change the xorg.conf file to reflect my actual driver and chipset.

Thanks,

Mike

---

### Post by meburke on 2010-07-15
OK, I tried running xrandr but couldn't open the display (duh!), so I ran the low res graphics option from the recovery mode menu, and danged if it didn't recover the 1680x1050 resolution of my screen and I got my desktop back!

Of course, when I reboot the system I still have the original problem I was asking about. I'm not able to reconfigure the system automatically from recovery mode..it can't generate a configuration file.

At least I can use the system if I'm willing to boot through the recovery mode option in GRUB. Now I need to speed the thing up; hulu runs real slow and jerky. However, it's 3:30AM and as long as I can actually use the system again, I'm going to bed.

Still open for suggestions on fixing this problem.

Thanks,

Mike

---

### Post by meburke on 2010-07-15
OK, I guess we can mark this one as SOLVED, but I don´t know how to change the title automatically...

I simply moved the files I needed to save over to my /home directory (which I maintain on a separate partition), and re-installed Karmic from my LiveCD. There is something good to say about running my programs from my home directory; I can be productive faster if I don have to install everthing on the main filesystem. I´m sure there is a better way, but I needed to get back to productivity.I will upgrade piecemeal this weekend, and see if I can discover what broke XWindows. I will no doubt make snapshots using dd so I can restore and make comparisons. Apparently this is not a trivial or unknown type of problem, especially in Lucid.

Thanks,

Mike

---

