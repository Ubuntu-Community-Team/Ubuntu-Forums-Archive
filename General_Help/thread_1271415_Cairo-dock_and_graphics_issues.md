---
title: "Cairo-dock and graphics issues"
date: 2009-09-20
forum: General Help
---

### Post by Stosskraft on 2009-09-20
Hello again,
 
I have added cario-dock through the package manager. When I open with out the open Gl it works fine and when I do open it with open GL its works fine ( alot better animations) but I have this black box around it I do not have if I open with out the GL.
 
I tried to enable the special effects under the appearance but it doesn't let me, though I do have compiz installed.
 
Can someone help me with the terminal commands to trouble shoot this? I am sure I can run open GL but I need to get rid of that box and find the conflict on my system.
 
Thanks for any help. I did spend alot of time researching but I think I may have caused a conflict somewhere, following all the different guides and help.
 
Update:
 
I tired to re-install cairo dock through the package manager, but when I try to start it up in applications, it just freezes in the "configure" screen.
 
It seems there is a conflict somewhere in my system but I don't know how to touble shoot or even begin to fix this.
 
Help

---

### Post by Tipped OuT on 2009-09-20
This is simply because the driver for your graphics card doesn't have full Open-GL support. There's nothing you can do about it.

---

### Post by Stosskraft on 2009-09-20
Hello, Thank you for the answer. Just to verify my graphics driver is: "ATI/AMD proprietary FGLRX graphics driver" as listed under the "hardware drivers' tab.

Also I was able to load up the open GL dock and everything was working great except for the black rectangle around it.

Is there anyway to back track in ubuntu? I think I have made my problem worse trying to fix it !!

Thanks for any advice

Update: I just tried to add the dock to my desk top. I use the package manager and installed "cario-dock" and "plugins" but when I start in up from the Applications-Other is just opens the "maintenance mode" and I CANT CLOSE IT!! I keep pressing the X and it just keeps poping up...I need to reboot to shut it down.

Help?

---

### Post by lidex on 2009-09-20
What version of Cairo Dock are you using? Version 1.x was not very good for me. I tried V 2.0 (now 2.0.8) and it blew me away - much better than AWN. There are two modes: OpenGL and Cairo Backend. Seems OpenGL is not working with older graphics cards and/or AMD(ATI). That's what the Cairo version is for. Please remove all traces of Cairo-Dock currently installed. Then go here:
[http://www.cairo-dock.org/ww_page.php?p=From%2520the%2520repository&lang=en#7-Ubuntu]("http://www.cairo-dock.org/ww_page.php?p=From%2520the%2520repository&lang=en#7-Ubuntu")
to add the CD depository. Next go here:
[http://webupd8.blogspot.com/2009/05/cairo-dock-200-is-here-linux-dock-menu.html]("http://webupd8.blogspot.com/2009/05/cairo-dock-200-is-here-linux-dock-menu.html")
for installation and usage info. Lastly, if so inclined, go here:
[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html")
to get info on repository for updated drivers that may make OpenGl an option for you.
Good luck.

---

### Post by falconindy on 2009-09-20
You may want to try out the Docky theme of Gnome-Do. The graphical glitches with Cairo-Dock became too much for me, and Gnome-Do has been good to me thus far.

I'll qualify this and mention that I really only use my dock for maintaining a list of open programs. I don't employ it as a launcher, but Gnome-D in itself is probably one of the best launchers out there. I never really delved into the applets or special effects that Cairo offered.

---

### Post by Stosskraft on 2009-09-20
> **falconindy said:**
> You may want to try out the Docky theme of Gnome-Do. The graphical glitches with Cairo-Dock became too much for me, and Gnome-Do has been good to me thus far.

I'll qualify this and mention that I really only use my dock for maintaining a list of open programs. I don't employ it as a launcher, but Gnome-D in itself is probably one of the best launchers out there. I never really delved into the applets or special effects that Cairo offered.

Can you tell me how to install this?

As for the cairo-dock, I have reset my dest top with:

> rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and purged compiz with : 
sudo apt-get --purge remove compiz 
Now I think I am back to square one. I have enabled "extra Visual effects" in the appearance tab as I could not do it before..

Can anyone tell me how to know if my ATI card is compatable with open GL? or should I just run a normal dock?

Any ideas now, that I think I have gotten back to square one.

Hehehe confused noobie

---

### Post by Stosskraft on 2009-09-20
can some one please give me the terminal command to completely remove the cairo-dock elements? I tried to reinstall from hte package manager but when I opened it it kept opening up the maintenance screen and when I close it it keeps poping up  (with no visable dock) and I need to uninstall before the screen goes away.

Help

---

### Post by lidex on 2009-09-21
Don't know the terminal command but you can go into Synaptic and search for "cairo-dock". Right-click on any installed packages and select "Mark for complete removal".  Also click the "status" button on the left and select "Not Installed (residual config)" to mark any appearing there. When through selecting click the apply button.

---

### Post by Stosskraft on 2009-09-21
OK, I followed your instructions.

When I tri to reinstall in the pacage manager I get this error: 

Could not mark all packages for installation or upgrade. 

The following packages have unresolvable dependencies. Make sure that all required respositories are added and enabled in the preferences.

cairo-dock-data

Depends: cario-dock but it it not going to be installed

I did check my - third part sources and I have 2: #cairo-dock-stable  and a http//repsoitory.cairo-dock.org/ubuntu jaunty cario clock --- checked

Does this help?


Suggestions how to fix? and can you explain why?...I mean I am trying to understand this ubuntu thing as a noobie so I like know why something is done...hehehe if that makes sense?

Thanks all

---

### Post by fabounet on 2009-09-21
Just to say that GLX-Dock 2.1 has been succesfully tested with the latest Intel drivers and ATI free drivers on the latest X.org.
Also, the Catalyst 9.9 (9.10?) already fully support GLX-dock (they will be released in November).
So Linux will soon have a complete support of OpenGL, and Cairo-dock will take advantage of it. Until that moment, only NVidia drivers can handle glx-dock properly (but of course the cairo backend is working for any card)

---

### Post by Stosskraft on 2009-09-21
> **fabounet said:**
> Just to say that GLX-Dock 2.1 has been succesfully tested with the latest Intel drivers and ATI free drivers on the latest X.org.
Also, the Catalyst 9.9 (9.10?) already fully support GLX-dock (they will be released in November).
So Linux will soon have a complete support of OpenGL, and Cairo-dock will take advantage of it. Until that moment, only NVidia drivers can handle glx-dock properly (but of course the cairo backend is working for any card)

Sorry does this mean I can load GLX-Dock now and use it?

Anyone able to suggest something for the error I am getting trying to install the cairo-dock? Should I delete the 3 extra repsotories I have enabled?

Cheers all

---

### Post by Stosskraft on 2009-09-22
I got the AWN dock working, it seems alright but kinda simple to the cairo dock..I cant move it around my screen.

Do I get instructions about the GLX dock please? I did some searching but nothing for downloading it, is coming up

Advice?

---

### Post by fabounet on 2009-09-22
just follow the wiki, it's very simple.
purge your system from Cairo-Dock before, to avoid any conflict.
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

depending on your drivers, you may have to choose the cairo version rather than the glx one.

---

### Post by lidex on 2009-09-22
Stosskraft
Did you enable the repositories per the tutorial? *You do not need cairo-dock-data* so remove it. GLX-dock is actually the new version of cairo-dock. If you install v2.0.8 from the cairo-dock repository you will get the cairo and glx version. 

This is much better than AWN. The only packages I have installed are "cairo-dock" 2.0.8 and "cairo-dock-plug-ins" 2.0.8. Refer to the web pages I referenced in an earlier post for more info.

---

### Post by Stosskraft on 2009-09-22
OK now whenI re start and try to start the dock through the applications menu I get this error:

> Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

I tried adding it to the start up but not sure I did it correctly. How do I fix this? It was working fine before I restarted?

Ideas? once I get that figured I will work on adding the cairo V2.

Thanks again

---

### Post by NoaHall on 2009-09-22
"sudo apt-get install compiz compiz-fusion"

---

### Post by Stosskraft on 2009-09-22
This is what I get when enter that in the terminal:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fusionHow should i proceed?


also if I try: 

/usr/bin/compiz-start:

I get : >  /usr/bin/compiz-start: No such file or directory

But yesterday the dock and compiz was working, I have only restared since then

Help

---

### Post by lidex on 2009-09-22
In a previous post you stated that you purged compiz. Probably why it's not working.
Try this command:
```
compiz --replace
```


If it doesn't work read this thread as it should answer any questions you might have:
[The Great Desktop Effects FAQ of 2009]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by Stosskraft on 2009-09-22
> **lidex said:**
> In a previous post you stated that you purged compiz. Probably why it's not working.
Try this command:
```
compiz --replace
```
If it doesn't work read this thread as it should answer any questions you might have:
[The Great Desktop Effects FAQ of 2009]("http://ubuntuforums.org/showthread.php?t=809695")

OK tried that command and this is the result:

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start

SO what does this tell me? Now should I reintall compiz and see what happens? How to make it autostart?

Thanks again everyone. Makes it alot easier to switch when people give good answers so quickly.

---

### Post by Stosskraft on 2009-09-24
Bump, sorry guys still need help with this.

Tried :sudo apt-get install compiz compiz-fusion:

and got this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fusion

tried this:/usr/bin/compiz-start

got:> bash: /usr/bin/compiz-start: No such file or directory

Sorry unsure where to go from here.

---

### Post by lidex on 2009-09-24
Go to your main menu: System>Administration>Software Sources. Click on the "Third-Party Software" tab. Click the add button on the bottom-left. Enter each of these lines, one at a time, and click the "Add Source" button.

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
```

Then click the close button. Allow it to update the repositories. Now open up a terminal and enter:
```
sudo apt-get install ubuntu-tweak
```

When this is done open ubuntu tweak from the "system tools" menu. Click "applications" in the left pane, then "third-Party Sources" (enter your password as needed). Now in the right pane select by checking the box for each: Compiz and Ubuntu X (the first one-not unstable). Click the refresh button and allow to update.

It should ask if you want to go to add/remove - go there and check off "cairo-dock" and "Compizconfig-Settings-Manager". Now click apply and allow to install. When all finished close the program, open terminal and enter one line at a time
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Stosskraft on 2009-09-24
OK, I followed your directions to a T. Now I have cairo and AWN in my applicaitons. But AWN doesnt work and both the non- and open GL cairo have the big ugly black box around them.

if I type compiz in the terminal this is what I get:

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
yanek@yanek-desktop:~$ Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400027 (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3600027 (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x24000c3 (Start comp)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2e001e7 (yanek@yane)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

I think I need to active this compiz but when I do click it in applicaitons my screens goes blannk and flickers a few times, but cannot get the docks working.

Help

---

### Post by Stosskraft on 2009-09-24
OK guys Thank you for all the help. Now Ive got it working I am able to use both cairo and AWN...thought not sure what one I prefer yet.

Now time for a dumb question. I am not exactly sure how it is working, how do I make it automatically start up and keep my current settings?  I am afraid to restart

---

### Post by lidex on 2009-09-24
Do you have Emerald installed? Seems to work well for me with compiz-fusion. Open Synaptic (System>Administration>Synaptic Package Manager). Click the "reload" button; if any updates are available select them. Now with "All" selected in the left pane enter "compiz" in the quick search box. From the packages listed make sure these are installed - if not mark them for install:
compizconfig-backend-gconf
compizconfig-settings-manager
compiz-core
compiz-fusion-bcop
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-wrapper
emerald
libdecoration0
libemeraldengine0
python-compizconfig

Click the apply button. Allow install of dependencies. When finished close synaptic. 

To autostart compiz go to System>Preferences>Startup Applications. Click the "add" button. In the name field enter "Compiz Fusion" and enter ```
compiz --replace
```in the command field. 

Click "save" then "close". Open Compiz Settings (System>Preferences>CompizConfig Settings Manager). Under "Effects" make sure "Window Decoration" is enabled (checked). Click that button. In the right pane "Command" field enter ```
emerald --replace
``` 
Click "back" then "close".

Reboot.=D>

---

### Post by zenxi on 2009-09-24
> **Stosskraft said:**
> can some one please give me the terminal command to completely remove the cairo-dock elements? I tried to reinstall from hte package manager but when I opened it it kept opening up the maintenance screen and when I close it it keeps poping up  (with no visable dock) and I need to uninstall before the screen goes away.

Help

sudo apt-get remove --purge cairo-dock

---

### Post by lidex on 2009-09-24
P.S. Do not enter "compiz" into terminal. I tried that to see what result I would get and had to reboot...it may be part of your problem.

---

### Post by Stosskraft on 2009-09-25
Hey, thanks for the help, everything is working perfect now. When I reboot the cairo dock starts up, thought it seems to have a clear box around it. Hard to explain. If someone can guide to take a screen shot that might help. Through it is not really major I am curious when it is happening. 

Thanks again

---

### Post by Stosskraft on 2009-09-25
> **Stosskraft said:**
> Hey, thanks for the help, everything is working perfect now. When I reboot the cairo dock starts up, thought it seems to have a clear box around it. Hard to explain. If someone can guide to take a screen shot that might help. Through it is not really major I am curious when it is happening. 

Thanks again

Wait guys I think I uploaded it through picasa, let me know if you can see what I am talking about. The "clear box" and I am not crazy it was there before:(

[http://picasaweb.google.com/lh/photo/eOhdNfXEpx8vQSIFJavlvg?authkey=Gv1sRgCJzgoP3mseTB0AE&feat=directlink](http://picasaweb.google.com/lh/photo/eOhdNfXEpx8vQSIFJavlvg?authkey=Gv1sRgCJzgoP3mseTB0AE&feat=directlink)

---

### Post by lidex on 2009-09-25
You have ATI/AMD graphics, correct? I have ATI Radeon on my notebook. With OGL i get the black box; cairo backend has no artifacts but not as much eye candy. Which are you using?

---

### Post by Stosskraft on 2009-09-25
The box only appears with the open GL cairo not the non open Gl or AWN dock. If you look at the photo ( can you please confirm that it worked) you will see the "box" is clear and transparent with a faint box showing when I hover near the dock. I have tried to adjust the values of the box to 0, but it is still there.

Yes to confirm I do have ATI/AMD graphics installed.

Thank you

---

### Post by lidex on 2009-09-26
Yes, your upload worked and I saw what you speak of. 

> **fabounet said:**
> Just to say that GLX-Dock 2.1 has been succesfully tested with the latest Intel drivers and ATI free drivers on the latest X.org.
Also, the Catalyst 9.9 (9.10?) already fully support GLX-dock (they will be released in November).
So Linux will soon have a complete support of OpenGL, and Cairo-dock will take advantage of it. Until that moment, only NVidia drivers can handle glx-dock properly (but of course the cairo backend is working for any card)

The problem is the graphics driver. The new drivers (ATI) should fix that problem when released. Your's is doing better than mine (my notebook anyway) as I have a big black box, so, for now using cairo-backend.

---

### Post by Stosskraft on 2009-09-26
Hey lidex,

Thanks for your time and patience. I will just use the backend as you recommend or play around with awn...it seems to work a little better but its just personal taste. 

I have found this switch to ubuntu quite easy with all the help on the forums like this, anyone here makes it out to Hanoi let me know, beer is on me.

---

### Post by Stosskraft on 2009-09-26
Hey lidex,

Thanks for your time and patience. I will just use the backend as you recommend or play around with awn...it seems to work a little better but its just personal taste. 

I have found this switch to ubuntu quite easy with all the help on the forums like this, anyone here makes it out to Hanoi let me know, beer is on me.

One more question, how can I get the Non open GL to autostart vs open GL?

Thanks

---

### Post by DLGandalf on 2009-09-26
haven't checked, but probably in system->preferences->startup applications

find glx-dock(cairo-dock ...blabla..), edit properties and replace the '-o' parameter with '-c'

---

### Post by lidex on 2009-09-26
Stosskraft
You're welcome. I used Awn for quite awhile - the earlier versions of cairo-dock were not to my liking but updates kept breaking things and it was always doing weird stuff at startup and taking forever to load. When I tried the 2.0 version of CD I was blown away. The configuration options are immense and just seemed more stable. The weather applet to me is superb; the applets for clipper and compiz very nice also. Of course my main PC has nVidia graphics so I get the full benefits. If you like AWN you may want to enable the repository thru ubuntu-tweak and use the trunk version. Follow DLGandalf's instructions for cairo backend startup. :)

---

### Post by Stosskraft on 2009-10-10
Well today after a restart and big update, I get a balloon touting the features and the ability to work with ATI drivers in open GL.

These are the instructions they give to get rid of the big black box around the dock in open GL: 

```
If your under gnome (I am), you can activate it in Metacity in this way: open gconf-editor, edit the key '/apps/metacity/general/composting_manager'and set it to true.
```

Ok so I have followed the instructions and still that horrible black box is there. Any suggestions or ideas

Thank you again

---

### Post by lidex on 2009-10-10
Hmmm. Not using that setting here - it's unchecked. What I do have checked is "compositing manager" under "apps>compiz>general>allscreens>options".

Also under "apps>compiz>plugins>decoration>allscreens>options" I have "command" value of "emerald --replace"

---

### Post by lidex on 2009-10-10
From the Cairo-dock wiki:

  * ATI cards : Sorry but already now (2009 May), ATI drivers are just crappy  . But there are many reasons to hope and we may have a real driver one day  . So wait and use Cairo-Dock without OpenGL. (cairo-dock -c)
          
            => Cairo-Dock with OpenGL support seems to be fully supported (maybe with some modifications (look [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/408065"))) on Ubuntu Karmic (tested Aug 2009 with the last ATI xorg drivers and the last kernel (2.6.31-x-generic)) 

It seems that Catatyst will support Cairo-Dock soon (news from AMD devs) 

You could try playing around with drivers from the "xorg-edgers" ppa:
[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html")

---

### Post by Stosskraft on 2009-10-10
ok reason, I ask is based on this from the cairo-dock website:

> Cairo-Dock 2.1.0 : faster, easier, better
(translated by ppmt) 

While 2.0 was introducing OpenGL, version 2.1 is getting more robust. 
Here is the result of 4 months of hard labour : 

Some "annoying bugs" from the Taskbar, PowerManager, Clipper and the keyboard indicator have been squashed. 
The dock at the same became more stable and faster especially when OpenGL is activated (the applet Clock or Cairo-Penguin are now virtually using no CPU resources). 
A news that should please many is that OpenGL now works with the very latest OpenSource drivers for ATI and Intel video card ! 

The dock is evolving thanks to you all ! Lots of comments made after the launch of 2.0 where noted and acted on. 
The configuration panel has been polished (the presentation as improved and the options are better grouped, etc) 
The pictures ratio is now correct (windows thumbnail and Switcher, etc) 
It is easier to create a new main dock or to move the icons from one dock to another. 
A new mode "extended dock" has appeared (the dock will fill up the all side of the screen). 

Themes have also been reviewed and now have an user friendly interface : you can sort the theme by name, rating or simplicity. You can even rate them yourself once you have downloaded them ! 
Thanks to all of the contributors ! 
A complete tutorial is available here. 

Applets have also gained in the process : 

Shortcuts and Notes now have a improved desklet mode, which will allow you to display on your Desktop the icons normally drawn by Nautilus as well you "post-it". 
The digital clock has a better rendering. 
The applets 'Rhythmbox' and 'XMMS' merged to form a new applet MusicPlayer, It now allows to control just about any player. 
'Cpusage', 'Ram-meter' and 'Nvidia' also merge into the System-Monitor applet, which offers basic system information (CPU, RAM, Nvidia card temperature, etc) 

On the very new side we are introducing Dnd2Share, an file sharing applet. It will allow you to send your files on a server of your choice by simply dragging and dropping them on the applet ! you will not be able to live without it. 

You will also notice that open effect of the Slide view is looking a bit more like its Mac OSX equivalent. 

On the project side itself, we migrated to LaunchPad ! 
This means that: 
there is a 'weekly-build' Ubuntu users.
a manual 'daily-compiled' (Mav' script has been updated)
Easier tools for the translators (it's here)
The possibility for everyone to contribute to the project thanks to bazaar.
A complete documentation of Cairo-Dock's API available at this address : [http://doc.cairo-dock.org](http://doc.cairo-dock.org).


As usual your comments/remarks are most welcome. 
Enjoy this new version of Cairo-Dock ! 

The Cairo-Dock team.

The built in help function gave me the above instructions. I ll give your ideas a shot and see what happens.

Thanks

---

### Post by lidex on 2009-10-10
Just installed that update. Nice. I think the key phrase is "A news that should please many is that OpenGL now works with the [COLOR="Red"]*very latest OpenSource drivers*[/COLOR] for ATI and Intel video card !

Once again the drivers come into play. If you are using Compiz + Emerald you don't want Metacity, BTW.

---

