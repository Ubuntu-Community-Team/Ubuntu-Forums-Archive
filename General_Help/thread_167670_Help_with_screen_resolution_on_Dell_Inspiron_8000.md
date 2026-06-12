---
title: "Help with screen resolution on Dell Inspiron 8000"
date: 2006-04-28
forum: General Help
---

### Post by wglenncamp on 2006-04-28
I installed ubuntu "breezy" tonight.  And it loaded fine, but I am having a small issue with my screen resolution.  Whenever I choose a lower resolution than 1600x1200, the screen wiggs out!

I have already tried the dpkg-reconfigure xserver-xorg, and that really didn't change anything.

My eyes are hurting!  :)  Thanks for any help.

---

### Post by yager on 2006-04-28
Does your monitor have an automatic setup mode?  I know that when I switch back and forth between Windows XP and Ubuntu, I sometimes have to force an automatic reset to match the settings to match what Ubuntu is driving the video card at.  Not sure if this is specific only to LCD monitors or not, but it works every time.

---

### Post by wglenncamp on 2006-04-28
I have tried the FN + F7 (CRT/LCD), but that didn't change anything.  The screen still gets crazy when I switch the resolution.

---

### Post by EarthlyDilemma on 2006-04-29
By crazy, do you mean that the screen is split up, showing the same 
part over and over again? Or is the screen flickering/bouncing?

If the screen is flickering/jumping around then the refresh rate may 
be at fault, either too high or too low.

To check this, Click System -> Preferances -> Screen Resolution.
Right below the Resolution is a drop down box that says Refresh 
Rate. See if you have any options.

If you do, try turning it down/up (in that order).

A minimal amount of research seems to suggest that dell prefers a 
60hz refresh on laptops, so if yours is anything else, trying forcing
the refresh to 60hz.

If the screen is splitting up (think about that time you drank a liter
of vodka and tried to walk through a sliding porch door), then the 
monitor probably does not support the selected resolution. If you
have a wide screen monitor, make sure you are selecting the correct
ratios (the same actually goes for standards size as well, my desktop
keeps trying to tell me that 1280x768 would be a great resolution...)

These are the easiest things to check, so i would start there.

---

### Post by psyke83 on 2006-05-02
Hi wglenncamp,

I have a Dell Inspiron 8000 laptop and had the same problem as you. These instructions should hopefully fix your screen issue, as well as some other annoyances with this particular laptop, providing you have the model with an ATI Mobility M4. If you have an Nvidia card, just follow the first part of the instructions and disregard the rest.

Edit /etc/X11/xorg.conf and add the following lines to 'Section "Monitor"':
```

	HorizSync	31-82
	VertRefresh	40-110
```
Do you have an ATI Mobility M4? If you do, you'll experience crashes when switching to a terminal or starting/stopping X. The problem is related to the Fn-F7 key. In the past the only way I could get it not to crash was to keep the screen unscaled, but this can be fixed by changing some settings:

Edit /etc/X11/xorg.conf again, and add these lines to 'Section "Device"':*
```
        Option          "AGPMode"               "4"
	Option		"AGPSize"		"32"
	Option          "EnablePageFlip"        "true"
        Option          "Display"               "BIOS"
	Option		"SWCursor"		"true"
        Option     	"CCEusecTimeout" 	"20000"
```
Edit your grub config at /boot/grub/menu.lst, find the defoptions line, and add this part in red:
```

# defoptions=quiet splash [COLOR="Red"]vga=0x311[/COLOR] scheduler=cfq
```
Changing the scheduler to CFQ worked wonders on this laptop, you may want to change that setting too. Now, update grub's config:```
sudo update-grub
```Changes should take effect when you reboot your system. Hope that helps.

*Note that some of these tweaks are performance enhancements. Page flipping, for example, increases my glxgears score to ~714fps, and the CCEusecTimeout is a workaround to a nasty CCE idle bug in the r128 driver that can cause some games to crash badly. It's solved problems for several apps, but not for others (increasing the timeout may help). Changing AGPSize to 32 enables me to play some games where textures would be missing otherwise; in neverball, for example.

---

### Post by wglenncamp on 2006-05-02
Awesome!  Thanks.  It's working now.

---

### Post by psyke83 on 2006-05-03
[QUOTE=wglenncamp]Awesome!  Thanks.  It's working now.[/QUOTE]

Glad to hear it. Hey, can I use you as a guinea pig for a minute? ;) I'm troubleshooting a problem with this specific laptop, but only the model with a Mobility M4.

Have you noticed a problem with the vertical resolution being squashed when playing back movies? It only affects Xv/Xvideo output. The best way to test is using mplayer from the universe repo:```
mplayer -vo xv filename.avi
```Let me know if your picture seems distorted; the picture will be vertically squashed and you'll see a black band at the bottom of the video.

(The problem doesn't appear at 1400x1050, but appears at lower resolutions, progressively getting worse/more squashed as the resolution is lowered)

Thanks!

---

### Post by matthinckley on 2006-05-09
I have a Dell Inspiron 8000 with the ATI Mobility M4 and when I run 1400x1050 or 1280x1024 everything is fine, but when I run 1024x768 or lower (800x600 or 640x480, which I only tried for testing purposes, but may run games in those res.) the screen is fuzzy and folded in the middle.. the left and right thirds of the screen look fine, but the middle of the screen is unreadable and looks like a copy of the right side of the screen but fuzzy.

Any thoughts?  I followed the suggestions above about changes to xorg.conf and /boot/grub/menu.lst

Matt

---

### Post by psyke83 on 2006-05-09
[QUOTE=matthinckley]
Any thoughts?  I followed the suggestions above about changes to xorg.conf and /boot/grub/menu.lst[/QUOTE]

While running in those troublesome resolutions, try unscaling the screen using the Fn+F7 combination, does that help? Otherwise your problem sounds like a refresh rate problem, which my earlier instructions should have fixed...

---

### Post by OscarT on 2006-07-24
i just hit fn+f7 and it went into a small screen in the middle, when i did it again, the resulution was strangely fixed! do i still have to put in that code?

---

### Post by psyke83 on 2006-07-24
> **OscarT said:**
> i just hit fn+f7 and it went into a small screen in the middle, when i did it again, the resulution was strangely fixed! do i still have to put in that code?

Yep, follow (all) the instructions I gave in post #5 of this thread.

---

### Post by EDevil on 2006-10-28
I just installed Edgy on a Dell Inspiron 8000 and the screen was all garbled...

I altered xorg.conf like it is described here and it worked. Why can't this be autodetected?

---

### Post by gen2ux on 2006-10-30
Yeah, I just installed Edgy on a Dell Latitude C800 and same thing.  Seems strange that a distro this "easy" can't figure out these older machines.  I went back to Drapper and put in the fix for the video and all is well.  Thanks to everyone for the help.

---

### Post by EDevil on 2006-11-07
> **psyke83 said:**
> Yep, follow (all) the instructions I gave in post #5 of this thread.

I would just like to add that even though these instructions worked for resolution 1600x1200, the screen still breaks up in the middle in the lower resolutions. I haven't tried yet the fn-F7 trick because I don't have the laptop here with me but can't these lower resolutions be fixed as well?

Thanks for the help.

---

### Post by osarusan on 2006-11-19
> **EDevil said:**
> I would just like to add that even though these instructions worked for resolution 1600x1200, the screen still breaks up in the middle in the lower resolutions. I haven't tried yet the fn-F7 trick because I don't have the laptop here with me but can't these lower resolutions be fixed as well?

Thanks for the help.

This is true, fn+F7 works wonders for me, but it only makes 1600x1200 work by default. If I want my res to be lower than 1600 by default, what would I have to set in the xorg.conf? Or is the best way to just use fn+f7 every single time?

Thanks so much for this help, btw! It saved my laptop!

---

### Post by psyke83 on 2006-11-19
Hi,

Just a note: I don't have access to my Inspiron 8000 anymore, but I can say that the instructions I posted successfully resolved the screen issue for all resolutions (including 1024x768 and 1280x1024), but my screen resolution is limited to 1400x1050, not 1600x1200 (in Windows and Linux alike). My laptop has a Mobility M4 8mb.

I suggest experimenting with different HorizSync and VertRefresh rates (although I took the original ones from Dell's support site). Sync rates cited across the net differ wildly, but try these as an example:

```
HorizSync   30 - 85
VertRefresh 50-85
```

If they don't work, experiment with higher (or lower) values, and search the net for other people's Inspiron 8000 Xorg.conf files as examples.

See ya,
psyke83

---

### Post by chuckles on 2006-12-17
> **psyke83 said:**
> Hi,

Just a note: I don't have access to my Inspiron 8000 anymore, but I can say that the instructions I posted successfully resolved the screen issue for all resolutions (including 1024x768 and 1280x1024), but my screen resolution is limited to 1400x1050, not 1600x1200 (in Windows and Linux alike). My laptop has a Mobility M4 8mb.

I suggest experimenting with different HorizSync and VertRefresh rates (although I took the original ones from Dell's support site). Sync rates cited across the net differ wildly, but try these as an example:

```
HorizSync   30 - 85
VertRefresh 50-85
```

If they don't work, experiment with higher (or lower) values, and search the net for other people's Inspiron 8000 Xorg.conf files as examples.

See ya,
psyke83



Well, I've tried everything on this thread and nothing helps.  I have the same broken screen issue and I have to use FN-F7 to clear it up.  I've tried updating the xorg.conf file with your suggestions, updated the grub/menu.lst file, I even went into /usr/share/hwdata/MonitorsDB and updated the Vert and horz parameters for the Dell 1600x1200 Laptop Display panel.  Nothing works... still does the same thing.  The problem is that everytime I update the xorg.conf file with the proper settings, it is over written again when I reboot.    It's like the settings are stored somewhere else and it reverts back when it can't get the xorg.conf file to work.   I have attached all the files that I think you would need to see to determine what is going on with this.  Thanks,

Chuckles

---

### Post by Big Willie on 2007-01-09
psyke83 - you R awesome dude!

I came across this problem when installing another distro (Fedora) onto my Dell C800 - and your suggestions from post 5 worked great, and the laptop seems to run very well - I think because I used your suggestions for the CFQ - I also had some crashes, and didnt realize they were when stopping X, but you fixed that too!

Dont get me wrong, Ubuntu is the Best, I am just installing this to for my Brother who uses Fedora.

---

### Post by grantgm on 2007-03-23
Does anyone know if there has been a bug report filed for this? I haven't seen one yet, and I'd love to have this fixed before Feisty is out, but its still there in Herd 5.

Thanks!

---

### Post by psyke83 on 2007-03-23
grantgm,

I'll check launchpad for any similar bugs tomorrow, but I think it's better if you (or someone else with an Inspiron 8000) file the bug anyway - I don't have this laptop in my possession anymore, so I can't contribute towards testing, etc.

---

### Post by aluxito on 2007-04-05
Great, thanks alot, i just try your configurations then  everything goes well.

---

### Post by willray on 2007-05-05
has anyone attempted to run fiesty on these laptops? reason i ask is i'm new to linux and i'm trying to download/install for first time. however, whenever I attempt to begin the process the resolution is set so high i can't read everything to even get through the whole process. I assume I can't change resolution problems until the install is complete and not running from cd?

thanks. Will

---

### Post by willray on 2007-05-06
Hello, I do have ATI and have tried to change as posted. When I go into grub config at /boot/grub/menu.lst however there is no defoptions line to edit. Should I just add in this line at bottom of Default Options section?


Also, I don't understand exactly how to update the grub config file...is this "sudo-update config" done through terminal?
Brand spanking new to linux so thanks for bearing with me. : )
Thanks. Will

 > **psyke83 said:**
> Hi wglenncamp,


Do you have an ATI Mobility M4? If you do, you'll experience crashes when switching to a terminal or starting/stopping X. The problem is related to the Fn-F7 key. In the past the only way I could get it not to crash was to keep the screen unscaled, but this can be fixed by changing some settings:

Edit /etc/X11/xorg.conf again, and add these lines to 'Section "Device"':*
```
        Option          "AGPMode"               "4"
	Option		"AGPSize"		"32"
	Option          "EnablePageFlip"        "true"
        Option          "Display"               "BIOS"
	Option		"SWCursor"		"true"
        Option     	"CCEusecTimeout" 	"20000"
```
Edit your grub config at /boot/grub/menu.lst, find the defoptions line, and add this part in red:
```

# defoptions=quiet splash [COLOR="Red"]vga=0x311[/COLOR] scheduler=cfq
```
Changing the scheduler to CFQ worked wonders on this laptop, you may want to change that setting too. Now, update grub's config:```
sudo update-grub
```Changes should take effect when you reboot your system. Hope that helps.

*Note that some of these tweaks are performance enhancements. Page flipping, for example, increases my glxgears score to ~714fps, and the CCEusecTimeout is a workaround to a nasty CCE idle bug in the r128 driver that can cause some games to crash badly. It's solved problems for several apps, but not for others (increasing the timeout may help). Changing AGPSize to 32 enables me to play some games where textures would be missing otherwise; in neverball, for example.

---

### Post by psyke83 on 2007-05-06
willray,

Be very careful with /boot/grub/menu.lst, if you make an error while editing it could render your system unbootable. Having said that, here's what you need to do:

Open a terminal, then run:

```
gksudo gedit /boot/grub/menu.lst
```

Find this section:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```

Change it to this (what's in red):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash [COLOR="Red"]vga=0x311[/COLOR]

```

Save the file and close, and in the terminal run:
```
gksudo update-grub
```

If you still can't find that section in your menu.lst file, please don't edit it, and posts its contents here instead.

---

### Post by duojet on 2007-05-11
that worked perfectly, thank you!

also, if you're having trouble finding the defoptions part, (like I was) you can just use the FIND function in the edit menu of gedit- works like a charm.

---

### Post by lucidv01d on 2007-06-15
I have tried the post from psyke83 and others with no luck, but I was able to fix the problem by just switching to vesa mode using dpkg-reconfigure xserver-xorg.

If these posts havn't helped and you just want a working screen try this:

When you get to the jarlbled login screen type Ctrl-Alt-F1 for a consol, and then type:

sudo dpkg-reconfigure xserver-xorg

When the utility loads do the autodetect, but then change the driver to vesa.
Accept all the default options, except
    no kernel framebuffer device interface
    load all x.org server modules
    and select the last 3 video modes 
When you get to the monitor characteristics, do advanced and (as from psyche83)
   set horiz sync range to 31-82
   set vert sync range to 40-110 
   and write the monitor sync ranges to the config file
   set the depth to 24

That should be it!
Then just reboot and it should work. Hope it helps.

---

### Post by psyke83 on 2007-06-16
> **lucidv01d said:**
> I have tried the post from psyke83 and others with no luck, but I was able to fix the problem by just switching to vesa mode using dpkg-reconfigure xserver-xorg [...]

Yes, it seems that an update to either the xserver-xorg-video-ati or xserver-xorg-core itself, broke the r128 driver's horizontal/vertical refresh. Under Dapper (and perhaps Edgy), my posted solution works 100% perfectly, but under  Feisty it doesn't work - you always need to toggle the screen scaling using the Fn+F8 key (if I recall).

Unfortunately I don't have the laptop anymore, but while I was in possession of it, I was unable to successfully resolve the resolution/refresh problem. Your solution will work, but the vesa driver has no acceleration and so will be quite slow.

Beggars can't be choosers, but perhaps someone with this laptop should post a bugreport to [http://bugs.freedesktop.org](http://bugs.freedesktop.org), and maybe the issue can be fixed.

---

### Post by Dingo_aus on 2007-06-27
Thanks psyke83, with your suggestion for my xorg.conf you got me up and running on my Inspiron 4000 straightaway with Xubuntu.

---

### Post by Placenta Juan on 2007-10-04
Just saying thanks, that fix worked for me. I was unable to get a resolution higher than 800x600 with a fresh install of Kubuntu 7.04 on an Inspiron 8000. Now I get 1600x1200. Now to work on the wireless...

Edit: My grub display was messed up with the vga=0x311 line added. I just changed it back to what it was originally and now everything is fine.

---

### Post by twhid on 2007-11-17
Also chiming in with a word of thanks. 

I originally tried Ubuntu 4.10 about a year and a half ago and couldn't figure out how to get decent resolution out of the inspiron monitor. Now it's working great with 7.10! Brought back some hardware that I thought was long gone :-)

---

### Post by Eric Lander on 2007-11-20
I've got an Inspiron 5000e, and am struggling to get things working correctly under Ubuntu 7.10.

My research through these and other methods and how-to's shows me that the machine itself will support a 1400 x 1050 resolution.  I'm currently running that now, but have streaking  vertical lines waving through my right hand side of the screen.

When I grab a screen shot, those lines of course do not appear -- so it's certainly a hardware configuration issue.

I know that it has been discussed before at length -- but what would be the best way to approach solving this or at least cutting down on the possibilities?

---

### Post by zzottt on 2007-12-07
this fix worked for me, still have to do the FN+F7 at lower resolutions so thats gonna be a bummer. I just recently picked up a Dell Inspiron 8000 for cheap. Im going to give this to my mother for chirstmas. she doesnt have perfect eyes so I was going to set the default res at 1024x768 but that will require the FN+F7 fix

she isnt all there upstairs so i dont dare trust her with a Windows computer. Ubuntu is just perfect. She cant possibly mess it up and I dont have to get hundreds of calls cause something doesnt work.


:D


the FN+F7 is gonna be something odd for her though. If anyone ever figures this out

can you please email me at

z zottt @ gmai l . c o m

---

### Post by gdubbus on 2008-01-18
Thanks alot of the info. The added lines to Xorg.conf really worked, I've been trying to get the Rage Mobility M4 to work for a couple of days now, the Dell Inspiron 8000 is a querky beast. Thanks again!!!

xubuntu 7.10 is my new fav.

---

### Post by Ubermateo on 2008-02-12
psyke83, Thanks a lot. This saved my Inspiron 8000 from a life of dust collection.

---

### Post by psyke83 on 2008-02-12
To everyone that replied,

Many thanks for the thanks ;). I gave this laptop to my brother (installed with Windows, unfortunately), and I've been itching to install Ubuntu for him (to avoid support headaches for me). The only problem is that the most recent ati driver I tried didn't set up the initial resolution properly, and required the Fn+F7 key combination to be pressed each time X starts, and movies did not play correctly.

Can I ask anyone that's still using their Inspiron 8000 to answer these questions: 

[LIST=1]
[*]Is it necessary to press the Fn+F7 key combination when X initially starts, or does my suggested xorg.conf completely solve the problem? Please let me know the graphics adapter you have and the native panel resolution, as well as the resolution you're running X in.

[*]Do movies using XV output (default for Totem, VLC, etc., can try with 'mplayer -vo xv movie.avi') play at the proper scale? On my laptop, there was a vertical scaling bug that caused movies to get squashed at resolutions lower than the native panel size.
[/LIST]

Many thanks if you can provide any information, and if you know of any bug reports open, etc, let me know.

psyke83

---

### Post by Brixtontechnical on 2008-03-03
I've followed this thread all the way through, and it all makes sense to me. However at the risk of sounding  like a complete idiot, I cannot successfully edit my xorg.conf file - I keep being told I don't have permission to edit the file when I try to save the changes. I'm a total newbie to ubuntu but I'm fairly computer literate - this is my first ubuntu installation and unfortunately it's on a Dell 8000 laptop with the same video problems as the rest of these people. So please - how do I change the permission on my root files so I can edit them?

---

### Post by psyke83 on 2008-03-03
> **Brixtontechnical said:**
> I've followed this thread all the way through, and it all makes sense to me. However at the risk of sounding  like a complete idiot, I cannot successfully edit my xorg.conf file - I keep being told I don't have permission to edit the file when I try to save the changes. I'm a total newbie to ubuntu but I'm fairly computer literate - this is my first ubuntu installation and unfortunately it's on a Dell 8000 laptop with the same video problems as the rest of these people. So please - how do I change the permission on my root files so I can edit them?

You don't need to change the permissions of any files, you need to elevate your own user status (temporarily).

Most flavours of Windows default to using administrator privileges for accounts, giving read/write access to all system files - which can be dangerous. On most Linux-based systems (including Ubuntu), however, users do not have administrator privileges by default.

When you installed Ubuntu, you were asked to provide an administrator password - this is the "root" password.

If you use a text-based editor such as "nano", you can run:

```
sudo nano /etc/X11/xorg.conf
```

If you use a graphical editor such as "gedit", you can run:

```
gksudo gedit /etc/X11/xorg.conf
```

The difference is that "sudo" works well for terminal-based programs, but "gksudo" is designed for use with GUI-based programs. For both commands, it will ask you to input the root (administrator) password.

Take a read here to learn the basics: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by Brixtontechnical on 2008-03-03
Many thanks psyke83 - I tried your solution but it didn't make any difference to my situation with the display problem. I then tried a manual reconfiguration of xserver-xorg as suggested by another poster and that worked. Hopefully it's clear sailing from here on.

---

### Post by operator981 on 2008-06-20
excellent thanks alot been using ubuntu on desktop for a while got given a inspiron 8000 thought would try kubuntu got it working screen wise by just editing the HorizSync and VertRefresh.

word of advice if u dont know what video card i.e Nvidia or something else go to Nvidia website they have a scan thing.

time to work on D-link DWL-G122 C1 

thanks all

---

