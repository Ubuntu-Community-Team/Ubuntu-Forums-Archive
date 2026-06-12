---
title: "Help : Several Ubuntu/Linux questions."
date: 2010-02-22
forum: General Help
---

### Post by hithisisatempaccount1532 on 2010-02-22
Good evening my valued Ubuntu community. I unfortunately can't say I will be here for long but I will always continue to thrive towards using Linux primarily.

For this specific thread I have a few questions,

When initially installing Ubuntu and having selected the ENTIRE drive to overwrite and format, does Grub automatically install itself and write over the existing MBR/Partiion table?

In Ubuntu, why does it seem that Firefox cannot properly display Flash Objects properly? Relating to Firefox, it also takes constant reloading/page requesting. (This is in a VM, could be the issue maybe?)

Also, on another PC that has over 256MB of RAM, when I try to run the Live CD Desktop x32 version it begins to load with the signature Ubuntu logo but then spasm's out with a pink screen that flickers to white vertical stripes going through it.

This is relating to Windows (Vista+)/Ubuntu - When performing either the 'bootrec /fixmbr' command or the equivalent in Linux, does it entirely overwrite the MBR or does it only overwrite when a problem is detected? If it does overwrite it, would this eliminate all problems in the MBR (including malware/viruses).

By the way, I am aware that Linux is immune to MBR viruses as it has excellent security implementations but in theory it is possible as installing a driver on Linux could do such or going from Windows to Linux with an infected MBR.

Oh, and one more thing... for Ubuntu 9.10 on the PS3 using alternative setup, the drive must be formatted as Ext3 which then disables most software programmed for the Linux kernel to become invalid and not supported... does YDL somehow fix this? Would you suggest installing YDL on the PS3 rather than Ubuntu (I love Ubuntu on the PC's but it seems the PS3 port just isn't cutting it)?

Many, many, many thanks to anyone and everyone whom responds to this. All constructive responses are GREATLY appreciated.

And most important of all, keep up the great work. The Ubuntu (Linux too) community makes it one of the greatest software types in development.

---

### Post by hithisisatempaccount1532 on 2010-02-22
Sorry for the bump but, I really need these questions answered. :'(

---

### Post by hithisisatempaccount1532 on 2010-02-22
Yet another pathetic bump.

---

### Post by louieb on 2010-02-22
> **hithisisatempaccount1532 said:**
> 
When initially installing Ubuntu and having selected the ENTIRE drive to overwrite and format, does Grub automatically install itself and write over the existing MBR/Partiion table?
yes.
> 


Also, on another PC that has over 256MB of RAM, when I try to run the Live CD Desktop x32 version it begins to load with the signature Ubuntu logo but then spasm's out with a pink screen that flickers to white vertical stripes going through it.How much more that 256MB? The live CD requires 384 MB or more.
> 

This is relating to Windows (Vista+)/Ubuntu - When performing either the 'bootrec /fixmbr' command or the equivalent in Linux, does it entirely overwrite the MBR or does it only overwrite when a problem is detected? If it does overwrite it, would this eliminate all problems in the MBR (including malware/viruses).
only the 1st 466 bytes are overwritten.  Vista reserves ~1066 sectors - can't recall the exact number - plenty of room for a smart virus writer to hide his stuff.  BTW: this is a change from XP which reserved 63 sectors. 

BTW: forum  etiquette is 1 bump a day - constant bumping can lead to an infraction.

---

### Post by Agent ME on 2010-02-22
> **hithisisatempaccount1532 said:**
> In Ubuntu, why does it seem that Firefox cannot properly display Flash Objects properly?
Have you installed flash? You'll probably want to just install the [ubuntu-restricted-extras](apt://ubuntu-restricted-extras) package.

> **hithisisatempaccount1532 said:**
> Oh, and one more thing... for Ubuntu 9.10 on the PS3 using alternative setup, the drive must be formatted as Ext3 which then disables most software programmed for the Linux kernel to become invalid and not supported... does YDL somehow fix this?
Using the ext3 filesystem doesn't disable most linux software; ext3 is actually one of the most popular filesystem choices, and my laptop uses it.

---

### Post by hithisisatempaccount1532 on 2010-02-22
> **louieb said:**
> yes.
How much more that 256MB? The live CD requires 384 MB or more.

only the 1st 466 bytes are overwritten. Vista reserves ~1066 sectors - can't recall the exact number - plenty of room for a smart virus writer to hide his stuff. BTW: this is a change from XP which reserved 63 sectors. 

BTW: forum  etiquette is 1 bump a day - constant bumping can lead to an infraction.

For the MBR overwriting on first install, does Linux write over everything on the disk leaving nothing behind if you select to install to the entire drive (ie... it's a 'low' level format, or nowadays a high level format, leaving no chance for anything left behind to come back)?

And it was 2GB of RAM. For some reason it just goes to a seizure inducing pink screen with flashing white stripes... I will be trying the alternative disk in a moment.

And for the forum etiquette, my apologies.
Your feedback, however, is GREATLY appreciated.

EDIT:
> **Agent ME said:**
> Have you installed flash? You'll probably want to just install the [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras") package.


Using the ext3 filesystem doesn't disable most linux software; ext3 is actually one of the most popular filesystem choices, and my laptop uses it.
Thanks for your feedback as well, but that seems confusing to me now... when I use the Ubuntu Software Center and try to install the Adobe Flash Player it says that it doesn't support the system architecture... oh durr, it's talking about the processor... right?
And yes, flash is installed on the PC that has strange flash problems.

Edit:

Another question... how can you manually view the contents of the Master Boot Record or the contents of the first few sectors of the drive?

---

### Post by louieb on 2010-02-23
> does Linux write over everything on the disk leaving nothing behind if you select to install to the entire drive no - does a quick format. data can be retrieved from areas of the disk not overwritten by the installed software. - Programs such as testdisk and photorec can recover some if not most of it. 

If you want to wipe it clean use a program such as dban or or write zeros to the whole drive with the dd command.

---

### Post by hithisisatempaccount1532 on 2010-02-23
Well, would it be possible for a virus to survive a format of all partitions on a drive and running the bootrec /fixmbr command on a windows machine... likewise for Ubuntu except I just installed it to the entire disk thinking that grub would overwrite the MBR entirely itself... eliminating all chances of an MBR virus.
 
My focus is not to eliminate everything on the drive from being capable of recovery or anything of that nature, simply just making it impossible for a virus to survive.
 
I know the chances are very slim but I'm just paranoid, it's a problem I have. I have a secure setup with software+hardware firewalls, Anti-everything (including ClamAV on Linux because I'm that paranoid), freeware and shareware. 
 
Is there a proven way to edit/view the contents of the first few sectors of the drive or just the MBR alone? I think I read something about a feature GRUB has, and also something about an OLD microsoft article about doing a ChkDsk and reading the total memory output from the cmd.exe and comparing that to the actual storage amount to compute whether or not something suspicious is up... I'm sorry for the trouble but I just need to prove to myself that there is nothing to freight about.
 
Once again, many thanks for your support and assistance.
 
PS: I may be incapable of responding soon as I'm at school. :'(

Edit:
Another question, what is the difference between Ubuntu and UbuntuStudio (both 9.10)... do they run different desktop enviornments and differ greatly or is UbuntuStudio just more visually pleasing and more easily capable of users focusing productivity?

---

### Post by hithisisatempaccount1532 on 2010-02-23
My one-time-a-day bump goes here.

---

### Post by hithisisatempaccount1532 on 2010-02-24
Well what I'm aiming for is this:
 
Can a virus survive a reformat, running bootrec /fixmbr, and then installing Ubuntu?
Reformat meaning from the windows disk recovery console, using the format command for all partitions. 
 
Likewise, would a virus be capable of surviving the first two steps alone?

Oh, and the pink screen with artifacts was caused by having two monitors hooked up to the video card, one monitor worked which I had turned off and the other would display the pink screen with flashing lights and multicolored artifacts. I've yet to manage to get the second screen to work - any suggestions? Would installing the corresponding display drivers correct this flaw?

---

### Post by hithisisatempaccount1532 on 2010-02-26
Still no answer... :'(

---

