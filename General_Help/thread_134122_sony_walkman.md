---
title: "sony walkman"
date: 2006-02-21
forum: General Help
---

### Post by jamesrw on 2006-02-21
i've got a sony mp3 player... in windows it uses the sonicstage application to transfer music. I tried to install the application with wine but can't get it to work. The USB connection work fine which is great but I haven't fond anything about a way to transfer music yet. Anyone out there know anything?

---

### Post by zhoux on 2006-05-19
I have the same problem, whenever i try to install SS, it gives an errror that "SonicStage does not install on this Windows Version."

Help anyone

---

### Post by jamesrw on 2006-05-22
There is an application I have which lets you drop files onto the sony device. The application installs onto and is run from the device itself. I have tried to run in in Wine but did not succeed. I will post a link to the app when I get a chance and maybe someone can see if they can get it to work.

---

### Post by Ramses de Norre on 2006-05-22
I'm having this issue too, and I've tried to install SS to wine quite a few times but it wont work.

I'm pretty interested in that app your talking about.

---

### Post by jamesrw on 2006-05-22
Here is a link to the alternative application to Sonic Stage, it is compatible with the  [NW-E103/E105/E107/E403/E405/E407/E503/E505/E507] models. Hopefully someone can get it to run in linux.

Driver & MP3 File Manager Ver.2.0 Installer for the Network Walkman
[http://www.sonydigital-link.com/DNA/downloads/downloads.asp?l=en&ct=NWF&f=MP3FM20](http://www.sonydigital-link.com/DNA/downloads/downloads.asp?l=en&ct=NWF&f=MP3FM20)

---

### Post by dmizer on 2006-05-22
sony walkman is freakin beautiful (mine was an nw-a1000 ... 6gig version), but the software what makes it run is the pits. i got so fed up with it both in linux and in windows, that i ended up returning it and bought an iriver instead.

first of all, it doesn't actually RUN mp3's, it needs to convert to some proprietary format that has no software conversion available that i could find.

second of all, even in windows, the connect/sonic stage won't run unless you are in an administrator account (can you say ROOTKIT?).

my iriver was cheaper, i can simply drag/drop mp3's onto it and it will play them.  i can watch color video, read books, look at pictures and listen to the radio.  and (did i mention) it was cheaper.

i got sonic stage to actually run in a windows vm, but had trouble getting the usb to connect the device.  actually, the ONLY way i was ever able to get music onto the thing was by putting a windows machine together from scrap parts i had laying around.

neither sonic stage, nor connect player will work in wine or any derivative.

the player is beautiful, sound quality isn't fantastic ... but it's livable. software stinks.  i returned mine.  the guys at the store didn't even ask, they just said, "software problems?" and gave me my money back.

---

### Post by zhoux on 2006-05-24
i've been trying out the app that allow you to drag and drop on Wine.  Unforunately, its not working. :confused: :mad: 
The problem seems like that the app cannot find where the device is connect to, so perhaps there need to be a change in the Wine/Windows registry? :confused:

---

### Post by kairu0 on 2006-05-25
That app doesn't work with the newer Sony Network Walkmans (NW-Exx) from my experience.

---

### Post by jamesrw on 2006-05-25
[QUOTE=kairu0]That app doesn't work with the newer Sony Network Walkmans (NW-Exx) from my experience.[/QUOTE]

see above, i listed the models that are compatible... i'll mess with it some more using wine this weekend... not promising anything, i don't think theres much more i can try to do.

---

### Post by Shay Stephens on 2006-05-25
Don't fight it.  Sell your player and get one that supports what you want to do.  Support software and products that support freedom.

---

### Post by Tye on 2007-07-04
I love my walkman


the atrac is supposed to be the most advanced format of music compression
i think i'll take sonys word for it since they are the leaders in so many other fields

even though thats how they get their 27 hours playback 
(all music must be in atrac format and at 64bit)
but stilll that 64bit atrac version is supirior to wma and mp3

maybe we should ask sonic stage to make a linux version

instead of just complaining

---

### Post by mbeierl on 2007-07-04
The problem comes down to this:

the walkman is NOT an mp3 player.  I challenge anyone to show me how it can be called an mp3 player when it cannot play mp3 files.

Secondly, it requires proprietary driver to administer the filesystem.  My daughter finds her walkman nearly useless now as we no longer use Windows.  Time to get an iPod.  At least Apple is on the right track with their DRM free iTunes.  Way to go Apple!

---

### Post by bobsp on 2007-07-08
Take a look at **[this link.]("http://david.dw-perspective.org.uk/Sony-NW-E00X-Walkman-On-Linux-FreeBSD-MacOSX-etc.html")**.  Haven't tried it myself yet, but it seems plenty of people have...

---

### Post by funnypanks on 2008-02-02
thank you so much worked perfectly for my e015

---

### Post by orasetaina on 2008-06-18
will this work for a NWHD3?

---

### Post by drjonze on 2008-06-18
You can also use the Jysmphonic software. Its a Java app so make sure you have Java installed. I could not get it to work but I didn't try very hard. I really just played with it for a few minutes. I'm getting a new mp3 player soon so I wasn;t going to invest anytime in something I won't be using anymore. I currently have a Sony NW-E405. It will work with Jysmphonic as I learned from this thread:

[http://ubuntuforums.org/showthread.php?t=716477&highlight=jsymphonic]("http://ubuntuforums.org/showthread.php?t=716477&highlight=jsymphonic")

Jysmphonic can be run on Linux, Windows and Mac. You can actually store the application on the device.

---

