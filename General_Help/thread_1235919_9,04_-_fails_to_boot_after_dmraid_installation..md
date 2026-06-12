---
title: "9,04 - fails to boot after dmraid installation."
date: 2009-08-09
forum: General Help
---

### Post by prodigy_ on 2009-08-09
[Edit]: This problem is obsolete since 9.10 (Karmic) installs Grub2 by default.

---

I installed Jaunty recently and everything has been working well until I decided to add dmraid.

I have 3 HDDs on my current rig. 2 of them are in a fakeRAID setup (based on ICH10R) and 1 is a non-RAID disk. Since there are only NTFS partitions on my fakeRAID, I disabled it (disconnected member disks) before installing Ubuntu. I did so because Jaunty installer doesn't even ask where to put GRUB and that results in a broken MBR which already happened to me before.

So, I installed Ubuntu on the non-RAID HDD. After installation I reconnected fakeRAID HDDs and was able to boot into both Windows and Ubuntu.

A bit later I tried to gain access to NTFS partitions from Ubuntu. I installed dmraid and three things happened:

- I was able to see/mount/access partitions on the fakeRAID, so dmraid apparently worked fine;
- "Mass Storage Device" appeared in Nautilus next to "Filesystem" which probably referred to the whole fakeRAID (I couldn't open it because it gave an error message);
- I could no longer boot into Ubuntu.

All I see now when I'm trying to boot is GRUB and then "no block devices found" error message that repeats 4 times. After that nothing happens and system doesn't boot (I tried to wait for about 15 minutes). It doesn't lock up either - it responds to keyboard and reboots after Ctrl-Alt-Del. 

Also I still can boot into Windows w/o any problems. (Not surprisingly, since it's installed on another physical device.)

Any suggestions?

---

Config:
MB: ASUS P5Q Deluxe, P45/S775, BIOS Rev. 1702
HDD (2x): Seagate (ST31000333AS) 1TB, SATA-2, RAID0
HDD: Maxtor (7L300S0) 300GB, SATA-1, non-RAID
OS: Ubuntu 9.04 64-bit

---

### Post by prodigy_ on 2009-08-09
Bump.

---

### Post by prodigy_ on 2009-08-10
Well, I was able to reproduce this bug after reinstaling Ubuntu (to get the full picture I even installed Kubuntu via Wubi - with the same result).

---

Evidently no-one has any solution for this. In this regard everything is just the same as it used to be.

Bye-bye again Ubuntu. Until next time - maybe in a year with 10.4 I'll have more luck...

I'm not a Linux hater, not at all. My first Linux was free RedHat 7.1 more that 8 years ago (even before it became Fedora). It was so much fun because there you couldn't even install a single program w/o breaking apart everything else. Since then I've been returning regularly. Things have definitely improved but... even now desktop Linux remains to be a completely unsatisfactory experience. I'll give you some reasons why:

- Ubuntu is friendly but friendliness alone does not equal usability or convenience. You still (OMG, it's 2009 out there) can't even tile two windows vertically w/o using an unsupported Compiz extension. That is, both of mainstream Linux WMs are stuck in the stone age of ergonomics (you'll agree with this statement if you have a 30" monitor like me).

- Compiz is unbearably slow. I have Q9550, 8GB of fast RAM and 4870X2 and it's still slow as hell. You minimize a window and it takes 5 seconds to switch back to it. You can't even force AA to make the cube look better. And yes, I installed Catalyst 9.7 and even enabled Crossfire. (Linux fans continue to blame ATI for "not releasing a good driver" but actually I had no problems with it at all. Proprietary or not, it works. And aticonfig responds to commands just as it should, not with cryptic error messages.)

- Gnome with all effects turned off is fast but looks like it's straight out of '90s era. You can customize it of course (it's not an easy task though) but out of the box it looks much worse than the classic theme of WinXP. You get a UI where everything screams: "it's been designed by programmers and they have no clue about eye candy or good taste."

- KDE is better-looking but fragile. You can break it with literally one wrong move of your mouse. And then it's not obvious how to revert things back to default. Also instead of a stable FF 3.0.x in Kubuntu you get some Shiretoko beta. Why? And when you manually install 3.5.2 for example, its interface looks ugly (probably because of the missing Gnome resources default theme relies on). I understand that KDE developers are obsessed with Konqueror but someone needs to tell them that their "browser" is a joke. It can't even dream about competing with FF.

- Hardware support has improved greatly but it's still nowhere near it has to be. Moreover, the focus of attention is wrong. People are concerned with all kinds of imaginary problems but they seem to ignore real issues like broken GRUB/dmraid combo.

---

Sorry for this long rant. My every intention is to help the community despite the disappointment which desktop Linux continues to be.

---

### Post by CommanderKeen on 2009-10-05
It's unfortunate that this thread is entirely made up of prodigy_'s comments.  Is there a complete lack of interest in fakeRAID support, or is everyone completely ignorant when it comes to setting up and configuring a dual booting system that involves fakeRAID?  Who knows.  
 
I've been experiencing a similar problem (read about it here: [http://ubuntuforums.org/showthread.php?t=1282628](http://ubuntuforums.org/showthread.php?t=1282628))  And even trying the #ubuntu irc channel, proved frustratingly pointless.  I'll be the first to admit, that when it comes to Linux, I am a novice, but with a fairly strong background in computer hardware / software in general, I see no reason to believe these issues are difficult much less impossible to resolve, but even after scouring the internet, I have yet to find an article, howto, or tutorial that seems to address my issue.  
 
I noticed a poll a little earlier which asked for the definition of a "desktop ready" Linux.  I would have to say something that, as prodigy_ said is ergonomically friendly, but more importantly, more readily supports a wider range of hardware and software configurations.  With the help of a simple driver disk, windows will install, or recognize my RAID 1, but this ubuntu 9.04 seems confused by it, no matter what I throw at it.

---

### Post by rars on 2009-10-12
Hello prodigy_ and CommanderKeen,

I understand your problems and claim for lack of support, but sometimes problems are a little just to specific.

And yes, there is not much information regarding your problem.

I too had the same problem, and I'm still trying to solve part of it.

Well, for the first part of the problem,

@prodigy_

if you are still interested in resolving the problem just type:

"dmraid -ay"

when you enter that boot line saying "No blocks found"

then type "exit"

or if you prefer : "dmraid -ay;exit"

This will mount your raid disk automatically, and continue to boot. 

My problem now is how to put this "raid mounting" automatically... :P

I'm trying in the rcX.d directories, and when I found out something I'll come back here just to say the result.

And also... if you want to install ubuntu in raid disks just do the same thing, when in partitioning the disk and the raid does not appear, go to the command line (there is an option to that) type "dmraid -ay", then type "exit" and ask installer to find again the disk. And voila... they are there!

Regarding the rest of Linux flame... Well it may not be the best... but it is free... If you have the money to pay go for the other solutions, I also use other operating systems and Linux Operating Systems. Each one is good for its things... ;)

---

