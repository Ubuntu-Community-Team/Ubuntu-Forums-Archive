---
title: "ISO file burning problem"
date: 2010-03-07
forum: General Help
---

### Post by archeryrob on 2010-03-07
I am trying to burn the ISO download file for 9,10 server to a CD so I can install it on a blank computer I an piecing together for a file server.

I followed the direction here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I could not get Infrarecorder, but I got Express Burn and Free Easy Burner

I tried following the direction and I still end up with a CD with another ISO file, not an unpacked installation disk. I did not see it on a search.

Any help or threads to point too?

---

### Post by joeknoodle on 2010-03-07
Are you burning it as an ISO or as a Data disk? If memory serves, I think you need to create a Data disk.

---

### Post by egalvan on 2010-03-07
Are you burning under Windows? If so I would (strongly) recommend "imgburn"


[http://www.imgburn.com/](http://www.imgburn.com/)


I've used it for some four years now, and donate $5 a year 'cause it's that good.

once the program is installed in Windows, double-clicking an iso file will automatically start the program in "burn image" mode...
it's more-or-less fool-proof.

I also use it (occasionally) to create an iso from a CD or DVD.

---

### Post by archeryrob on 2010-03-07
I need a bootable CD. I keep getting a copy of the ISO on the disk. Any particular way I have to run it? I got imgburner and am trying it again now. I don't have windows or a operating system only the bios on the chip, little hard drive and cd drive.

This way i can play with it and learn it and then add more SATA drives later

Fool proof, well this fool did not get it.

---

### Post by archeryrob on 2010-03-07
Active ISO burner is also installed and changes the icons for the ISO files. I click to burn with it and with IMG burn and I just keep ending up with an ISO file on the disk not a install disk that I can place in a blank system.

Do i need to get a hack for windows just to install Ubuntu? How can I install this without an OS on the machine?

---

### Post by geirha on 2010-03-07
This screencast is rather old, but the procedure for burning the iso-file on a CD-R has not changed, and I believe it uses ImgBurn:
[http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO](http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO)

Are you doing anything different than what is done in the screencast?

---

### Post by egalvan on 2010-03-07
> **archeryrob said:**
> Active ISO burner is also installed and changes the icons for the ISO files. I click to burn with it and with IMG burn and I just keep ending up with an ISO file on the disk not a install disk that I can place in a blank system.

OK, multiple software on Windows can sometimes break things...

here is a link to a simple "how-to" using imgburn

[http://forum.imgburn.com/index.php?showtopic=61](http://forum.imgburn.com/index.php?showtopic=61)

I have used imgburn "out-of-box" on many Windows installs, usually to obtain a Linux-based distro...thusly

download imgburn,
install it,
download the Linux distro iso,
double-click it,
and disk image burned...

it has never failed me,
and I have never had to do any "set-up" with imgburn.


> Do i need to get a hack for windows just to install Ubuntu? How can I install this without an OS on the machine?

No "hacks" or "cracks" needed....

To install to a blank machine, you should use a LiveCD, or an installation CD. :)
Of course, you need someway to obtain that CD... :)
you can also do a network-based  (LAN or Internet) install, using a dedicated installer such as unetbin.
Or a generic installer.


And we could use a bit more information...

What kind of computer are you using to create the CD?
What system (Windows XP?) is installed?
How much RAM?
How large a drive?

---

### Post by archeryrob on 2010-03-07
OK, this computer is:

Windows XP 2002 service pack 3
P4 3Ghz and 3 G ram
DVD CD - RW drive

The other computer is parts I have gathered. But do you need windows to install Ubuntu? How do you install Ubuntu from scratch?

---

### Post by egalvan on 2010-03-07
> **archeryrob said:**
> this computer:

Windows XP 2002 service pack 3
P4 3Ghz and 3 G ram
DVD CD - RW drive

This is a completely serviceable machine, should work fine for downloading and burning iso's.


> The other computer is parts I have gathered.

I've installed operating systems on many a machine I have assembled from "extra" parts.
Just make sure the parts will work together, and are supported by the system you want/need.

>  But do you need windows to install Ubuntu? How do you install Ubuntu from scratch?

Again, **NO**, you don't **NEED** Windows to install Linux.

You merely **need** some way of **booting an installer**.

This can be a LiveCD, or USB-based, or a PXE-based, to name a few.


Now, **how and where** you get this installer can be a problem if you have no computer that will boot what you need.


You can buy a CD/DVD distro from an on-line company...

two examples

[http://www.linuxcd.org/?ref=distrowatch](http://www.linuxcd.org/?ref=distrowatch)

[http://www.osdisc.com/cgi-bin/view.cgi/index.html?affiliate=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/index.html?affiliate=distrowatch)

You can download it on a friend's machine,
or an internet cafe, or the library...

Download a tiny distro, such as Tiny Core Linux, which weighs in at 10M download (yes, a mere TEN megabytes)

[http://tinycorelinux.com/](http://tinycorelinux.com/)

PartedMagic weighs in at around 44Meg

partedmagic.com

Puppy weighs in at around 100Meg

[http://www.puppylinux.com/](http://www.puppylinux.com/)

All of these will allow you to connect to the internet, download the iso you want/need, and will allow you to burn it.
Or copy to a USB drive.

---

### Post by archeryrob on 2010-03-08
Oh wait, so I can load Tiny core on a USB and boot the computer with it. The try and load the OSI file?

If that is so it woulld work for my other "play" project. Wanting to build a DVR type box with eprom memory. Easy to download from the net or watch central storage files. It will give me someting to do over the summer when not fishing

---

### Post by archeryrob on 2010-03-08
Loaded Img Burn on my wifes Win7 64bit Dell laptop and it burnt fine and its all unpacked.

So what wrong with my desk top? 32 bit? maybe corruption? Maybe I get the server and back it up and wipe it with a restore.

---

### Post by Tikkyca on 2010-03-08
Why don't you get free live CD from ubuntu website from that CD you can try ubuntu,isntall it,without problems: [http://shipit.ubuntu.com/](http://shipit.ubuntu.com/)

---

