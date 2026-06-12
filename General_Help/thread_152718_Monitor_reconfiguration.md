---
title: "Monitor reconfiguration"
date: 2006-03-30
forum: General Help
---

### Post by SFAOK on 2006-03-30
Hi there,

I've taken delivery of a new Acer monitor (AL1751BS) today and very nice it is too :) It's an upgrade from an old Relisys CRT and as this monitor has DVI input, I'm now using DVI rather than the old analogue lead. However, I'm having a problem. Occasionally - and it's not a set amount of time - the screen will go black momentarily and then come back after around half a second.

Very frustrating for a new piece of kit. At first, it was just the once but then it happened more frequently. I took my PC apart, made sure the graphics card was sitting in its slot properly (took it out, put it back in), put it all back together and after a while: the same problem occured.

I thought I'd give it a go in Windows - rebooted into Windows, played with it for 20-30 minutes, no problems. Rebooted into Ubuntu and so far it's been fine which means either a. the problem has gone away b. the problem occurs because of something to do with ubuntu - but hasn't shown up for a while or c. the problem is with the monitor and I was lucky/didn't try it for long enough with Windows and Ubuntu suffers in the same way Windows is suffering.

I've looked in vain for a configuration tool that will let me choose my monitor (thinking Ubuntu may still think I have my old monitor) but couldn't find one. Looking in the the xorg.conf file, it apparently still thinks I have my old monitor. But I'm wary of changing things in the file because I don't really know what I'm doing, what I should be putting in there and what I shouldn't be touching under any circumnstance.

Can anybody offer me any advice about how to register the new monitor so the configuration files know which monitor I actually have now? If the problem keeps persisting I'll try the analogue cable instead but obviously I don't want to be doing that long term.

TIA

---

### Post by ajgreeny on 2006-03-30
In your /etc/X11/xorg.conf you should have a section about the monitor which looks something like this:-

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	50-75
EndSection

Look in your monitor documentation for the spec to find the horizsync and vertrefresh figures and change your xorg.conf to show those figures.  It may not help but it is worth doing anyway.  Bestof luck.

---

### Post by BeerSlinger on 2006-03-30
[QUOTE=ajgreeny]In your /etc/X11/xorg.conf you should have a section about the monitor which looks something like this:-

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	50-75
EndSection

Look in your monitor documentation for the spec to find the horizsync and vertrefresh figures and change your xorg.conf to show those figures.  It may not help but it is worth doing anyway.  Bestof luck.[/QUOTE]

Hi, 

I would like some help on this too because I have been reading to the point that my eyes are watering and I can find many ways to make my machine blow up but I can't figure out how to get the configuration right...

Just to be detailed, this is a new install and I only tried Ubuntu as of yesterday.  My monitor is a little bit older and my video isn't too old.  I have:

Monitor: Samsung SyncMaster 1100DF
Video: ATI X800

Well, I can find tutorials on how to make both monitors work but the examples that I make for xorg.config make XWindows error out. So at this point i'm not sure what to do...

First, i'm only able to get a 1024X768 screen res and that's a bit cramped for me, I would prefur to have a 1280X1024 which is well within what can be handled.  First I checked and modified the conf file so that the larger resolutions could be recognized.  Here is the modification (which hasen't blown up):

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

This seems to work, but all I know is that it doesn't blow up.......the code that does blow up is the config for the monitor......to be specific, this is my exact monitor:

[http://www.bhphotovideo.com/bnh/controller/home?A=details&Q=&is=REG&O=productlist&sku=269334](http://www.bhphotovideo.com/bnh/controller/home?A=details&Q=&is=REG&O=productlist&sku=269334)

It would have been nice to give you the manufacturers information but they are about as much help as a lead bullett slug embedded in your foot...

Here is the config that I tried that blewup:

Section "Monitor"
        Identifier  "Samsung Syncmaster 1100DF"
        HorizSync  30-121
        VertRefresh 50-160
EndSection

I have tried other examples but they haven't worked either, any other suggestions that someone might have?

:confused:

---

### Post by BeerSlinger on 2006-03-31
[QUOTE=BeerSlinger]Hi, 

I would like some help on this too because I have been reading to the point that my eyes are watering and I can find many ways to make my machine blow up but I can't figure out how to get the configuration right...

Just to be detailed, this is a new install and I only tried Ubuntu as of yesterday.  My monitor is a little bit older and my video isn't too old.  I have:

Monitor: Samsung SyncMaster 1100DF
Video: ATI X800

Well, I can find tutorials on how to make both monitors work but the examples that I make for xorg.config make XWindows error out. So at this point i'm not sure what to do...

First, i'm only able to get a 1024X768 screen res and that's a bit cramped for me, I would prefur to have a 1280X1024 which is well within what can be handled.  First I checked and modified the conf file so that the larger resolutions could be recognized.  Here is the modification (which hasen't blown up):

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

This seems to work, but all I know is that it doesn't blow up.......the code that does blow up is the config for the monitor......to be specific, this is my exact monitor:

[http://www.bhphotovideo.com/bnh/controller/home?A=details&Q=&is=REG&O=productlist&sku=269334](http://www.bhphotovideo.com/bnh/controller/home?A=details&Q=&is=REG&O=productlist&sku=269334)

It would have been nice to give you the manufacturers information but they are about as much help as a lead bullett slug embedded in your foot...

Here is the config that I tried that blewup:

Section "Monitor"
        Identifier  "Samsung Syncmaster 1100DF"
        HorizSync  30-121
        VertRefresh 50-160
EndSection

I have tried other examples but they haven't worked either, any other suggestions that someone might have?

:confused:[/QUOTE]

I will post a new thread on this because I have partially found the answer and i'm testing it....

It has failed once but I'm taking it one step at a time to address the real error in configuration....

---

### Post by Gustav on 2006-03-31
The easy way is to run ```
sudo dpkg-reconfigure xserver-xorg
``` in the terminal.

---

### Post by BeerSlinger on 2006-03-31
[QUOTE=Gustav]The easy way is to run ```
sudo dpkg-reconfigure xserver-xorg
``` in the terminal.[/QUOTE]

that was part of the solution I found.......but the actual reason why it didn't work in the first place........I found out that I wasen't doing things right during setup.......

Basically, I've been making all of the classic newbie blunders........though I hope some can forgive because at most this is only my fifth day.......I'm so use to being spoon feed from microsoft, and from some extent, Redhat that I made some moves that could have been entered into the idiots classic tournament.....

My first problem, and its not listed here, I couldn't get it through my head when it asked for the Name server in the setup, it was refuring to the DNS.......I knew what it stood for, I just couldn't make the connection because I've never heard it said without the word "Domain" so it never registered.....

The second dumb mistake that I made was to not figure out that when the multitudes of resolutions came before me during setup, I had to enable them with the space bar..........it was a real DOOH moment.........

But now that its fixed I'm much more comfortable.........I don't know about all of you but the difference between 1024X768 and 1280X1024 can make you clostraphobic.....

Also, tonight, I was about to make another dumb mistake and that was about software install (core not idividual packages)........but the more I have looked, the more i've been mind-boggled not by the amount of information, but just how well organized it is......Well compiared to other linux versions......Someone has taken some real time with the "HOW TO's" out there and it shows.......I think..........

So, I guess I'm off to blow up my computer again....

I'm still in the Trial and Error Phase, so I guess I should expect this.....

](*,)

---

