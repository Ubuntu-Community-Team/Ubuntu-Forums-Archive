---
title: "WINE installation nightmare"
date: 2006-04-25
forum: General Help
---

### Post by Kashirigi on 2006-04-25
Hi everyone,

I'm trying to install WINE, mostly to use my Photoshop filters in Gimp.

If I try to use apt/synaptic to get winesetuptk, wine will be removed and vice versa. This is extremely irritating and unhelpful.

Secondly, if I run winesetup, I will get this message
CBase::AutoConf:GetWinInstalls: unable to grep /mnt/C:/msdos.sys: child process exited abnormally

I can still complete the setup. It will write the configuration files to ~/.wine

Then I'll have to apt-get install wine (which overwrites the files, of course. Naturally I would have made a backup and replaced them).

Then, I will try and run wine.

I get:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible

My windows partition is FAT32, the wine config file is set to 

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
"Windows" = "nt40"

Could someone please enlighten me as to what I can do to get this to work successfully?

Thank you.

---

### Post by Toxicity999 on 2006-04-25
Easiest possible way,
run winecfg (it seems that you never created you fake drives for wine to operate with! This should do that, and allow you to tweak some.)

Or go from the very beginning with:

sudo gedit /etc/apt/sources.list

add
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
to the bottom.

sudo apt-get update
sudo apt-get install wine

now you can just run winecfg which will automatically create your fake drive structure, and allow you to tweak. Orrrrrr, you can install WineTools. which allows easy(ish) installation of some very basic software which some programs could need.

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by Kashirigi on 2006-04-26
Thank you. That seems to have solved most of my problems.

However, now I have further problems with GIMP and pspi.

But that's a job for another thread.

---

