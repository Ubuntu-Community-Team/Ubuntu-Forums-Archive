---
title: "Very Anoying errors"
date: 2006-03-16
forum: General Help
---

### Post by egoo on 2006-03-16
Ok, I tried to install Ubuntu but when i gotto 6% with the installation of the base system the install failed. Tried to install of different computer and it worked fine, Took the hardrvie to the other computer but when it got to loading the modules hda1 could not be found.

Tried to install on the first computer again but this time took 128 of ram out to leave me with 256. Installation of base sytem went fine until about 70% when initrd-tools could not be install or something. Live CD ran on the PC.

System Details:

CPU: AMD Duron 800
RAM: 256MB
Hard Drive : 80gb
Motherboard: Jetway 830CF/CH

Any ideas? Been trying for hours to install, driving me insane!

---

### Post by towsonu2003 on 2006-03-16
I would check the md5sum of the downloaded iso. if it's okay, burn to cd again with slowest speed possible.

---

### Post by Luke on 2006-03-16
maybe re-burn install disc at lower speed??? perhaps one cd drive is pickier than the other.

edit: i'm too slow :)

---

### Post by egoo on 2006-03-16
The CD is the one ordered from ubuntu shipping site. It was off a friend who ordered loads.

---

### Post by towsonu2003 on 2006-03-16
[QUOTE=egoo]The CD is the one ordered from ubuntu shipping site. It was off a friend who ordered loads.[/QUOTE]
some of those CDs were corrupt as well. ask your friend to give you another one (or, download one?)

---

### Post by egoo on 2006-03-16
I will download now. If it installed fine on another computer shouldn't the cd be ok though?

---

### Post by towsonu2003 on 2006-03-16
[QUOTE=egoo]shouldn't the cd be ok though?[/QUOTE]
I'm not sure -the only way to be sure of that is to get the iso, check md5sum, burn to cd w. slow speed, try... if doesn't work, burn once more.. if not good again, burn one last with a different cd burner. 

until than, everyone here will tell you to re-burn the CD <= this wouldn't help you a bit...

---

### Post by egoo on 2006-03-16
Ok, Thanks for your help.

---

### Post by egoo on 2006-03-16
Ok, Installation with CD worked fine. Installing the remaining packages not so good. 

An error came up saying that some packages could not be installed with an 'ok' button at the bottom and when pressed a black screen where yout type your ubuntu username and password in. 

Can I make a reovory this far into the installation? Mayby copy the packages to the hard drive again from the install cd then run them manually or something? I got all excited when it was installing fine.

---

### Post by egoo on 2006-03-16
Anyone? Any help apreciated

---

### Post by Luke on 2006-03-16
is there a problem with the network connection on the target machine?

---

### Post by egoo on 2006-03-16
he DHCP didnt confiugre on setup. Why would the network connection matter?

---

### Post by Luke on 2006-03-16
oh, i thought, based on your earlier post, that maybe it was a problem connecting to get extra packages after first reboot. however, i don't think it attempts to connect if network connection was not established during initial install. i don't think i have any more ideas on this one. 
are you still using the original cd or did you download and burn a new one?

---

### Post by ebutton on 2006-03-16
Hello!

I'm on a Sony VGN-S380P laptop which needs the nvidia drivers.  I frequently see my screen colors distorted, but still somewhat usable.  I have to log in without clearly seeing what I am typing (user name), but afterwards, I can move my mouse pointer around and some parts of the menus become readable - at least, enough to navigate them.

When the problem happens is not predictable.

I found a workaround that does not require me to reboot.  Using the mouse, I click System, then Preferences, then Screen Resolution and select a lower resolution.  I then click Apply.  At this point the screen becomes more readable and I see a window asking if I want to keep the new setting or go back to the Previous setting.  I choose to go back and voila! - the problem is solved.

Hopefully, Dapper Drake will not have this problem with the nvidia devices.

I hope that this works for you.

---

### Post by egoo on 2006-03-16
The screen im taken to a shell thing with the line

iain@ubuntu:$

---

### Post by ebutton on 2006-03-16
Oh.  Sorry then, I don't know enough to help you, except perhaps to suggest that you use the "Search" feature above on the menu bar, between "New Posts" and "Quick Links".  I've found answers to several problems that way.

'nuther thing:  There is more introductory tutorial stuff at the top of the ??? - I think it's called "Absolute Beginner" forum.  I mostly start with that forum or with a Search, when I need help, which is still frequently, but getting better.

I am confident that if you remain patient and determined, you will get expert advice from this community that will soon help you to become happy and successful with your FREE Breezy OS and applications.

Warm Regards,
Ed Button

---

### Post by egoo on 2006-03-16
:) Thanks for your help anyway :)

---

### Post by towsonu2003 on 2006-03-16
[QUOTE=egoo]he DHCP didnt confiugre on setup. Why would the network connection matter?[/QUOTE]
try the installation again, and when it fails to configure dhcp, tell it NOT to configure dhcp. also, note each step (partitions, filesystems, formatting etc) as well as the packages that weren't installed if installation fails again. if fails again, pls post that info as well. good luck

oh, and, not that it matters but the black screen with you user name in white is called command line interface (i.e. CLI) :)

---

### Post by DumbNoob on 2006-03-17
I had an install not complete like that.  Fortunately it far enough through that it still gave me a GUI on reboot and I was able to get the rest of the internet.  I didn't keep that installation but it seemed fine for the short period that I did have it.
I'm wondering if he configures his network himself when installing and can get far enough that it gives him a command line then he can try apt-get dist-upgrade ?

If it sounds like a stupid suggestion it's because I'm a DumbNoob and it's my first post.

---

### Post by towsonu2003 on 2006-03-17
[QUOTE=DumbNoob]
I'm wondering if he configures his network himself when installing and can get far enough that it gives him a command line then he can try apt-get dist-upgrade ?
[/QUOTE]
Sure. I just prefer clean installs rather than half-completed installs later fixed by downloading, tweaking etc. Half-installed distro is just a bad start / first impression... if something goes wrong later, you'll always think 'did I do st wrong during my first installation tweaks??"... A clean install will make you forget previous aches...

Also, my first ever ubuntu install failed st like that. bc I had a winmodem, it couldn't configure dhcp. asked me whether it should try again. I said to either try it again or try again later, and it failed. in my second try, I chose 'don't try to configure dhcp or I'll kill you', so it installed nicely. I guess this is a bug, but to report the bug, I have to reproduce it. to reproduce it, I have to reinstall, which is not time-saving...

Off-topic note: don't curse at yourself with a nick like that ;) everyone was a newbie at one point, nt wrong with that...

---

### Post by Jason_25 on 2006-03-17
[QUOTE=egoo]Anyone? Any help apreciated[/QUOTE]
Try running memtest86 on the install cd for a few loops to look for any errors.

---

