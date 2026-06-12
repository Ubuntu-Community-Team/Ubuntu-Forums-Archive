---
title: "XGL and Compiz eyecandy: One thread to rule them all... (Index)"
date: 2006-03-21
forum: General Help
---

### Post by g14 on 2006-03-21
[color=red]WARNING - This howto is outdated, please check this sticky instead: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)[/color] - *Artificial Intelligence*


**This is not a support thread!** Ask questions in the [compiz forum]("http://compiz.net/")

[So what is this whole Xgl/compiz thing I keep hearing is so darn cool?]("http://compiz.blogspot.com/2006/03/introduction-to-compizxgl.html")

I started this thread as a place to put the best of the other compiz threads and common issues into a central place making them easier to find.

[SIZE="4"]**Installation**[/SIZE]

Compiz works fine on any videocard supporting Directx 9.0 and pixelshaders. This is known to work well on Nvidia Geforce FX >= 5200 and ATI >= 95xx. Compiz will also run on older or non 3d accelerated hardware, but not without choppy/slow effects and possibly freezes.

[Building Xgl/compiz from source code]("http://www.ubuntuforums.org/showthread.php?t=132406")
[Xgl/compiz on an Nvidia video card]("http://www.ubuntuforums.org/showthread.php?t=131267")
[Xgl/compiz with an Nvidia video card on AMD64]("http://ubuntuforums.org/showthread.php?t=133427")
[Xgl/compiz on an Nvidia video card with KDE]("http://ubuntuforums.org/showthread.php?p=845077")
[Xgl/compiz on an Ati video card]("http://www.ubuntuforums.org/showthread.php?t=131253")
[Xgl/compiz on an Intel i915 video card with DRI]("http://www.ubuntuforums.org/showthread.php?t=134069")
[Xgl/compiz on an Intel i810 video card with Breezy Badger (Ubuntu 5.10)]("http://ubuntuforums.org/showthread.php?t=133772")
[Aiglx/compiz on an Intel i915 video card]("http://www.ubuntuforums.org/showthread.php?t=145068") compiz seems to have better performance on Aiglx with this video card.

**[SIZE="4"]Once you have it working[/SIZE]**

**Installing the latest compiz with all of the new goodies.**
NOTE: You should be running this later version of compiz/Xgl for some of the other how-tos in this thread to work
[INDENT][http://www.compiz.net/viewtopic.php?id=2]("http://www.compiz.net/viewtopic.php?id=2") Overview[/INDENT]
```

sudo gedit /etc/apt/sources.list

```
Add this to the very end:
```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```
Run these following commands and you will have the latest version of Xgl and QuinnStorm's newest compiz.
```

sudo apt-get update
sudo apt-get dist-upgrade

```

**An easy way to restart compiz and switch back to metacity if you don't like it**
[http://www.compiz.net/viewtopic.php?pid=11734]("http://www.compiz.net/viewtopic.php?pid=11734")
Download compiz-start.py, and logo24.png from this website and save it in your home directory. Then you can run these commands to properly install it:
```

chmod 755 compiz-start.py
sudo mv compiz-start.py /usr/bin/
sudo mv logo24.png /usr/share/icons/

```
Next, you can manually run the command 'compiz-start.py' from a terminal to see if it works (it should). If it does, go to
System ---> Preferences ---> Sessions ---> Startup ---> Add: and add a line that says compiz-start.py. If you use compiz-start.py, make sure to remove anything from your session that looks like this:
```

gnome-window-decorator
compiz --replace gconf
thefuture

```
If you don't, compiz could start twice and mess things up. This is nice to restart compiz when unstable plugins like dock crash it or when you want to switch back to metacity to play opengl games. You need to logout and back in for these changes to take effect.

Mandatory Screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=12265&stc=1&d=1152121234[/IMG]

**Xgl CVS**
NOTE: If you add QuinnStorm's apt repository, you shouldn't need to do this as the latest Xgl CVS is updated by reggaemanu.
[INDENT][http://ubuntuforums.org/showthread.php?t=148860]("http://ubuntuforums.org/showthread.php?t=148860")[/INDENT]

**Setting a video or screensaver on your desktop for an animated wallpaper.**
[INDENT][http://www.ubuntuforums.org/showthread.php?t=146533]("http://www.ubuntuforums.org/showthread.php?t=146533")[/INDENT]

**Installing a graphical tool to change compiz configuration instead of gconf-editor.**
Use QuinnStorm's repository and then run the following command:
```

sudo apt-get install gset-compiz gcompizthemer

```
Then you can run gset-compiz for a nice graphical configuration tool and gcompizthemer for a theme configuration tool. If you use compiz-start.py, you can right click on the compiz icon in your tray and go to configuration to bring up gset-compiz for you. Just make sure to install it.

**Poking around at the compiz configuration.**
[INDENT]Open up gconf-editor from a terminal or from the run dialog (ALT F2 in gnome) and browse to /apps/compiz.[/INDENT]

**Making CTRL ALT Delete open up the system monitor like in windows.**
```

gconftool-2 --set --type string /apps/compiz/general/screen0/options/run_command1 "<Control><Alt>Delete"
gconftool-2 --set --type string /apps/compiz/general/screen0/options/command1 "gnome-system-monitor"

```
**Making the Print Screen button actually work again.**
```

gconftool-2 --set --type string /apps/compiz/general/screen0/options/run_command0 "Print"
gconftool-2 --set --type string /apps/compiz/general/screen0/options/command0 "gnome-screenshot"

```

**For people that want to enable the MacOS X style scale plugin by moving the mouse to the corner of the screen**
1.) Install the software you need.
```

gconftool-2 --set --type list /apps/compiz/plugins/scale/screen0/options/corners "TopRight"

```

[SIZE="4"]**Common Annoyances:**[/SIZE]

**Keyboard Shortcuts Don't Seem to Work**
Go to System --> Preferences --> Keyboard and change your keyboard layout. I had this problem with my Microsoft Natural 4000 keyboard.

**gconf-editor is crashing and says** **** glibc detected *** free(): invalid pointer: 0x0837d4b0 **** **from the terminal.**
[INDENT]This fix takes a few steps, but is still pretty easy. 

[LIST=1]
[*]From a terminal or from deskbar-applet, type "gedit ~/.rungconf.sh".
[*]Paste and then save the following into it:
```

#!/bin/bash
G_SLICE=always-malloc gconf-editor

```
[*]From a terminal, chmod 755 ~/.rungedit.sh. Note that the . before the name will make it hidden so type ls -a if you want to see the file.
[*]Right click at an empty spot on your panel --> Add to Panel --> Custom Application Launcher. 
[*]The name doesn't matter, but type in /home/**yourusername**/.rungedit.sh for the command and make sure to select an icon. 
[*]Hit Ok and now you have a way to get to gconf-editor without it crashing.
[/LIST] 
[/INDENT]

**Fixing ATI x700 XGL Hard locks**
[INDENT][http://ubuntuforums.org/showthread.php?t=150854]("http://ubuntuforums.org/showthread.php?t=150854")[/INDENT]

**Minimizing windows shows an ugly black border around them or is choppy.**
```

gconftool-2 --set --type boolean /apps/panel/global/enable_animations "False"
gconftool-2 --set --type boolean /desktop/gnome/interface/enable_animations "False"

```
**Animations like wobbly windows or the cube are choppy.**
[INDENT]There is a patch in Xgl cvs that prevents Xgl from slowing down when the CPU is maxed out. If you install the version of Xgl from QuinnStorm's repository, you shouldn't notice this problem.[/INDENT]
```

gconftool-2 --set --type boolean /apps/compiz/general/screen0/options/detect_refresh_rate "False"
gconftool-2 --set --type integer /apps/compiz/general/screen0/options/refresh_rate "60"

```
**rdesktop connections are transparent and hard to see or look strange.**
[INDENT][http://ubuntuforums.org/showpost.php?p=867127&postcount=4]("http://ubuntuforums.org/showpost.php?p=867127&postcount=4")[/INDENT]
**Some windows wont let me move them.**
[INDENT]Hold ALT and drag the window to move it or update to the latest compiz from QuinnStorm's repositories.[/INDENT]
**Some windows won't let me close them.**
[INDENT]Try ALT F4 or update to the latest compiz from QuinnStorm's repositories. If you are on a laptop or a weird keyboard, make sure the fn key is enabled.[/INDENT]
**Some windows won't let me resize them.**
[INDENT]Hold ALT, right click and drag the window.[/INDENT]


Feel free to leave a reply if you have suggestions or new threads that I should put in here. I will update this post as often as I can.[/QUOTE]

---

### Post by hezral on 2006-03-21
great thanks!

---

### Post by krusbjorn on 2006-03-21
*** THIS POST IS EXTREMELY DEPRECATED ***

In this post I will try to summarize the [first thread you mentioned under "Once you got it working"]("http://ubuntuforums.org/showthread.php?t=139265"), in which there has been an amazing activity during the last couple of days. The first post contains a guide by DeeZiD that makes installing xgl and compiz piece of cake.

Far back in the thread, QuinnStorm has attached compiz, compiz-gnome, compiz-kde packages as well as a fresh snapshot of gnome-window-decorator, that adds A LOT of functionality and solves all three annoyances you mentioned. See [this]("http://ubuntuforums.org/showpost.php?p=848893&postcount=891")   post for the compiz* debs:

**The current plugins** (except for the usual cube, decoration, fade, move, place, resize, rotate, scale, switcher, wobbly and zoom) in the "Quinndebs" are:

**Minimize:**
Makes windows "zoom in" from the mouse pointer when opened, and "zoom out" to the mouse pointer when closed. (Cred to QuinnStorm)

**Opaquefocus:**
Athropos came up with a plugin that allows to set opacity for unfocused windows. Quinnstorm patched it to allow to set opacity for the focused window, and _avatar patched it further, to allow to set brightness and saturation for unfocused windows. The fade effect speed in this plugin is directly dependent on the speed set in the fade plugin.

**There are also extended functionality for these plugins:**

**Move:**
moving_window_opacity_level - set opacity level for windows being moved. (Cred to QuinnStorm)

**Switcher:**
all_desktops - when unchecked, only the windows in the current workspace will appear in the switcher. (Cred to QuinnStorm)

**Scale:**
Athropos hacked the scale plugin, and added the ability to set the opacity for unfocused windows when using the scale (exposé-like) plugin.

Quinn also just a couple of hours ago compiled the latest update of the **gnome-window-decorator**, and attached the binary and the source code to [this]("http://ubuntuforums.org/showpost.php?p=848917&postcount=892") post. This includes Quinn's hack that lets ju move, resize and close dialog windows (like the search dialog in synaptic), adds options to have windows stay on top and stick to all workspaces (when right-clicking the menubar), and solves a couple of bugs. To install, simply replace /usr/bin/gnome-window-decorator (but backup the old one first!), and restart it.

Also, Athropos made a plugin called **transset** that lets you in advance set opacity levels for any application you want, which is applied to the window when you execute the app. See [this]("http://www.ubuntuforums.org/showpost.php?p=839591&postcount=629")  post. Note that the opaquefocus plugin brutally will reset any opacity levels set by transset, if enabled. (This plugin is not yet in Quinns debs, but she says that it will as soon as she gets ahold of the source code).

I'm not 100% sure that I got everything summarized here, but I think so. I also hope that I have given credits to the right people, but the speed of which new patches and plugins have arrived has been so great it has been really hard to keep track. I apologise if I have made any mistakes, and please drop me a PM if you encounter any incorrectly stated facts.

Finally, Who is running a **blog** in which he tries to keep up with the latest and greatest in a more overviewable way. If you don't have the time or commitment to read the entire thread, at least look through his blog. It makes this mess more than overviewable, but is more detailed than this post. [http://compiz.blogspot.com/](http://compiz.blogspot.com/). For directions for how to use those plugins, check the blog or search through the thread.

As I stated earlier, this post ONLY summarizes what has been going on in [this particular thread]("http://ubuntuforums.org/showthread.php?t=139265"). I will try to keep this post updated as far as that thread concerns.

 -Krusbjorn

**[COLOR="Red"]EDIT:[/COLOR] To stay updated with QuinnStorm's packages, check [this]("http://ubuntuforums.org/showthread.php?t=148472") thread out.**

---

### Post by AnThOnYhO on 2006-03-21
Good thread.

---

### Post by TrinitronX on 2006-03-21
Ah... finally one main thread to sort out all the different ones. 
I've got a suggestion for something to add to common annoyances section.

Choppy/Laggy window wobble effects
Go into gconf-editor and change the key apps->compiz->general->screen0->options->refresh_rate to 60.

---

### Post by mfarley on 2006-03-22
Thank You!!!

And maybe add to the list of annoyances:

-Unable to adjust mouse sensitivity via GUI

---

### Post by palermi on 2006-03-22
good job ! now it more easy find a solution.

The best post is [http://www.ubuntuforums.org/showthread.php?t=139265](http://www.ubuntuforums.org/showthread.php?t=139265) . 

QuinnStorm is the best !

---

### Post by mcduck on 2006-03-22
To remove those ugly wireframe animations that Gnome has by default:
Open gconf-editor, go to apps/panel/global and deselect 'enable_animations'

This makes Compiz animations smoother, as your machine is not trying to do two different animations at the same time for the same window :)

---

### Post by Eklöf on 2006-03-22
[QUOTE=mcduck]To remove those ugly wireframe animations that Gnome has by default:
Open gconf-editor, go to apps/panel/global and deselect 'enable_animations'

This makes Compiz animations smoother, as your machine is not trying to do two different animations at the same time for the same window :)[/QUOTE]


That was a good tip. I have been disturbed by those a long time now..

---

### Post by palermi on 2006-03-22
[QUOTE=mcduck]To remove those ugly wireframe animations that Gnome has by default:
Open gconf-editor, go to apps/panel/global and deselect 'enable_animations'

This makes Compiz animations smoother, as your machine is not trying to do two different animations at the same time for the same window :)[/QUOTE]

thank, but the effect for recycle bin no change :neutral:

---

### Post by Who on 2006-03-22
I will try an keep track of this thread aswell on [http://compiz.blogspot.com](http://compiz.blogspot.com) - which already traks the main plugins/patches threads on these forums and elsewhere on the internet.

Just as an aside - I think discussion of the eye candy should be restricted to the thread that it is relevant to - not just put in this one - it is already hell trying to follow most of them!!

---

### Post by joneZ on 2006-03-22
Maybe some could help with debugging ... 

System:
Dapper: up2date
Dell Latitude D600
ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
radeon driver from xorg.

I still have the problem with all version's after that are in the dapper repostries. That i can't resize the windows. 

I can only maximize them to max 600x600. And when I grab the border-edge
and want to resize manuall it will not let me.

When a programm start in "Maximized Mode" and click then on " Maximize" it
switches directly to 600x600 and stays there forever untill I downgrade
compiz packages to 0.0.2.

Maybe someone has a clue ?

Many thx
Erik

---

### Post by Who on 2006-03-22
I added this introduction to XGL/Copmiz to the [blog]("http://copmiz.blogspot.com") - which fills a hole in the thread - it doesn't explain what it is about!

[http://compiz.blogspot.com/2006/03/introduction-to-compizxgl.html](http://compiz.blogspot.com/2006/03/introduction-to-compizxgl.html)

It says what it is/they are, links to the videos and back to this thread/the forums for how to get it and for tips.

---

### Post by Tharna on 2006-03-22
I set up a repository where I try to keep all the different packages related to xgl/aiglx and compiz. 

```

deb http://kapsi.fi/tharna/ubuntu/ ./

```

Currently there are aiglx packages from gandalfn, depdeb and quinndeb packages from QuinnStorm and admincompiz package from GaRgAm.

AMD64 packages from hva/pdc303 arent included yet, as their package names are the same as the xgl ones.

I would hope that people making those packages could keep me up to date by sending all the packages directly to me so I dont need to crawl those all the time from forums.

---

### Post by Who on 2006-03-22
[QUOTE=Tharna]
I would hope that people making those packages could keep me up to date by sending all the packages directly to me so I dont need to crawl those all the time from forums.[/QUOTE]

If you are going to be doing this then could you CC: me please!? mailforwho <at> googlemail [dot} com

---

### Post by hugmenot on 2006-03-22
Puh, all these threads are overwhelming.

Just want to check with you all, is anybody seeing artifacts at the lower and right window deco boundaries and at the corners of the window title?
I think it was a /there/not there issue but now it's permanent.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=7429&d=1143046674[/IMG]

---

### Post by Tharna on 2006-03-22
[QUOTE=Who]If you are going to be doing this then could you CC: me please!? mailforwho <at> googlemail [dot} com[/QUOTE]

Sure.

---

### Post by reda_ea on 2006-03-22
[QUOTE=g14]
**Making CTRL ALT Delete open up the system monitor like in windows**
```

gconftool-2 --set --type string /apps/compiz/general/screen0/options/run_command1 "<Control><Alt><Delete>"
gconftool-2 --set --type string /apps/compiz/general/screen0/options/command1 "gnome-system-monitor"

```
[/QUOTE]

shouldn't that be   <Control><Alt>Delete  ??

---

### Post by cbudden on 2006-03-22
[QUOTE=reda_ea]shouldn't that be   <Control><Alt>Delete  ??[/QUOTE]

Yes it should be.

Another good one would be gnome-screenshot with Print.

---

### Post by g14 on 2006-03-22
[QUOTE=reda_ea]shouldn't that be   <Control><Alt>Delete  ??[/QUOTE]
I typed those gconf commands from memory, thanks for the fix.

---

### Post by g14 on 2006-03-23
I just thought I would let anyone know that is monitoring this thread that I've added quite a bit to it. I try to update the first page as often as I actually get a chance to with fixes and common issues.

---

### Post by helpme on 2006-03-23
[QUOTE=hugmenot]Puh, all these threads are overwhelming.

Just want to check with you all, is anybody seeing artifacts at the lower and right window deco boundaries and at the corners of the window title?
I think it was a /there/not there issue but now it's permanent.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=7429&d=1143046674[/IMG][/QUOTE]
Yes, I'm having the same issue, though I only see it on the right side.

---

### Post by firingstone on 2006-03-23
Great Job !
Thanks

---

### Post by zvjer on 2006-03-23
[QUOTE=joneZ]ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
radeon driver from xorg.

I still have the problem with all version's after that are in the dapper repostries. That i can't resize the windows. 

I can only maximize them to max 600x600. And when I grab the border-edge
and want to resize manuall it will not let me.

When a programm start in "Maximized Mode" and click then on " Maximize" it
switches directly to 600x600 and stays there forever untill I downgrade
compiz packages to 0.0.2.
Erik[/QUOTE]
Same here! Same Card!
But it's not 600x600. Its 512x512 if you don't count the window decorator.
Quinn says it's a bug in compiz. But it's funny how come the older version isn't buggy.

---

### Post by joneZ on 2006-03-23
[QUOTE=zvjer]Same here! Same Card!
But it's not 600x600. Its 512x512 if you don't count the window decorator.
Quinn says it's a bug in compiz. But it's funny how come the older version isn't buggy.[/QUOTE]


created a new thread .. since this isn't a support thread ...

---

### Post by Melvil on 2006-03-23
[QUOTE=helpme]Yes, I'm having the same issue, though I only see it on the right side.[/QUOTE]

I got the same glitches, on both sides

---

### Post by wolfchri on 2006-03-23
Helllo folks, 

please excuse my stupid question, but will Dapper include out-of-the-box working XGL animations or are all these efforts described here and in other threads necessary in the final Dapper, too? 

To me, the nexessary preparations needed for XGL currently remind me a lot of my Gentoo times :-) Actually, that collides a little bit with the typical ease of installation and setup of Ubuntu ... :mrgreen:

---

### Post by pabloalgar on 2006-03-23
[QUOTE=Melvil]I got the same glitches, on both sides[/QUOTE]

[QUOTE=helpme]Yes, I'm having the same issue, though I only see it on the right side.[/QUOTE]
Me too. A 1 pixel offset between client itself and the right and bottom frame border. Misplaced transparency on the upper corners of the window. Windows doesn't completly fill the desktop in maximized mode. It all started from the last X11 updates.
I think it has nothing to do with XGL nor Compiz.

---

### Post by hugmenot on 2006-03-23
[QUOTE=pabloalgar]Me too. A 1 pixel offset between client itself and the right and bottom frame border. Misplaced transparency on the upper corners of the window. Windows doesn't completly fill the desktop in maximized mode. It all started from the last X11 updates.
I think it has nothing to do with XGL nor Compiz.[/QUOTE]

Really? I'm seeing that for quite some time. But I've been making compiz  from CVS since the early days.

EDIT: where is the bug tracker for XGL/compiz?

---

### Post by g14 on 2006-03-23
[QUOTE=hugmenot]Really? I'm seeing that for quite some time. But I've been making compiz  from CVS since the early days.

EDIT: where is the bug tracker for XGL/compiz?[/QUOTE]

Since the cvs for Xgl/compiz lives on fdo, so does the bugtracker. While Xgl/compiz do not have their own components in the bugzilla, you just file a bug on xorg.

Here is the xorg bugtracker which you should file bug reports against:
[https://bugs.freedesktop.org/](https://bugs.freedesktop.org/)

Doing a search for Xgl or for compiz will return a few results for you to look at.

---

### Post by Fudgie on 2006-03-24
[QUOTE=zvjer]Same here! Same Card!
But it's not 600x600. Its 512x512 if you don't count the window decorator.
Quinn says it's a bug in compiz. But it's funny how come the older version isn't buggy.[/QUOTE]
It's not a 'bug' as such, it's davidr limiting window sizes to your cards reported max texture size.

---

### Post by joneZ on 2006-03-24
[QUOTE=Fudgie]It's not a 'bug' as such, it's davidr limiting window sizes to your cards reported max texture size.[/QUOTE]

Ok maybe you are right but ....

- why is it working under fglrx without these problems, when my card say I have
this or this max texture size ?? fglrx doesn't care about max texture size if my
card report these to the driver or am I wrong ? 

- why is it working for the first time with radeon driver .. Example If I update
from 0.0.2 to a newer version and then log in and open firefox it start's wonderfull maximized and when I click on maximize button it jumps directly to
600x600. That makes no sense in my eyes, that it works once

So maybe it is a bug in radeon driver ?

Erik

---

### Post by web250 on 2006-03-24
Anyone know if there is, or will be a fix for XGL and Tv Tuners? ie: so you can use tvtime?

---

### Post by g14 on 2006-03-26
[QUOTE=web250]Anyone know if there is, or will be a fix for XGL and Tv Tuners? ie: so you can use tvtime?[/QUOTE]
If tvtime uses OpenGL for output, there is still some work that needs to be done for it to function properly...

---

### Post by web250 on 2006-03-26
[QUOTE=g14]If tvtime uses OpenGL for output, there is still some work that needs to be done for it to function properly...[/QUOTE]
Ya that's what I figure.

The gentoo forums say to try:
```
xdtv -noxv
```

I'm home on spring break and won't have my main PC until April 2nd, so I'll try it then.

---

### Post by The Warlock on 2006-03-26
I've been using Compiz and XGL, and every hour or two, my xserver crashes and gdm restarts. Has anyone else had similar problems? I've moved back to Xorg and Metacity for now because of it.

Compiz sure looks nice, though.

---

### Post by g14 on 2006-03-26
[QUOTE=The Warlock]I've been using Compiz and XGL, and every hour or two, my xserver crashes and gdm restarts. Has anyone else had similar problems? I've moved back to Xorg and Metacity for now because of it.

Compiz sure looks nice, though.[/QUOTE]

System --> Preferences --> Sessions --> Startup Programs --> Add
xmodmap /usr/share/xmodmap/xmodmap.en

Try that and see if it fixes the problem. For me, thats all I needed to add and it worked.

---

### Post by g14 on 2006-03-26
Also, I added a section on how to make the corners enable the Mac OS X-ish scale plugin.

---

### Post by zvjer on 2006-03-27
[QUOTE=joneZ]Ok maybe you are right but ....
- why is it working under fglrx without these problems, when my card say I have
this or this max texture size ?? fglrx doesn't care about max texture size if my
card report these to the driver or am I wrong ? 
<cuT>
So maybe it is a bug in radeon driver ?
Erik[/QUOTE]
How did you manage to get fglrx+xgl running on R250 anyway? :-k 
I tried in a lot of ways and all I got is a messed up screen.
Note: fglrx works fine on my R250 without xgl.
I would like to try fglrx if there's a way.. Yesterday I was reading about aiglx but that seems to be even more ](*,)  than xgl ;)

---

### Post by ntd on 2006-03-27
Thanks for this thread, it made it a lot easier to catch up with XGL/Compiz and get all the new goodies installed, I had a lot of slowness with the out of the box dapper versions with my nvidia card, but now everything is super responsive

---

### Post by risings0n on 2006-03-27
It seems trailfocus dont work well with my mplayer windows. Although i have added MPlayer to the list of windows to be ignored by trailfocus, it compiz keeps crashing whenever an MPlayer window loses focus.

---

### Post by Shadou on 2006-03-27
Thanks for adding my post to this index :)

---

### Post by apoclypse on 2006-03-28
I tried the new compiz quinn packages. i don't know if I should post this here, but what I'm asking is more of a refinement than a feature. Right now the scale plugin works great but is not very practical. It just seems to bring whatever window you pick to the front regardless of its position when what it should be doing is centering the window if they are not in the middle of the screen. An example, I have an application somewhere to far bottom right where all you can see is the title bar. Scale will just bring this back to its current position defeating the purpose of it as a task manager imo. It should focus the windows selected to middle in a ready to use state. The switcher should do this too. However it could be an option if people like the current way.

Another Idea just popped into my head. Right now the quin compiz packages have this great zoom effect when you close windows and stuff. The zoom goes towards the mouse position, in other words things open and close accrding the mouse position. Why not have these things come from the application menu instead, this will be kind of like the light tracing thing that mcosx has, wher application originate and terminate to the same position. For example if I open a folder I would expect the zoom effect to come from the folder not from the current mouse position. I;m very confused with all thes folders and programs coming from all over the place. Its distracting, when it really shouldn't be. If I knew anything about programming in comppiz I would try to fix these myself as they are really only minor fixes (or maybe not).

---

### Post by g14 on 2006-03-28
[QUOTE=apoclypse]I tried the new compiz quinn packages. i don't know if I should post this here, but what I'm asking is more of a refinement than a feature.[/QUOTE]

Since this is a feature request regarding [Quinn's awesome debs]("http://ubuntuforums.org/showthread.php?t=148472"), maybe you should post this in [her thread]("http://ubuntuforums.org/showthread.php?t=148472").

---

### Post by Syirrus on 2006-03-28
I would like to see a Genie like effect if all possible when you minimize and restore windows to and from your task bar

---

### Post by xplode_me on 2006-03-28
Hmmmm

Sorry, kinda lost some pages of the thread.. So, any way to get gDesklets to work nice along Xgl ? :)

---

### Post by Bou on 2006-03-29
I updated my XGL and compiz packages by adding the repos mentioned in [http://ubuntuforums.org/showthread.php?t=148860](http://ubuntuforums.org/showthread.php?t=148860) and [http://ubuntuforums.org/showthread.php?t=148472](http://ubuntuforums.org/showthread.php?t=148472).

I don't know if XGL is really working (I get "no direct rendering" on glxinfo), but I had to lauch metacity because I don't get any window borders with compiz. And there aren't any icons on my desktop, Nautilus doesn't seem to be drawing them.

Any way to fix this? Thanks!

---

### Post by | MM | on 2006-03-29
Hey, bit of bug for me with rhythmbox, say u minimise a the player to the notification area, on maximising rhythmbox again you get artifacts and rhyhmbox isnt displayed properly.

---

### Post by junior aspirin on 2006-03-29
does anyone have a problem with openoffice crashing under gnome/compiz/ati

i open i file suchas a powerpoint file or odt. the scroll the page and open office just dies on me. it works fine on a new blank document, it also works fine on a new acount not running compiz. i also deleted and open office config files from my home directory, but it still happens. it looks like it is to do with compiz to me.

can anyone confirm?

---

### Post by goober99 on 2006-03-29
I liked how in Gnome before I installed Compiz, dragging a window near another window offered resistance allowing you to easily line windows up next to one another. Is there a way to enable this using Compiz also?

---

### Post by g14 on 2006-03-29
[QUOTE=goober99]I liked how in Gnome before I installed Compiz, dragging a window near another window offered resistance allowing you to easily line windows up next to one another. Is there a way to enable this using Compiz also?[/QUOTE]
Hold CTRL for a similar but more eyecandy-ish effect to line up windows. It will only work if you have the wobbly plugin loaded.

---

### Post by MacSlow on 2006-03-30
Some people with nvidia-cards running the closed-source driver might enjoy this little [hint]("http://macslow.thepimp.net/?p=34").

Best regards...

MacSlow

---

### Post by TerminX on 2006-03-30
[QUOTE=MacSlow]Some people with nvidia-cards running the closed-source driver might enjoy this little [hint]("http://macslow.thepimp.net/?p=34").

Best regards...

MacSlow[/QUOTE]
I've found in trials with a Ti4200 that using FSAA and AF in conjunction with Xgl drives performance way down without giving any noticeable improvement in visual quality.  Can anyone else share their experiences?

Vsync, however, is a must. :)

---

### Post by nrwilk on 2006-04-02
g14,

Please add to the first post the info for our new compiz/eyecandy forum.

This was created by Quinnstorm, iXce, thirion, et al.

it is located here:
[http://compiz.ed3n.com/](http://compiz.ed3n.com/)

It is many people's hope that it will take the Xgl/Compiz load of threads off of the Dapper forum.  Please encourage people to use it as a replacement for the Dapper forum for Xgl/Compiz/eyecandy topics.

Thank you! :D

---

### Post by dreamsINdigital on 2006-04-02
I disabled the Gnome animations, and that got rid of the wireframe animations when launching a program, but it still animates when I open the wastebasket.  Does anyone know how to get rid of it for the wastebasket?

---

### Post by Owdy on 2006-04-03
I see 2 kind of instructions around:

```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher & xmodmap /usr/share/xmodmap/xmodmap.us
``` 
```
#!/bin/bash
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus & xmodmap /usr/share/xmodmap/xmodmap.us
``` 
What is that extra 'opaquefocus' in that second one? I use that. Do i need it?

---

### Post by chanders on 2006-04-03
[QUOTE=Owdy]I see 2 kind of instructions around:

```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher & xmodmap /usr/share/xmodmap/xmodmap.us
``` 
```
#!/bin/bash
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus & xmodmap /usr/share/xmodmap/xmodmap.us
``` 
What is that extra 'opaquefocus' in that second one? I use that. Do i need it?[/QUOTE]

[SIZE="4"]RTWF[/SIZE] - Read the [wiki]("https://wiki.ubuntu.com/compiz") first!

---

### Post by Owdy on 2006-04-03
Thanks!

---

### Post by Rob2687 on 2006-04-03
I am getting crashes which I think are related to Xgl/compiz. When it crashes the screen goes all garbled and everything locks up but sometimes I can still hear music playing through the speakers.... This happens pretty frequently.
It never happened with the older Xgl packages. I've reinstalled everything since then and moved to the ones from Quinns repos. :(

---

### Post by g14 on 2006-04-03
[QUOTE=Owdy]I see 2 kind of instructions around:

```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher & xmodmap /usr/share/xmodmap/xmodmap.us
``` 
```
#!/bin/bash
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus & xmodmap /usr/share/xmodmap/xmodmap.us
``` 
What is that extra 'opaquefocus' in that second one? I use that. Do i need it?[/QUOTE]
opaquefocus was buggy and removed. The same effect + more can be achieved with the trailfocus plugin and the trailfocus plugin is less buggy. I never liked either of them, but that is just me.

---

### Post by nik on 2006-04-03
Just wondering, would it be difficult to implement animated wallpapers like e17 uses ( [http://www0.get-e.org/Backgrounds/Animated/](http://www0.get-e.org/Backgrounds/Animated/) )? It's really nice when done properly.

---

### Post by i386DX on 2006-04-03
I installed XGL/Compiz (folowing the sticky on this forum) and everything worked.
I don't want to start XGL/Compiz as default, so it isn't started when I reboot my pc.

When I try to start it with 'thefuture' everything works except the shortcuts (F12, CTRL-ALT-left/right....). Even when I enter: 
xmodmap  usr/share/xmodmap/xmodmap.be first (I think this command has something to do with key-binding)?

When I look in compiztools I see that the keys are properly defined...

---

### Post by Owdy on 2006-04-03
[quote=i386DX]

When I try to start it with 'thefuture' everything works except the shortcuts (F12, CTRL-ALT-left/right....). Even when I enter: 
xmodmap  usr/share/xmodmap/xmodmap.be first (I think this command has something to do with key-binding)?

When I look in compiztools I see that the keys are properly defined...[/quote] I got same issue. Then i did this

[http://www.ubuntuforums.org/showthread.php?t=131267]("http://www.ubuntuforums.org/showthread.php?t=131267")
> Now go to:

apps>compiz>general>screen0>option

Then turn off the "detect_refresh_rate" option.

Then set the "refresh_rate" to 60 
After that, everything worked.

---

### Post by krmiller on 2006-04-04
I am a little confused.   I have a 915 intel graphics chipset.  When I run glxgears I get 1500 fps.  I have followed the guide for installing xgl/compiz that included adding the quinnstorm repositories.  I then installed the latest compiz, comiz-gnome and xserver-xgl.  When I launch gconf-editor under apps there is no compiz.  Not sure what I am missing.  Any help would be appreciated.

---

### Post by Rob2687 on 2006-04-04
I'm having problems installing the latest updates for Dapper. Which resulted in a busted Xgl.

I am getting this error.

```
robert@ubuntu:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/1569kB of archives.
After unpacking 4231kB of additional disk space will be used.
(Reading database ... 85799 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@ubuntu:~$

```

---

### Post by g14 on 2006-04-04
[QUOTE=Rob2687]I'm having problems installing the latest updates for Dapper. Which resulted in a busted Xgl.

I am getting this error.

```
robert@ubuntu:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/1569kB of archives.
After unpacking 4231kB of additional disk space will be used.
(Reading database ... 85799 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@ubuntu:~$

```[/QUOTE]

It is conflicting on a man page! This is an easy fix:
```

sudo dpkg -i --force-all /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb

```

---

### Post by funkenstein on 2006-04-05
[quote=g14]It is conflicting on a man page! This is an easy fix:
```
sudo dpkg -i --force-all /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu7_i386.deb
```[/quote] THANKS!! I was wondering about that....


on another note - can anyone tell me: I've got the latest CVS stuff running great, but XGL conflicts with xover office, which is essential to me. Is there somewhere else I can edit, besides the gdm.conf-custom, so as to have xgl replace x *only when user1 logs in*? In other words, user1 gets thefuture goodness, and user2 gets xover office goodness... maybe somewhere in the xsessions so it's selectable?? 

I want to demo my windiz friends XGL, but I want to work too... editing gdm.conf-custom is too much hassle. Heck, it's even too much hassle to type it in this post :P

EDIT: a typo and:
would [http://wiki.ubuntu.com/XglHowto](http://wiki.ubuntu.com/XglHowto), gnomerc step do the trick? I assume not cuz it's still swapping Xorg for Xgl...

---

### Post by kristian on 2006-04-05
I'm trying to get Xgl working but it seems I can't really get there...

First of installing everything as the howto shows and when I'm trying to start Xgl i get the following error
```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  173
  Current serial number in output stream:  174
``` 
If I however remove the libGL.so.1 symlink in /usr/lib/ and add a new symlink against the nvidia drivers libGL.so.1.0.8178 instead Xgl works fine. But when I then try to launch compiz i get:
```

compiz.real: GLX_EXT_texture from pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0name of display: :0.0
``` 
But then again if I execute glxinfo I can clearly see that GL_EXT_texture_from_pixmap is there.
```

display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 420 Go 32M/AGP/SSE2/3DNOW!
OpenGL version string: 1.2 (1.5.5 NVIDIA 81.78)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

Anyone that has any suggestions or a solution to this problem?

---

### Post by mickymouse on 2006-04-06
Thanks very much for this tutorial.

---

### Post by bvucinic on 2006-04-06
Just made a dist-upgrade (new xgl). If I want to see a video no matter which player (vlc, totem) X crashes.
Anyone else experiencing the same?
I've been running xgl/compiz for a couple of weeks with no problems (nvidia).

---

### Post by flibblesan on 2006-04-06
[QUOTE=bvucinic]Just made a dist-upgrade (new xgl). If I want to see a video no matter which player (vlc, totem) X crashes.
Anyone else experiencing the same?
I've been running xgl/compiz for a couple of weeks with no problems (nvidia).[/QUOTE]
same for me, but I got VLC working if I change the output to use X11. XV output crashes, just like Totem does.

I think XV is borked somehow.

---

### Post by caspian on 2006-04-07
I'm using XGL on a laptop, and sometimes I need to kell XGL to save batter life. Is there a safe way to stop the Xgl server? (I can stop compiz, but since Xgl is till running, it still eats up my battery)

Thanks!

---

### Post by bvucinic on 2006-04-08
[QUOTE=flibblesan]same for me, but I got VLC working if I change the output to use X11. XV output crashes, just like Totem does.

I think XV is borked somehow.[/QUOTE]


sudo apt-get remove xserver-xgl
sudo apt-get install xserver-xgl
reboot

fixed the problem! :)

---

### Post by DerGuteMoritz on 2006-04-08
Hi everyone, first time poster, medium time reader :) 
Having benefited from this forum so much, I'd like to contribute some [snippet I've found in the Kororaa forums which helped me enabling the super-key for my German keyboard]("http://kororaa.org/forums/viewtopic.php?t=506"). Additionally, I discovered quite a nice way to set the keyboard layout to xmodmap.de (or xmodmap.[yourlocale]) for every user logging in with gdm. There is a file /etc/gdm/PostLogin/Default-sample. Simply rename it do Default:
```
sudo mv /etc/gdm/PostLogin/Default-sample /etc/gdm/PostLogin/Default
```
Now put the following lines in it:
```

xmodmap /usr/share/xmodmap/xmodmap.de
xmodmap -e "keycode 115 = Super_L"  # Bind left and right keycodes to Super_L/R
xmodmap -e "keycode 116 = Super_R"
xmodmap -e "add Mod2 = Super_L"     # I guess Mod2 means Super (Mod3 for Hyper)
xmodmap -e "add Mod2 = Super_R"

```

Voilá - your super-key should be working after logging in with gdm now, as well as your locale settings (i. e. shift + backspace doesn't cause a restart of X etc.)

Note: As mentioned in the thread I've linked to above, your keycodes may be different than the ones I provide here (they work for German keyboards, at least). To find out your specific super-keycode, open a terminal end execute:
```
xev
```
A small white window with a rectangular black bordered box in it will appear. Now press your super-key(s) (which is, of course, the Windows key). The terminal should output something like this:
```
KeyPress event, serial 27, synthetic NO, window 0x2a00001,
    root 0x52, subw 0x0, time 2051453682, (1000,339), root:(1014,463),
    state 0x0, **[COLOR="DarkOrange"]keycode 115[/COLOR]** (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

```
The part I have highlighted above is your specific keycode!

---

### Post by Roderik on 2006-04-08
I've skipped the XGL threads from the moment i read that iet wouldn't work in twinview dual screen setups. Is there any change or progress in that area?

---

### Post by poofyhairguy on 2006-04-08
[QUOTE=Roderik]I've skipped the XGL threads from the moment i read that iet wouldn't work in twinview dual screen setups. Is there any change or progress in that area?[/QUOTE]

Not really.

I use Twinview with XGL now and I can stand it. The biggest problem is that when you maximize things it covers both screens. 

From what I can tell, the problem won't go away until Nvidia users are able to run Compiz on something other than XGL.....

---

### Post by thebluesgnr on 2006-04-08
[QUOTE=funkenstein]THANKS!! I was wondering about that....


on another note - can anyone tell me: I've got the latest CVS stuff running great, but XGL conflicts with xover office, which is essential to me. Is there somewhere else I can edit, besides the gdm.conf-custom, so as to have xgl replace x *only when user1 logs in*? In other words, user1 gets thefuture goodness, and user2 gets xover office goodness... maybe somewhere in the xsessions so it's selectable?? 

I want to demo my windiz friends XGL, but I want to work too... editing gdm.conf-custom is too much hassle. Heck, it's even too much hassle to type it in this post :P
[/QUOTE]

There is something you can do: edit the gdm.conf-custom file, and make sure the [servers] section reads:
0=Xgl
1=Standard

(I'm assuming you have [server-Xgl] to start the Xgl server, that is, you didn't call the Xgl line by [server-Standard].

Now, when you start your system you'll be able to login from the Standard server. Type Ctrl+Alt+F7 to get the Xgl server, and Ctrl+Alt+F8 to get back to the Standard server.

---

### Post by Mr.Auer on 2006-04-09
I installed the latest compiz with the necessary dependencies from Quinns repo, all other updates went fine except xserver-xgl version 7.0.0-0ubuntu5..when i try to update this one i get the following message:
/var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
>
And leaves the xgl package not updated...What should I do? It seems to work with the older xgl package too, but.. :) My system is a Flight 6 clean install, all updates from repos, so also latest repo-versions of xserver-xorg-core and others.
Thanks for any suggestions..

EDIT:oo, thx krusbjorn, it worked :) and how fast can u reply :P

---

### Post by krusbjorn on 2006-04-09
[QUOTE=Mr.Auer]I installed the latest compiz with the necessary dependencies from Quinns repo, all other updates went fine except xserver-xgl version 7.0.0-0ubuntu5..when i try to update this one i get the following message:
/var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
>
And leaves the xgl package not updated...What should I do? It seems to work with the older xgl package too, but.. :) My system is a Flight 6 clean install, all updates from repos, so also latest repo-versions of xserver-xorg-core and others.
Thanks for any suggestions..[/QUOTE]

sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz

---

### Post by Mr.Auer on 2006-04-09
One more trouble..I cant change keybinding in gconf-editor to terminate the Switcher plugin (alt-tab initiates), and the switcher remains on the screen after I stop pressing alt-tab..It would be ok if i could change the binding, but the keys always change back to ReleaseAlt-L, which dont work like it should...Ideas? Can I change the binding directly with a console command..
Thx...Otherwise the latest xgl+compiz is running sweet, finally window transparency works for me! (useful huh)

---

### Post by barrosz on 2006-04-09
[QUOTE=Mr.Auer]One more trouble..I cant change keybinding in gconf-editor to terminate the Switcher plugin (alt-tab initiates), and the switcher remains on the screen after I stop pressing alt-tab..It would be ok if i could change the binding, but the keys always change back to ReleaseAlt-L, which dont work like it should...Ideas? Can I change the binding directly with a console command..
Thx...Otherwise the latest xgl+compiz is running sweet, finally window transparency works for me! (useful huh)[/QUOTE]
remove SPLASH from gconf fade plugin.

---

### Post by Mr.Auer on 2006-04-09
Great, now it works as it should :) Thanks..

---

### Post by lanux on 2006-04-12
I have installed compiz0.0.9-0ubuntu1 and xserver-xgl7.0.0-0ubuntu4 but i have 2 problem.
1 - When pressed <ALT><TAB> pop up the window switcher - ok
     The switching is working good ,but always visibe ! 
     When I close 1 window the switcher is turning off 
2 - When running compiz in System-Theme-Theme Details-**window border** do not visible

what do you think ?

---

### Post by krusbjorn on 2006-04-12
[QUOTE=lanux]I have installed compiz0.0.9-0ubuntu1 and xserver-xgl7.0.0-0ubuntu4 but i have 2 problem.
1 - When pressed <ALT><TAB> pop up the window switcher - ok
     The switching is working good ,but always visibe ! 
     When I close 1 window the switcher is turning off 
2 - When running compiz in System-Theme-Theme Details-**window border** do not visible[/QUOTE]

1. Remove "Splash" from window_types for your fade plugin in gconf-editor (apps->compiz->plugins->fade->screen0->options)

2. Yeah, no work-around at the time. Compiz isnt compatible with metacity themes, so you are stuck with the current window borders until someone has developed theming capabilities.

---

### Post by dustobub on 2006-04-12
I just did a clean server install of flight 6 and installed xgl and compiz as per the xglati howto in the wiki. Almost everything works great. However, I dont have any window title bars or outlines, no "X" button, and can't move windows. I am sure it is something easy but I didn't see anything about my problem in the xgl threads. Thanks.

Dustin

---

### Post by idn on 2006-04-12
Hi

does anyone know how to make the gnome panel menu transparent? I have trried Gnome-panel 80 in transet but it does nothing

Thanks!

---

### Post by krusbjorn on 2006-04-13
[QUOTE=idn]Hi

does anyone know how to make the gnome panel menu transparent? I have trried Gnome-panel 80 in transet but it does nothing

Thanks![/QUOTE]

It doesnt work with transset, but you can still alt+scroll to change the opacity.

---

### Post by eokorie on 2006-04-13
I currently have a dual head setup with dapper drake.... will xgl break this if I set it up?

---

### Post by idn on 2006-04-13
[QUOTE=krusbjorn]It doesnt work with transset, but you can still alt+scroll to change the opacity.[/QUOTE]

Thanks, I can now change the transparency of the panel - but not of the main gnome menu. If there no way to automatically make it transparent?

---

### Post by ninja_indiano on 2006-04-14
I had this problem when I upgraded last night. Use the repositories listed on [this page]("http://compiz.ed3n.com/viewtopic.php?id=74"), and do apt-get dselect-upgrade. Then reboot, and compiz should work again. The latest compiz needs an updated libmesa.

thanks to Stormy Eyes

[http://compiz.ed3n.com/viewtopic.php?id=74](http://compiz.ed3n.com/viewtopic.php?id=74)

---

### Post by krusbjorn on 2006-04-14
[QUOTE=idn]Thanks, I can now change the transparency of the panel - but not of the main gnome menu. If there no way to automatically make it transparent?[/QUOTE]

No way to make menus transparent yet.

---

### Post by cRoMo on 2006-04-14
Guys, there is an important bug in libcairo2 that is provided with repositories. It breaks subpixel rendering for GTK apps. I think you should know that, it took me a couple of hours to find out what has happend.

---

### Post by kudeta on 2006-04-14
is that whats making my perl-tk apps fail to load??

---

### Post by g14 on 2006-04-14
[QUOTE=eokorie]I currently have a dual head setup with dapper drake.... will xgl break this if I set it up?[/QUOTE]
[http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg](http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg) <-- video of dual head xgl

---

### Post by Melvil on 2006-04-15
I have dual head running on Xgl on my Ati 9700 mobility

---

### Post by didobuntu on 2006-04-15
Hi all,
Sorry for the question: How can I understand what XGL and/or Compiz is. Is it an alternative gnome ? or it functions within it ? Can that be installed on Breezy ?:confused: 

Is there a topic where a Compiz/Xgl beginner can understand. ](*,) 

Thanks in advance:)

---

### Post by sYs^ on 2006-04-15
Hi,

[https://wiki.ubuntu.com/compiz](https://wiki.ubuntu.com/compiz)
[http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl)
[http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)
[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)
[http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/)
[http://compiz.ed3n.com/](http://compiz.ed3n.com/)

It can be installed on Breezy.

(I use xgl and compiz too, check my desktop in my signature if you're interested :p)

Good Luck and Have Fun :>

---

### Post by didobuntu on 2006-04-15
Thanks sYs I will try it.

---

### Post by Sushi on 2006-04-16
[QUOTE=g14][http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg](http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg) <-- video of dual head xgl[/QUOTE]

:shock:

---

### Post by pwrstick on 2006-04-16
Anyone else having problems Alt-Mouse Wheeling to get transparencies applied to windows?  I cannot alt-click on a windows title bar to get the transparency menu, so I cannot set transparencies at all.

---

### Post by pwrstick on 2006-04-16
Wow sushi that's pretty sweet.  I like the water plugin!

---

### Post by g14 on 2006-04-16
[QUOTE=pwrstick]Anyone else having problems Alt-Mouse Wheeling to get transparencies applied to windows?  I cannot alt-click on a windows title bar to get the transparency menu, so I cannot set transparencies at all.[/QUOTE]
You don't ALt click on the titlebar.

Try holding alt and using the mouse scroll wheel. That is how you make a window transparent. You could also use the transset plugin to make a window always start with a certain transparency. I use it to open up all gaim windows at 85% transparency and gnome-terminal at 80% transparency.

---

### Post by pwrstick on 2006-04-16
[QUOTE=g14]You don't ALt click on the titlebar.

Try holding alt and using the mouse scroll wheel. That is how you make a window transparent. You could also use the transset plugin to make a window always start with a certain transparency. I use it to open up all gaim windows at 85% transparency and gnome-terminal at 80% transparency.[/QUOTE]

Sorry I should have been more clear.  Alt-Mousewheeling anywhere doesn't seem to be working for me.  I was pointing out the alt (right) click on the title bar point to point out I'm using the newer build.

BTW I can't get other plugins to load so I don't have transset.

---

### Post by mordaha on 2006-04-16
The Gnome tray (notification area) is not working with Xgl+compiz
It is always empty...

The only icon visible in tray - is the icon of rhythmbox

There are no icons of licq, raki for example...

---

### Post by coldrick on 2006-04-17
Dumb question, sorry.

I can't find out how to define the "super" key. Someone said that the "windows" key is it by default, but not for me.

Suggestions, pointers?

Regards,
David

---

### Post by Horizon on 2006-04-17
[QUOTE=coldrick]I can't find out how to define the "super" key. Someone said that the "windows" key is it by default, but not for me.[/QUOTE]

If you're using Gnome, System>Preferences>Keyboard>Layout Options>Alt/Win Key Behaviour
and then select "Meta is mapped to the Win-keys" 
I really have no idea where it would be in the KDE menus, only ever used it once with knoppix.

---

### Post by coldrick on 2006-04-18
That worked, thanks Horizon. 

Rather obscure that "Meta is mapped to the Win-keys" works and not
"Super is mapped to the Win-keys", huh?

Best regards,
David

---

### Post by pwrstick on 2006-04-18
[QUOTE=mordaha]The Gnome tray (notification area) is not working with Xgl+compiz
It is always empty...

The only icon visible in tray - is the icon of rhythmbox

There are no icons of licq, raki for example...[/QUOTE]

Interesting you should have this problem too as I am running this in Breezy.  I just figured it was some conflict with Breezy.  I found the solution to be was to right click and re-add everything.

Sucks I know.  And I've done it twice now.  But I have no way of figuring out what else is going on because I'm not that knowledgeable with GNU/Linux.

---

### Post by motivez on 2006-04-18
I remember reading somewhere that you can make it so the rotate automatically begins switching when you move your mouse to the very edge of the screen.. but I can't seem to find where I saw that again

Can someone tell me how to enable it? :)

---

### Post by dreamsINdigital on 2006-04-18
[QUOTE=motivez]I remember reading somewhere that you can make it so the rotate automatically begins switching when you move your mouse to the very edge of the screen.. but I can't seem to find where I saw that again

Can someone tell me how to enable it? :)[/QUOTE]
Did you update Compiz?  After I did, it started doing that by itself.

---

### Post by motivez on 2006-04-18
[QUOTE=dreamsINdigital]Did you update Compiz?  After I did, it started doing that by itself.[/QUOTE]

Heh, no. It's taken me two weeks to actually get it to run.. I'm not about to update, at least not yet ](*,)

---

### Post by mrgnash on 2006-04-19
Where do I get the transset plugin from? At first the compiz entry didn't appear in my gconf at all, so I installed the package referred to in this wiki page: [https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati) -- and everything appears to work fine but I don't have any window transparency :confused:

---

### Post by matthinckley on 2006-04-21
[QUOTE=motivez]I remember reading somewhere that you can make it so the rotate automatically begins switching when you move your mouse to the very edge of the screen.. but I can't seem to find where I saw that again

Can someone tell me how to enable it? :)[/QUOTE]
In gconf-editor under /apps/compiz/plugins/rotate/screen0/options  there is a key called edge_flip.  check this.  and if you want there is another one called flip_move that makes it only flip when you are moving windows ( I checked that one too because it got really annoying to me when I would move the mouse out of the way and the screen would flip, only for me to try to flip it back quickly and the cube would begin spinning wildly and landing on the right desktop was like playing roulette.. lol.)

I am having a problem with QEMU..  I use DSL (damn small linux) off a usb flash drive and for some reason it is transparent.  the only way I can make it useable is to have a black terminal window open behind it.  Anyone have a fix for this?

Thanks 

Matt

EDIT:

found fix for QEMU:  off the compiz WIKI:
run this first:
```
export XLIB_SKIP_ARGB_VISUALS=1
```
then run your program

I just added this to the beginning of the script that starts DSL, works great now

---

### Post by Paool on 2006-04-22
Is games under cedega works in xgl with 1.0.8756 nvidia driver?

---

### Post by Xilon on 2006-04-23
Ok I just succeeded in installing Compiz + XGL (w00t!), it's looking great and all but I've got a few problems:

1. I can't find the super key :| I think it's alt but I'm not sure... I tried going to System > Preferences > Keyboard > Layout Options, but it's just blank... I also can't add any other keyboards apart from US :| I think this may be related to me choosing the "x settings" rather than the "gnome settings" when I was asked which Keyboard Settings I would like to use when first using compiz... Any help?

2. The notification area is pretty much useless, the notification icons show up as seperate windows on the desktop[IMG]http://img162.imageshack.us/img162/4808/screenshot5rj.png[/IMG]
I wouldn't be surprised if this was just a KDE think (Kopete, Amarok, Ktorrent) but the same thing happens for aMule. Listen seems to work fine though :| I don't think I've got any more "notification area" apps.

3. On VLC and aMule there are no window decorations and VLC acts really weird aswell. When changing the opacity of the window the whole GUI apart from the actuall screen (where the movie plays) screws up.

Help on any of those would be appreciated. Meanwhile I think I'll go back to good ol' GNOME

Edit: On another note, how do I update the compiz packages; libglitz-glx1 libglitz1 xserver-xgl?```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libglitz-glx1 libglitz1 xserver-xgl
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B/1900kB of archives.
After unpacking 393kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libglitz1 libglitz-glx1 xserver-xgl
Install these packages without verification [y/N]? y
(Reading database ... 110295 files and directories currently installed.)
Preparing to replace libglitz1 0.5.3-0ubuntu2 (using .../libglitz1_0.5.5-0ubuntu2_amd64.deb) ...
Unpacking replacement libglitz1 ...
dpkg: error processing /var/cache/apt/archives/libglitz1_0.5.5-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.so.1.0.0', which is also in package glitz-cvs
Preparing to replace libglitz-glx1 0.5.3-0ubuntu2 (using .../libglitz-glx1_0.5.5-0ubuntu2_amd64.deb) ...
Unpacking replacement libglitz-glx1 ...
dpkg: error processing /var/cache/apt/archives/libglitz-glx1_0.5.5-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz-glx.so.1.0.0', which is also in package glitz-cvs
Preparing to replace xserver-xgl 7.0.0-0ubuntu4 (using .../xserver-xgl_7.0.0-0ubuntu14_amd64.deb) ...
Unpacking replacement xserver-xgl ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/Xgl', which is also in package xorg-xgl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1_0.5.5-0ubuntu2_amd64.deb
 /var/cache/apt/archives/libglitz-glx1_0.5.5-0ubuntu2_amd64.deb
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
And I can't install compiz-gnome either (not sure if I need or have it?)```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz (= 0.0.9-0ubuntu3) but cvs20060218+opacityplugin-1 is to be installed
E: Broken packages

```

---

### Post by The_Major on 2006-04-24
Not sure if this would be of any use to anyone, but I found a way to use my tv card (pinnacle pctv rave) with xgl / compiz. 

I installed xawtv from the repo's, run it without xvideo extensions (run xawtv -noxv ) and set the capture option to grabdisplay and hey presto, I have tv with wobbly windows! :-D

---

### Post by MacSlow on 2006-04-24
Greetings everybody!

Not sure how closely everyone follows the CVS-commits and general releases of Xgl and compiz, but David just today added the first version of tweakable drop-shadows. [Take a look]("http://macslow.thepimp.net/?p=49").

Best regards...

MacSlow

---

### Post by gamma on 2006-04-25
Xilon I remember reading that you need a patch to get KDE's system tray working correctly with compiz. Sometimes when I used to log out of KDE the sound icon would be in the top left corner for a little while. Not sure what's going on here, and I no longer use KDE.

Does sudo apt-get remove libglitz-glx1 libglitz1 xserver-xgl then reapt-getting them do anything to get things working? Not sure about the last problem, are you using a 3rd party repository? If so what?

---

### Post by Xilon on 2006-04-25
Uhh I think that made it worse :P```
sebastian@Ubuntu:~$ sudo apt-get remove libglitz-glx1 libglitz1 xserver-xgl
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5616kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115382 files and directories currently installed.)
Removing xserver-xgl ...
Removing libglitz-glx1 ...
Removing libglitz1 ...
sebastian@Ubuntu:~$ sudo apt-get install libglitz-glx1 libglitz1 xserver-xgl Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1900kB of archives.
After unpacking 5222kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libglitz1 libglitz-glx1 xserver-xgl
Install these packages without verification [y/N]? y
Selecting previously deselected package libglitz1.
(Reading database ... 115361 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.5-0ubuntu2_amd64.deb) ...
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.5-0ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz-glx1_0.5.5-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz-glx.so.1.0.0', which is also in package glitz-cvs
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu14_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/Xgl', which is also in package xorg-xgl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz-glx1_0.5.5-0ubuntu2_amd64.deb
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have Reggaemanu's ([http://xgl.compiz.info/](http://xgl.compiz.info/)) repo enabled for the amd64 updates.

---

### Post by gamma on 2006-04-25
Xilon it looks like you've been switching between repositories without removing all the cruft :P.

sudo apt-get remove glitz-cvs xorg-xgl

then try reinstalling...

---

### Post by galo on 2006-04-25
Sorry but I've read as much as I could and sorry if this was already asked in this **FANTASTIC** thread, but I'm having problems with logout.

When I click logout, it's like my X crashed, but if I click in parts of the screen the computer reboots, shuts down, etc.. It's like the logout screen is there but it doesn't show up.

Anyone knows how to fix this ?

Using aiglx, i810, Intel 855GM.

---

### Post by Xilon on 2006-04-26
[QUOTE=gamma]Xilon it looks like you've been switching between repositories without removing all the cruft :P.

sudo apt-get remove glitz-cvs xorg-xgl

then try reinstalling...[/QUOTE]
```
sebastian@Ubuntu:~$ sudo apt-get remove glitz-cvs xorg-xgl
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  glitz-cvs xorg-xgl
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
Need to get 0B of archives.
After unpacking 6493kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115370 files and directories currently installed.)
Removing glitz-cvs ...
Removing xorg-xgl ...
sebastian@Ubuntu:~$ sudo apt-get install libglitz-glx1 libglitz1 xserver-xgl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xserver-xgl
The following packages will be upgraded:
  libglitz-glx1 libglitz1
2 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/1900kB of archives.
After unpacking 4854kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libglitz1 libglitz-glx1 xserver-xgl
Install these packages without verification [y/N]? y
(Reading database ... 115338 files and directories currently installed.)
Preparing to replace libglitz1 0.5.3-0ubuntu2 (using .../libglitz1_0.5.5-0ubuntu2_amd64.deb) ...
Unpacking replacement libglitz1 ...
Preparing to replace libglitz-glx1 0.5.3-0ubuntu2 (using .../libglitz-glx1_0.5.5-0ubuntu2_amd64.deb) ...
Unpacking replacement libglitz-glx1 ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu14_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sebastian@Ubuntu:~$ sudo apt-get install glitz-cvs xorg-xgl
Reading package lists... Done
Building dependency tree... Done
Package glitz-cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package glitz-cvs has no installation candidate

```Getting there :P I don't think that uninstalling xserver-xorg-core would be wise though :S

---

### Post by gamma on 2006-04-26
Xilon: haha you messed up your system baaad. Anyway.. do this

```
sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz
```

---

### Post by Xilon on 2006-04-26
Yes indeed I have, I just recovered from yet another X failure due to XGL being completely missing :P Oh well, at least I'm learning... I am after all a total linux newb :D```
sebastian@Ubuntu:~$ sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz
Adding `diversion of /usr/share/man/man1/Xserver.1x.gz to /usr/share/man/man1/Xserver.1x.gz.xgl by xserver-xorg-core'
sebastian@Ubuntu:~$ sudo apt-get install libglitz-glx1 libglitz1 xserver-xgl
Reading package lists... Done
Building dependency tree... Done
libglitz-glx1 is already the newest version.
libglitz1 is already the newest version.
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1784kB of archives.
After unpacking 4854kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xserver-xgl
Install these packages without verification [y/N]? y
(Reading database ... 117564 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu14_amd64.deb) ...
Setting up xserver-xgl (7.0.0-0ubuntu14) ...

sebastian@Ubuntu:~$ sudo apt-get install glitz-cvs xorg-xgl
Reading package lists... Done
Building dependency tree... Done
Package glitz-cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package glitz-cvs has no installation candidate

```More progress :P I'll try enabling the beerorkid repo and see if that works (I think it's the same as xgl.compiz.info)

btw. Thanks for all the help :)

Edit: Nope, glitz-cvs will not download.

---

### Post by RAOF on 2006-04-26
[QUOTE=Xilon]Yes indeed I have, I just recovered from yet another X failure due to XGL being completely missing :P Oh well, at least I'm learning... I am after all a total linux newb :D```
sebastian@Ubuntu:~$ sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz
Adding `diversion of /usr/share/man/man1/Xserver.1x.gz to /usr/share/man/man1/Xserver.1x.gz.xgl by xserver-xorg-core'
sebastian@Ubuntu:~$ sudo apt-get install libglitz-glx1 libglitz1 xserver-xgl
Reading package lists... Done
Building dependency tree... Done
libglitz-glx1 is already the newest version.
libglitz1 is already the newest version.
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1784kB of archives.
After unpacking 4854kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xserver-xgl
Install these packages without verification [y/N]? y
(Reading database ... 117564 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0-0ubuntu14_amd64.deb) ...
Setting up xserver-xgl (7.0.0-0ubuntu14) ...

sebastian@Ubuntu:~$ sudo apt-get install glitz-cvs xorg-xgl
Reading package lists... Done
Building dependency tree... Done
Package glitz-cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package glitz-cvs has no installation candidate

```More progress :P I'll try enabling the beerorkid repo and see if that works (I think it's the same as xgl.compiz.info)

btw. Thanks for all the help :)

Edit: Nope, glitz-cvs will not download.[/QUOTE]
You don't need glitz-cvs.  My Dapper64 has XGL working just fine without it.  Because it seems no-one wants to build amd64 packages, there are some more amd64 packages for compiz etc in my repository.  Which should now work ;)

---

### Post by gamma on 2006-04-26
Yea there is no glitz-cvs, just

sudo apt-get install compiz-vanilla-gnome xserver-xgl

---

### Post by martinbures on 2006-04-26
So I am having 2 issues.  One seems directly related to this thread.  The other is a reoccurance of an issue that I had with Breezy.

1.  <ALT><TAB> - switcher
Everything is installed and seems to be functioning properly(for the most part - and it rocks! thanks)  But this animal does not.  It comes up and functions properly with respect to choosing applications.  However, the only way to make it go away is to log out and log back in.

2.  When all of this stuff was first installed, my mouse and keyboard worked together properly - ex: I can hit <shift> on the keyboard and scroll with the mouse.  However, after an update, something changed, and now, as with Breezy, if I use my mouse, my keyboard does not function, and if I use my keyboard, my mouse does not function.

Any ideas on these two things?  What information can I provide to help with all of this?  

Thanks.
martin.

---

### Post by Xilon on 2006-04-26
[QUOTE=gamma]Yea there is no glitz-cvs, just

sudo apt-get install compiz-vanilla-gnome xserver-xgl[/QUOTE]
```
sebastian@Ubuntu:~$ sudo apt-get install compiz-vanilla-gnome xserver-xgl
Password:
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
The following extra packages will be installed:
  compiz-vanilla
Recommended packages:
  compiz-vanilla-kde
The following NEW packages will be installed:
  compiz-vanilla compiz-vanilla-gnome
0 upgraded, 2 newly installed, 0 to remove and 33 not upgraded.
Need to get 234kB of archives.
After unpacking 737kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-vanilla compiz-vanilla-gnome
Install these packages without verification [y/N]? y
Get:1 http://xgl.compiz.info dapper/main compiz-vanilla 0.0.9-0ubuntu3 [194kB]
Get:2 http://xgl.compiz.info dapper/main compiz-vanilla-gnome 0.0.9-0ubuntu3 [40.2kB]
Fetched 234kB in 28s (8305B/s)
Selecting previously deselected package compiz-vanilla.
(Reading database ... 117581 files and directories currently installed.)
Unpacking compiz-vanilla (from .../compiz-vanilla_0.0.9-0ubuntu3_amd64.deb) ...
Replacing files in old package compiz ...
Selecting previously deselected package compiz-vanilla-gnome.
Unpacking compiz-vanilla-gnome (from .../compiz-vanilla-gnome_0.0.9-0ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-vanilla-gnome_0.0.9-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/gnome-window-decorator', which is also in package compiz
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-vanilla-gnome_0.0.9-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sebastian@Ubuntu:~$ apt-cache search compiz-vanilla-gnome
compiz-vanilla-gnome - Gnome window decorator and libraries for Compiz

```Whoopty-doo 

What's vanilla for anyway?

---

### Post by islandman on 2006-04-26
Kde and Xgl on mepis !!! Put Windows in trash !!!! :D

---

### Post by Angry penguin on 2006-04-26
How do I make tansparency work? I have compiztools and transset plugin installed. Is there an option somewhere? Alt-scroll doesn't do anything.

EDIT: I may not have a new enough version of compiz, how do I figure out what version I have?

---

### Post by krusbjorn on 2006-04-27
[QUOTE=martinbures]1.  <ALT><TAB> - switcher
Everything is installed and seems to be functioning properly(for the most part - and it rocks! thanks)  But this animal does not.  It comes up and functions properly with respect to choosing applications.  However, the only way to make it go away is to log out and log back in.[/QUOTE]

Remove "Splash" from window_types in the fade plugin prefs.

---

### Post by gibbylinks on 2006-04-27
Hi Folks.

I have compiz working but, when I log in I'm left with a xgl window. Is there a way to stop this appearing, also I can't see the top or bottom of the cube when   I rotate screens, and since last update the water plugin has stopped working.

Any ideas

---

### Post by ruffneck on 2006-04-27
[QUOTE=galo]Sorry but I've read as much as I could and sorry if this was already asked in this **FANTASTIC** thread, but I'm having problems with logout.

When I click logout, it's like my X crashed, but if I click in parts of the screen the computer reboots, shuts down, etc.. It's like the logout screen is there but it doesn't show up.

Anyone knows how to fix this ?

Using aiglx, i810, Intel 855GM.[/QUOTE]

use the patched gnome-session provided by gandalf in this thread:

[http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)

---

### Post by muximus on 2006-04-29
i have an ati r9800 pro and athlon64 3000+

followed the instructions given above, but cant seem to get gdm working. all i get is a black n white screen n a busy icon. i got both xgl and compiz to work using startx and xterm, but if i start gnome-session frm there it is very slow. i also cant find compiz in gconf editor under apps. any clues??

---

### Post by Laterix on 2006-04-29
New Compiz packages compiz (0.0.10-0ubuntu2)  from QuinnStorm adds two new plugins. "bs" and "state". What are thay and how can I use them? I have added them to my plugin list, but only bs made gconf folder and there's nothing to configure.

Menus and tooltips are freaking wavy! :)

---

### Post by krusbjorn on 2006-04-29
[QUOTE=Laterix]New Compiz packages compiz (0.0.10-0ubuntu2)  from QuinnStorm adds two new plugins. "bs" and "state". What are thay and how can I use them? I have added them to my plugin list, but only bs made gconf folder and there's nothing to configure.

Menus and tooltips are freaking wavy! :)[/QUOTE]

I added state and bs right after gconf in the active plugins list and they work perfectly here.

State offers the ability to set transparency for certain window types. For example, add w:Unknown:85 to the list to make unknowns (menus, tooltips etc) 85% opaque.

bs lets you change the brightness of a window, like opacity_increase/decrease (in general->screen0->options) but for brightness. Default should be shift+mouse wheel.

To change how the menus and tooltips wobble, change the map_friction and map_spring_k in apps->compiz->plugins->wobbly->screen0->options.

---

### Post by Laterix on 2006-04-29
Thank you. This was very helpfull! But I can't find any list where I could add this w:Unknown:85, but it doesn't matter. I like it this way.

I really can't think of any usful meaning for BS plugin. Why would I want to make some windows darker?

---

### Post by Viriiguy on 2006-04-30
Ok well I have had XGL and Compiz running GREAT on my M6805 laptop. (ATI Radeon 9600 pro) But I had not booted linux for the last week, and decided to power it up and update it, as I usually do everyday. After the update it required a reboot. Well that was the last time my setup worked.

After the reboot I could not get it to boot to GDM. I fumbled around and managed to remove and reinstall Xorg today and that seemed to almost fix it. I can now get the GDM up, and log into my Gnome session, but compiz seems to not be working. None of my windows have title bars, and cannot be moved.

Any ideas what I should do?

Oh yea I have the thefuture2 script, and if I try to run it I get...

/usr/bin/thefuture2: line 1: !/bin/bash: No such file or directory
viriiguy@DeepThought:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension

One more thing, the login screen for gdm will not show unless I switch consoles first, then switch back with ctrl+alt+f7

---

### Post by Laterix on 2006-04-30
[QUOTE=Viriiguy]
I can now get the GDM up, and log into my Gnome session, but compiz seems to not be working. None of my windows have title bars, and cannot be moved.

Any ideas what I should do?
[/QUOTE]
Try this. Press ALT+F2 and run "gnome-window-decorator".

---

### Post by Viriiguy on 2006-04-30
When I try to run gnome-window-decorator I get...
gnome-window-decorator, failed to load shadow images.

Did the updates in the last week have a new version of XGL and compiz? 
And if so is there anyway to roll back to say a week ago? :)

---

### Post by flankker on 2006-05-01
hi i got this working in 10 minutes, using the radeon driver with my mobility radeon 9000 igp.

i get the wobly effect, opacity, and window switching effects and all the rest seem to be installed. but how do i activate them? i want to try the water, rain, spinning cube and the rest of the effects. thanx :)

**EDIT** i figured it out

---

### Post by veratyr on 2006-05-03
Just updated today and my gnome-window-decorator stopped working. Also has anyone ever had their home directory be viewable at the GDM when the user isn't even logged in yet? Kind of a big security issue.

---

### Post by Paool on 2006-05-03
[QUOTE=veratyr]Just updated today and my gnome-window-decorator stopped working.[/QUOTE]
I've got the same problem... :(

---

### Post by sublime on 2006-05-03
check out the bugs section on teh compiz forum.  there was a mew mesa release but there isnt a compiz out that can use it.  you can either downgrade or just wait till a new compiz is released.  to use gnome normally open a terminal and type metacity

---

### Post by veratyr on 2006-05-03
I just removed "thefuture" from starting with gnome for now. I'll just wait till the new compiz comes out. I'm sure it won't take long.

---

### Post by soulglo83 on 2006-05-03
[QUOTE=sublime]check out the bugs section on teh compiz forum.  there was a mew mesa release but there isnt a compiz out that can use it.  you can either downgrade or just wait till a new compiz is released.  to use gnome normally open a terminal and type metacity[/QUOTE]

fixed,
add the following if they arent already in your /etc/apt/sources.list
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

sudo apt-get update 
sudo apt-get dist-upgrade

compiz updates, run the script of your choice (most are familiar with thefuture) and compiz should load without barking about GLXFBConfig or whatever

---

### Post by sublime on 2006-05-03
theres a new compiz in the updates.  just added it within the last couple hours.

---

### Post by yawie on 2006-05-04
Like others, I updated two hours ago with this rep :
deb [http://xgl.compiz.info](http://xgl.compiz.info) dapper main

compiz would not work anymore (sounds like the mesa/compiz compatibility plugin, I got a white screen. Changing workspace with the cube was still working).

I added Quinn's repository, upgraded again
Compiz works again now but I have only one workspace :confused: 
Any of you have an idea ?

(nvidia with binary drivers, dapper up to date, no plf rep, kernel 2.6.15.21 K7)

Thanks :)

---

### Post by soulglo83 on 2006-05-04
[QUOTE=yawie]Like others, I updated two hours ago with this rep :
deb [http://xgl.compiz.info](http://xgl.compiz.info) dapper main

compiz would not work anymore (sounds like the mesa/compiz compatibility plugin, I got a white screen. Changing workspace with the cube was still working).

I added Quinn's repository, upgraded again
Compiz works again now but I have only one workspace :confused: 
Any of you have an idea ?

(nvidia with binary drivers, dapper up to date, no plf rep, kernel 2.6.15.21 K7)

Thanks :)[/QUOTE]
download gset-compiz
run gset-compiz, and tweak the "number of viewports" which is an option on the first page of gset-compiz.  you can have more than 4 virtual desktops if u choose!

---

### Post by yawie on 2006-05-04
Thanks for the reply, I DL it but the number of viewport was already 4. I tried to change but nothing more happen. It was working with yesterday's apt-get update.

---

### Post by Dambrosio on 2006-05-04
Let's start out by saying that I'm an extreme Noob when it comes to ubuntu and dapper, ok... So I was wondering if I wanted to install XGL and Compiz on my machine that i'm going to build for college would I want one 256 graphics card or 2x 128 graphics card (SLI) im new to SLI also. Also, is having a dual core 64 processer a advantage with XGL and Compiz?

---

### Post by g14 on 2006-05-04
[QUOTE=Dambrosio]Let's start out by saying that I'm an extreme Noob when it comes to ubuntu and dapper, ok... So I was wondering if I wanted to install XGL and Compiz on my machine that i'm going to build for college would I want one 256 graphics card or 2x 128 graphics card (SLI) im new to SLI also. Also, is having a dual core 64 processer a advantage with XGL and Compiz?[/QUOTE]
I actually would suggest against SLI as it would be much more of a pain to configure X.org and I don't think compiz supports it.

I run Xgl/compiz *perfectly* and smoothly on a 1.3GHZ AMD Athlon with 4GB of ram. Your AMD64 will blow this machine out of the water. For a video card, get an nvidia Geforce FX greater than or equal to a 5200. It will run perfectly on that. Also, most of the users are on 32 bit machines so it might take a little bit longer for you to get the right packages for a 64 bit machine.

I suggest you ask this question on the compiz forum located at:
[http://www.compiz.net]("http://www.compiz.net")

---

### Post by nhidog on 2006-05-05
Hi,

I finally managed to get XGL working but I have a few problems.

1. Applications are very slow to open.
2. Resizing windows is ridiculously slow.

I am currently on Thinkpad T60 with ATI  X1300 GFX.  If anyone has solved these problems with similiar card, could I get your xorg.conf file?

Thanks,
Nhi

---

### Post by krusbjorn on 2006-05-05
@nhidog

Window resizing is slow for everyone, and I dont think there is a fix for it yet. The amount of time it takes to load the different applications shouldnt be noticably affected by xgl/compiz though.

---

### Post by nhidog on 2006-05-05
@krusbjorn

Ah good to know I'm not alone, I think opening application is slow due to window resizing.  I can see application opening slow as it resizes the window, hehe.

Thanks,
Nhi

---

### Post by krusbjorn on 2006-05-05
[QUOTE=nhidog]@krusbjorn

Ah good to know I'm not alone, I think opening application is slow due to window resizing.  I can see application opening slow as it resizes the window, hehe.

Thanks,
Nhi[/QUOTE]

I think what you are referring to is the "minimize" plugin. It makes windows "zoom in/out" when opened/closed. You can change the options for the minimize plugin in gconf-editor (apps-compiz-plugins-minimize-screen0-options) or disable it completely in apps-compiz-general-allscreens-options, by removing it from the active plugins list.

---

### Post by nhidog on 2006-05-05
Tried removing minimize from active plugins but it didn't help.  Application still open super slow.  I can actually see the application gradually open via the blue outline.  Oh wells, XGL/compiz still rocks.  I have fun playing with it.  I'll just wait for a fix to be put out.

Nhi

---

### Post by Laterix on 2006-05-05
[QUOTE=krusbjorn]@nhidog
Window resizing is slow for everyone, and I dont think there is a fix for it yet.[/QUOTE]
Not true. My window resize is just as fast as without compiz. I have Nvidia 6600GT.

---

### Post by krusbjorn on 2006-05-05
[QUOTE=Laterix]Not true. My window resize is just as fast as without compiz. I have Nvidia 6600GT.[/QUOTE]
Strange. I have an nvidia 6200 and resizing is very jerky. I dont remember if resizing was as bad with xorg/metacity though. Anyways, lots of people have this problem and I have yet to see a fix for it.

[http://compiz.net/viewtopic.php?id=342](http://compiz.net/viewtopic.php?id=342)
[http://compiz.net/viewtopic.php?id=488](http://compiz.net/viewtopic.php?id=488)

---

### Post by jon_z on 2006-05-06
Fresh Dapper 6.06 beta 2 i386
ATI 9600 XT set up correctly with fglrx
AMD64 processor

what is the best method to install Xgl and Compiz on Gnome?  I've tried a few of the methods and some are shaky.  I want the most up to date version of compiz as well.  Thx a much.

---

### Post by thekidder on 2006-05-07
I've tried to get Xgl working on my Mobility x300 mostly by following this guide: [http://lems.kiskeyix.org/puntoyaparte/article.php?story_id=58](http://lems.kiskeyix.org/puntoyaparte/article.php?story_id=58). I stop GNOME and then execute the script and I get the error: Server is already active for display 1. If I switch to tty7 I still see the 'waiting' cursor. Any suggestions?

---

### Post by Xilon on 2006-05-10
[QUOTE=Horizon]If you're using Gnome, System>Preferences>Keyboard>Layout Options>Alt/Win Key Behaviour
and then select "Meta is mapped to the Win-keys" 
I really have no idea where it would be in the KDE menus, only ever used it once with knoppix.[/QUOTE]
For some reason I don't have those options in my layout options... I used to, I remember that... but I don't anymore. any ideas on how to get them back?

[IMG]http://img232.imageshack.us/img232/6532/screenshotkeyboardpreferences7.png[/IMG]

---

### Post by ketsugi on 2006-05-10
I know the wiki says there's currently no way to change the window border theme, but I'm wondering if this is something that's being worked on?

Also, I find myself unable to watch videos in Mplayer and VLC now. Once I open a video file, CPU use shoots up to 100% and the video is too choppy to watch.

Finally, XGL/Compiz looks great, it really does. But I don't really need all these effects and stuff. I just want my regular window manager to run faster. Is there a way to get Gnome to use hardware acceleration, but... stay Gnome? Without Compiz?

---

### Post by cleatus on 2006-05-10
Ok I got it installed and working thanks for the tutorial... but how do you get the effect of a 3-d cube to work. Are there instructions on how you get things working after finally getting it running?

---

### Post by RAOF on 2006-05-10
[QUOTE=ketsugi]...
Also, I find myself unable to watch videos in Mplayer and VLC now. Once I open a video file, CPU use shoots up to 100% and the video is too choppy to watch.

Finally, XGL/Compiz looks great, it really does. But I don't really need all these effects and stuff. I just want my regular window manager to run faster. Is there a way to get Gnome to use hardware acceleration, but... stay Gnome? Without Compiz?[/QUOTE]
1) For mplayer playback, I find that selecting "-vo gl2:yuv=4" (from the command line) gives excellent playback speed for me.  From the gui you'd be after Preferences->Video and select the "GL2" video output driver.  There's probably a similar option for VLC, somewhere.  And for totem, you can set the default video sink to be "glimagesink".

2) You could just use xcompmgr to get compositing with the normal Metacity - check out Poofy's guides (the Knome guide and the Composite manager guide) under the Breezy/HowTo forum.  They'll still apply to Dapper.

---

### Post by ketsugi on 2006-05-11
Thanks; xcompmgr is just what I needed.

---

### Post by Xilon on 2006-05-11
I've run into a bit of a pickle here...
After installing XGL and Compiz from scratch (Quinn's repo) I get a few errors that plugins are not loading.
```
$ compiz --replace gconf
$ compiz.real: Couldn't load plugin 'libminiwin.so'
compiz.real: Couldn't load plugin 'libtransset.so'
compiz.real: Couldn't load plugin 'libstate.so'
compiz.real: Couldn't load plugin 'libcube.so'
compiz.real: 'rotate' plugin must be loaded after 'cube' plugin
compiz.real: Can't activate 'rotate' plugin due to dependency problems
compiz.real: 'zoom' plugin must be loaded after 'cube' plugin
compiz.real: Can't activate 'zoom' plugin due to dependency problems
compiz.real: Couldn't load plugin 'libtrailfocus.so'
compiz.real: Couldn't load plugin 'libbs.so'
compiz.real: Couldn't load plugin 'libdock.so'
```
Now when I locate these plugins they seem to be in the correct place
```
$ locate libtransset
/usr/lib/compiz/libtransset.so
$ locate libstate
/usr/lib/compiz/libstate.so
$ locate libcube
/usr/lib/compiz/libcube.so
$ locate libtrailfocus
/usr/lib/compiz/libtrailfocus.so
$ locate libbs
/usr/lib/compiz/libbs.so
/usr/lib/libbsd-compat.a
$ locate libdock
/usr/lib/compiz/libdock.so
```This confuses me a bit... and I really have no idea how to fix this :S Is there something I should configure for Compiz to look in the correct directory or something? It reads to other plugins (like transset, resize, move, fade, wobbly, minimize, scale, water...) just fine and it works great. I really miss the cude :( Having miniwin/dock running would also be really great

---

### Post by Belathor on 2006-05-11
Hi Xilon,

I have no idea about your last post, but as to your keyboard problems, I had a similar problem. In addition, however, I was having trouble with my caps lock key. I was able to fix it by taking out the -kb from gdm.config-custom file from Quinns howto. I hope that works for you...

---

### Post by rplantz on 2006-05-11
I was successful installing XGL and Compiz, but it cost me the use of Keyboard Indicator. Since I like to be able to enter characters in other languages, e.g., ã, I went back to the standard Ubuntu set up.

But this made me curious. I don't have a good understanding of xservers and window managers. What are the ones used by Ubuntu? Can I get a speedup with my nvidia FX5200-128 by using XGL without Compiz? (I am using nvidia-glx.) Etc., etc.

Can anybody point me to some good discussions on these issues? I've looked around, but so far nothing is coming up in my search.

---

### Post by Xilon on 2006-05-11
Not sure about any discussions but you could try xcompmgr. There is a tutorial somewhere around here... basically it will do window acceleration so it might speed up the default window manager without having to try XGL / Compiz which might actually slow it down due to all the fancy effects.

By default ubuntu uses the standard X11 Xorg xserver (not sure what it's called exactly) and Gnome uses Metacity as it's composite manager (or rather window decorations, I don't think it's a composite manager... I'm new to this myself ;) ). Xgl is an alternative to Xorg and it runs on OpenGL so I'm not sure if that will speed up anything.

> I have no idea about your last post, but as to your keyboard problems, I had a similar problem. In addition, however, I was having trouble with my caps lock key. I was able to fix it by taking out the -kb from gdm.config-custom file from Quinns howto. I hope that works for you...Thanks, I'll try that when I restart. I also seem to be missing the numerioc functionality of the num pad, which seems to be a bit ironic. Even with the numlock turned on (it's turned off by default although I use the numlockx method to keep it on). I don't think I have any other problems apart from all the keyboard layouts bing gone and not being able to write foreign characters but that doesn't bug me as much. I remember that there was a solution by linking one directory to another where the keyboard layouts were held but I can't find it anymore :(

Edit: Nope, removing -kd did not solve the numpad problem.

---

### Post by dmacdonald111 on 2006-05-12
Hi, I've managed to work my way through the installation, and I can load up okay, but then I always end up with a hard lock. I saw the post about hard locks with ati cards and inserting 'aglock' etc, in xorg.conf which I have done, but I still end up with the same locking. Any ideas or direction you can point me in? Thanks

---

### Post by FedeXX on 2006-05-13
***solved by myself :P ***

---

### Post by miggl on 2006-05-13
[QUOTE=FedeXX]***solved by myself :P ***[/QUOTE]

Please share how you fixed it, even if it is really simple. This helps others who have the same (or similar) problem.

Thanks! :)

---

### Post by zisper on 2006-05-13
Hi;
     I've just been playing around with the Kororaa LiveCD (XGL livecd based on Gentoo) and the whole XGL thing is very cool - runs fine on my machine and the processor overhead seems very small, and I don't have the newest hardware (P4 1.7Ghz, GeForce3 Ti 500 64Mb, 1Gb Memory).  People should give it a whirl if they don't want to mess up their ubuntu installation.
     That brings me to my question:  Anybody know how far away from being able to just tick the box in synaptic and have an xgl based desktop?  I doubt it'll make it into the official dapper final release, but will it be in the backports before too long?  (I'm pretty new to ubuntu - once dapper stable is out, any new software versions come through the backporting efforts right?)
     I don't _mind_ setting stuff up myself, but the reason I switched to ubuntu (from gentoo) is that I wanted a low maintenance system.  Installing XGL by hand at the minute seems pretty high maintenance. ;)

---

### Post by bihe on 2006-05-14
thx - nice howto - just works

---

### Post by veratyr on 2006-05-14
Quick question regarding videos and xgl. I've been using mplayer mostly since I started using xgl. Is it possible to get rid of the vertical tearing in videos? I know I've seen it mentioned before but wasn't sure if there was a solution to it.

---

### Post by nverenin on 2006-05-14
[QUOTE=dmacdonald111]Hi, I've managed to work my way through the installation, and I can load up okay, but then I always end up with a hard lock. I saw the post about hard locks with ati cards and inserting 'aglock' etc, in xorg.conf which I have done, but I still end up with the same locking. Any ideas or direction you can point me in? Thanks[/QUOTE]

The option is called "agplock" not "aglock"; I made the same mistake from someone's howto where they misspelled the option.

At least for me, this is the only option I had to add to my xorg.conf on that particular system  to get rid of the lockups with xgl (x700pro pcie):

```

Option      "KernelModuleParm" "agplock=0"

```

---

### Post by crhylove on 2006-05-16
Same question as zisper...... I'm about out of ideas, and I LOVED the kororaa live CD.  I want XGL!!!

rhY

---

### Post by pau on 2006-05-16
Hi all there,

Everybody's talking about nvdia and radeon but my
Fujitsu-Siemens Lifebook P7010 has an Intel 855GME... and I don't know which driver should I use in the xorg.conf file... Any hint??

The kororaa live cd with xgl worked well (almost, playing movies would stop X)

Thanks,

Pau

---

### Post by dengar on 2006-05-18
edit: someone delete this reply, I made a mistake

---

### Post by commodore on 2006-05-18
My shortcut keys don't work :( Only Alt+Control+Left Click. I don't know what's wrong. I don't have anything to say. All my keys work in other applications.

---

### Post by Bazon on 2006-05-19
There is another thread to be ruled by this one:

 	
[HOWTO: Separate Xgl/Compiz Session](http://ubuntuforums.org/showthread.php?t=174233)

in contrast to other Howtos, it describes how to run xgl as a seperate x-session, so you can start a Xorg session without problems, too.

That's nice because not all things will work in a XGL-session (3-D games, fullscreen video...)

---

### Post by commodore on 2006-05-19
I don't know why the keys didn't work, but as I started Compiz today, everything worked perfectly.

---

### Post by florizs on 2006-05-20
does anybody know which plugin makes the windows in the background have a black shadow overlay?
Everytime I focus on a window the rest of my windows in the background go black-ish and almost unreadable.
I have been searching in the compiz settings but I cant find how to turn of that functionality.

does anybody know?
thanks in advance

p.s. I have attached a screenshot showing what I mean.

---

### Post by aoanla on 2006-05-20
[QUOTE=florizs]does anybody know which plugin makes the windows in the background have a black shadow overlay?
Everytime I focus on a window the rest of my windows in the background go black-ish and almost unreadable.
I have been searching in the compiz settings but I cant find how to turn of that functionality.

does anybody know?
thanks in advance

p.s. I have attached a screenshot showing what I mean.[/QUOTE]

That screenshot looks just like the windows are going /transparent/ when they lose focus. I believe that property is controlled by the trailfocus plugin, which is configurable.

---

### Post by Bazon on 2006-05-20
[QUOTE=florizs]does anybody know which plugin makes the windows in the background have a black shadow overlay?[/QUOTE]
It's a relativly new feature of the **decoration plugin** in Quinn's Compiz packages.

You can adjust colorof the shadow, radius, opacity and offest.
Really nice. :)

---

### Post by adamvert on 2006-05-21
[QUOTE=florizs]does anybody know which plugin makes the windows in the background have a black shadow overlay?
Everytime I focus on a window the rest of my windows in the background go black-ish and almost unreadable.
I have been searching in the compiz settings but I cant find how to turn of that functionality.

does anybody know?
thanks in advance[/QUOTE]

As I just realised, it's the trailfocus plugin - if you go to /apps/compiz/plugins/trailfocus/screen0/options in gconf-editor and set the minimum_window_brightness_level, minimum_window_saturation_level and minimum_window_opacity_level to be the same as the repective maximum levels, you won't have this happening anymore.  

It's a real pain when you're trying to adjust brightness levels in Gimp and the image you're working on keeps blacking out whenever you touch the brightness knob...

Adam

---

### Post by richbarna on 2006-05-21
whhhhoooooooaaaaaa !!!
3D Rotating multi-desktops,
Floppy wobbly transparent windows and menus.
This is cooool !!!
Just showed it to my windows using friends and they were open mouthed.....
I mean, their jaws just dropped !!!!!
We need more of this type of stuff !!
Guess who have just asked me to install Ubuntu on their computers ???

The guide was excellent by the way, Top notch.
I had a few teething problems (my fault),
But now everything is cool.

---

### Post by crhylove on 2006-05-22
I'm still having teething problems, but I DID get it up and running.  Now however, my desktop is always stuck at one workspace, so I can't use the cube feature at all, which is really a bummer...  Still working on it.

rhY

---

### Post by gamma on 2006-05-22
I was/still am considering jumping ship from a Windows-based computer (running only Linux) after owning my Dell Inspiron 5150 for 4 years and buying a Mac (and dual booting). The MacBook was just released and I read reviews of that and the MacBook Pro and see the same stuff. It makes whine/moo noises, runs idle at 70-80C due to incorrectly applied thermal paste (according to people) although sites show smaller cores should have a lot of thermal paste, but anyway... Initially I thought I'd switch to the smaller Mac laptop when it switched to Intel, but not with these problems.

Luckily compiz with its wobbly windows, scale and fade plugins will keep me using this bulky outdated laptop I have now. Some day I'll buy a nice new small laptop. ;)

---

### Post by Eric_T on 2006-05-22
Does anyone know how to remove the "dock" plugin? I don't find it in my startup script... It causes a lot of problems, my gdesklets and panels are showing on it, and I use the scale plugin more anyways. [SOLVED, just had to remove the dock plugin from the plugin list in gconf-editor...]

Also, my Super key and left mouse button aren't working, so I can't zoom or resize windows. Anyone got any ideas on how to fix that? The zoom feature is very useful for image editing.
[SOLVED, again, just an edit in gconf-editor... note to self: think before posting...:P ]

---

### Post by apejcic on 2006-05-22
[QUOTE=Eric_T]Does anyone know how to remove the "dock" plugin? I don't find it in my startup script... It causes a lot of problems, my gdesklets and panels are showing on it, and I use the scale plugin more anyways. [SOLVED, just had to remove the dock plugin from the plugin list in gconf-editor...]

Also, my Super key and left mouse button aren't working, so I can't zoom or resize windows. Anyone got any ideas on how to fix that? The zoom feature is very useful for image editing.[/QUOTE]

try this: xmodmap /usr/share/xmodmap/xmodmap.<language>

PLEASE READ BELOW, AND WATCH THE MOVIE, thx :)

Another question: Does anyone know what applet (the one in bottom left, that says computer) is the guy in the video using [http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/) -> Desktop Organization (sorry cant direct link, cuz they use javascript)... looks like something ms vista like

edit found direct link, stupid me: [http://cache.novell.com/cached/xglrelease/desktoporg.ogg](http://cache.novell.com/cached/xglrelease/desktoporg.ogg) (5.7MB)

---

### Post by Symbios on 2006-05-22
I can't seem to change the window transparency ammount. When I do the "Ctrl+Shift+Scroll Wheel" thing,  nothing happens. 

Am I doing something wrong here?

---

### Post by panurge77 on 2006-05-22
Transparency is set at alt-wheel (only alt) :)

---

### Post by panurge77 on 2006-05-22
[QUOTE=apejcic]Another question: Does anyone know what applet (the one in bottom left, that says computer) is the guy in the video [http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/) -> Desktop Organization (sorry cant direct link, cuz they use javascript)... looks like something ms vista like[/QUOTE]

That's probably beagle in a customized gui

---

### Post by panurge77 on 2006-05-22
[QUOTE=crhylove]I'm still having teething problems, but I DID get it up and running.  Now however, my desktop is always stuck at one workspace, so I can't use the cube feature at all, which is really a bummer...  Still working on it.

rhY[/QUOTE]

You're probably missing libsvg, on which the cube depends

---

### Post by mattoman on 2006-05-22
I am running ubuntu on a 27'' widescreen at 1360x768  compiz won't seem to run at this resolution, an ideas? Thanks!

---

### Post by Symbios on 2006-05-23
[QUOTE=panurge77]Transparency is set at alt-wheel (only alt) :)[/QUOTE]


D'oh! I thought I read somewhere that it was Shift+Ctrl+Wheel. 
Unfortunatly Alt+Wheel doesn't do anything either...

---

### Post by Bazon on 2006-05-23
BTW:
Did you know there exist at least 4 different methods to start Xgl?
I started a thread to compare these methods, if you're interessted:
[http://ubuntuforums.org/showthread.php?t=180545](http://ubuntuforums.org/showthread.php?t=180545)
You can also vote your favourit method there. :wink:

---

### Post by yawie on 2006-05-23
[QUOTE=crhylove]I'm still having teething problems, but I DID get it up and running.  Now however, my desktop is always stuck at one workspace, so I can't use the cube feature at all, which is really a bummer...  Still working on it.

rhY[/QUOTE]
Everything and one apt-get upgrade gave me this behaviour as well. If you find the solution please post it here :)

---

### Post by apejcic on 2006-05-23
[QUOTE=panurge77]That's probably beagle in a customized gui[/QUOTE]

well maybe im crazy, but... the menu has something like windows start button, favourite apps, search for files, quick run, .... It look way to cool for me not to have it.

Any hints on where to find this applet would be nice :), thx

---

### Post by panurge77 on 2006-05-23
Yes. I paused the video now to see it better and it does really look like windows start menu. If that's from novell, maybe it's in the new suse. Try asking on suse forums...

---

### Post by ba5e on 2006-05-23
I have been using xgl for a while now, and love it, but having just a PIII 733 with 256MB ram takes its toll.

I have had to uninstall it now :-|, as using just the opengl xserver killed my speed in almost everything I was doing ](*,) . but one day :-k  (with a fater pc maybe) I will jump back into the coolest thing I have seen in linux for a while...... till then happy compositing everyone !! :)

---

### Post by apejcic on 2006-05-23
[QUOTE=panurge77]Yes. I paused the video now to see it better and it does really look like windows start menu. If that's from novell, maybe it's in the new suse. Try asking on suse forums...[/QUOTE]

you are right, it's novell code, but they haven't released it (yet)
more at: [http://www.jonobacon.org/viewcomments.php?id=637](http://www.jonobacon.org/viewcomments.php?id=637)

---

### Post by panurge77 on 2006-05-23
[QUOTE=apejcic]you are right, it's novell code, but they haven't released it (yet)
more at: [http://www.jonobacon.org/viewcomments.php?id=637](http://www.jonobacon.org/viewcomments.php?id=637)[/QUOTE]

Hmm. Looks like my first hint about beagle was not all wrong. That novell menu is dependent on beagle and it'll probably be release but I doubt gnome will adopt it (at least in the near future). Theres a big discussion around here:

[http://mail.gnome.org/archives/desktop-devel-list/2006-February/msg00115.html](http://mail.gnome.org/archives/desktop-devel-list/2006-February/msg00115.html)

Actually, its a HUGE discussion, and there are some real angry folks... I'm getting interested :)

---

### Post by varl on 2006-05-23
Today when I was told to update my compiz was upgraded.

Now XGL doesn't start.

I only get the error:
```

varland@varland[~] $ thefuture
varland@varland[~] $ slw: 0     srw: 0  sth: 0  sbh: 24

```
And I have no idea what to do.
Has someone else experienced this after updating?

---

### Post by panurge77 on 2006-05-23
[QUOTE=varl]Today when I was told to update my compiz was upgraded.

Now XGL doesn't start.

I only get the error:
```

varland@varland[~] $ thefuture
varland@varland[~] $ slw: 0     srw: 0  sth: 0  sbh: 24

```
And I have no idea what to do.
Has someone else experienced this after updating?[/QUOTE]

From what I read at compiz forums, there was only ONE user who survived this update. You can watch there for a fix... (should be out soon)

[http://compiz.net/index.php](http://compiz.net/index.php)

(Or just go back to your previous compiz)

---

### Post by varl on 2006-05-23
[QUOTE=panurge77]From what I read at compiz forums, there was only ONE user who survived this update. You can watch there for a fix... (should be out soon)

[http://compiz.net/index.php](http://compiz.net/index.php)

(Or just go back to your previous compiz)[/QUOTE]
Thanks alot. :)

---

### Post by ninja_indiano on 2006-05-23
[QUOTE=panurge77]From what I read at compiz forums, there was only ONE user who survived this update. You can watch there for a fix... (should be out soon)

[http://compiz.net/index.php](http://compiz.net/index.php)

(Or just go back to your previous compiz)[/QUOTE]


Having the same problem...where did you read that only one user survived the update?

Can't find it on de compiz.net

Sorry...

Found it...however can't delete this post...

---

### Post by Belathor on 2006-05-23
Where did you see the error message? My XGL isn't working either but I haven't seen the error message, all I see is that I have no orange bar above my open applications and I can't switch desktops.

---

### Post by ninja_indiano on 2006-05-23
[QUOTE=Belathor]Where did you see the error message? My XGL isn't working either but I haven't seen the error message, all I see is that I have no orange bar above my open applications and I can't switch desktops.[/QUOTE]

Go to a shell and run the script theFuture(the name of the script changes depending on which tutorial you followed)

---

### Post by varl on 2006-05-23
[QUOTE=Belathor]Where did you see the error message? My XGL isn't working either but I haven't seen the error message, all I see is that I have no orange bar above my open applications and I can't switch desktops.[/QUOTE]
It came up when I ran thefuture from a console.

---

### Post by apejcic on 2006-05-23
[QUOTE=panurge77]From what I read at compiz forums, there was only ONE user who survived this update. You can watch there for a fix... (should be out soon)

[http://compiz.net/index.php](http://compiz.net/index.php)

(Or just go back to your previous compiz)[/QUOTE]

no he was just using old mesa libs... but that is not the trick

---

### Post by panurge77 on 2006-05-23
For those with broken compiz:

[http://compiz.net/viewtopic.php?id=949&p=4](http://compiz.net/viewtopic.php?id=949&p=4)

---

### Post by Belathor on 2006-05-23
> For those with broken compiz:

[http://compiz.net/viewtopic.php?id=949&p=4](http://compiz.net/viewtopic.php?id=949&p=4)

I downloaded the patch... what do I do with it?

---

### Post by panurge77 on 2006-05-23
[QUOTE=Belathor]I downloaded the patch... what do I do with it?[/QUOTE]

Actually the problem was within that patch. It's a patch for those running Xinerama and Quinn adopted it on her (his?) debs. It would break those systems not using Xinerama. You downloaded the fixed patch, but I don't know how to apply it. The manual fix is described on the previous page:
[http://compiz.net/viewtopic.php?id=949&p=3](http://compiz.net/viewtopic.php?id=949&p=3)

in src/screen.c at line 2365, after the fprintf add:

if(!h)
**break;

(where those ** means two blank spaces: the forum engine is erasing them when I post)

So you can either find ou how to apply that patch or try adding these two lines. I'm using amd64 debs, which are already fixed.

---

### Post by Hermanjr on 2006-05-24
[QUOTE=Belathor]Where did you see the error message? My XGL isn't working either but I haven't seen the error message, all I see is that I have no orange bar above my open applications and I can't switch desktops.[/QUOTE]

I have this exact same problem since I updated earlier today. Anyone know what causes this behaviour? I fired up firefox and keyboard input is extremly slow too. 

Argh! I had this working so nicely too. ](*,)

---

### Post by sublime on 2006-05-24
for those that cant get the new compiz working try this until quinnstorm can get a fixed package out.  hopefully she will.  all its doing is downgrading to the previous working version.
```

sudo dpkg -i /var/cache/apt/archives/compiz-gnome_0.0.10-0ubuntu14_i386.deb
sudo dpkg -i /var/cache/apt/archives/compiz_0.0.10-0ubuntu14_i386.deb

```

---

### Post by sublime on 2006-05-24
nevermind, a new compiz package has just been released to the repos.  works just fine for me.

---

### Post by sanone on 2006-05-24
[QUOTE=sublime]for those that cant get the new compiz working try this until quinnstorm can get a fixed package out.  hopefully she will.  all its doing is downgrading to the previous working version.
```

sudo dpkg -i /var/cache/apt/archives/compiz-gnome_0.0.10-0ubuntu14_i386.deb
sudo dpkg -i /var/cache/apt/archives/compiz_0.0.10-0ubuntu14_i386.deb

```[/QUOTE]

Thanks for sharing. But I'm not sure if I should apply these patches. When the fixed version is in the repo can I upgrade? How will that work? Will it override the current version or install a new version along with the version installed through the repo?

I'm new to the debian/ubuntu scene and I have some bad experiences with linux and manual patching so I'm a bit scared. 

**Another problem:**
I have another weird issue. When I start downloading I leave the PC on and go away. Sometimes when I come home I see the login screen in a low res version (1024x168 instead of 1280x1024). I'm not sure what happens because I'm simply not there when it occurs. One time I still had nautilus _in front_ of the login screen. I have totaly no clue why this occurs. 

The problems above are the only ones I have with XGL and apart from not doing anything right now it works like a charm! ;) 

Cheers,
San

---

### Post by sanone on 2006-05-24
[QUOTE=sublime]nevermind, a new compiz package has just been released to the repos. works just fine for me.[/QUOTE]
Same here... phew!

---

### Post by reclusivemonkey on 2006-05-25
Hello Everyone,

Longtime linux user (Slackware for about five years), new Ubuntu user. I am also having the odd (somewhat trivial) issue with XGL. I followed the instructions here ([http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)), and I added the extra repositories as instructed here ([http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)). On my windows, I have "On Top" greyed out, and can't zoom/set transparency. I notice a few people have mentioned that they have picked up a new compiz today, but I don't seem to have this myself.  I have a NVidia FX 5200 with the ubuntu nvidia drivers installed, and I followed the instructions at the begining of this thread to get XGL/compiz working. Currently I have compiz version 0.0.2-4ubuntu2 installed, in my sources.list I have;
```

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

```
I've searched the forums for a couple of days now and I am a bit lost with the sheer amount of information available on XGL. So really, I am asking;

1. Do I need to add a different repository to my list to pick up the latest compiz that will fix my issues?
2. Or can anyone point me to a thread which will allow me to get transparency/zoom and "On Top" back?

I would be very grateful if anyone could point me in the right direction. Thanks.

---

### Post by panurge77 on 2006-05-25
check [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) for the repository with latest xgl/compiz debs

---

### Post by reclusivemonkey on 2006-05-25
[QUOTE=panurge77]check [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) for the repository with latest xgl/compiz debs[/QUOTE]

Thanks panurge, that link was very helpful. Everything is working bar "On Top" now, but I am sure that just on the to do list... ;)

---

### Post by denjin on 2006-05-25
For some reason gdm isn't starting Xgl properly. I've followed the instructions properly and edited gdm.conf and gdm.conf-custom (ATi x600).  If I paste the Xgl line that is in gdm.conf-custom into a terminal window and sudo it, it starts Xgl.  But gdm just gives a grey screen w/the pinwheel thingy and then dumps me to the terminal.

---

### Post by panurge77 on 2006-05-25
About nvidia driver options: I'm new to Ubuntu but I used suse for the last couple months and I remember reading on suse howto's that nvidia drivers enable renderaccel as default on installation, and they didnt mean only theirs rpm, but the nvidia drivers from nvidia site too. I'm running xgl perfect without that option. Also, option "NoFlip" "true" is suggested on novell cool solutions, but I have no clue what's that about.

[http://www.novell.com/coolsolutions/feature/17174.html](http://www.novell.com/coolsolutions/feature/17174.html)

Anyone knows more about that?

---

### Post by Tedd on 2006-05-26
Hello;

I followed the instructions on how to get Xgl/Compiz running on my Ati Radeon 9800Pro,  located here: [www.wiki.ubuntu.org/xglati](www.wiki.ubuntu.org/xglati)

I got it working...sort of. It has a few problems, namely just two. The first is that when I try to move windows, I can't. As in, windows are locked to the sides of the screen.

And the second is that when I open programs, this yellow border expands until the program is opened. That's annoying, not to mention ugly.

Can anybody PLEASE point me in the right direction?

---

### Post by spockrock on 2006-05-26
btw the newest quinn package allows for xinerama........I have it going now its great

---

### Post by Tedd on 2006-05-26
Hate to bump, but I fixed the first error; the one about the docking. Now I just need to get rid of that ugly border that pops up when I open programs.

Also, it's a little bit slow...is there a way to fix it?

---

### Post by panurge77 on 2006-05-26
Dock is still very unstable on most systems. Disabling zoom created windows on the minimize plugin was known for helping a better perfomance but I'm not sure if it's still needed (compiz is developing fast).

(For amd64 users: looks like latest compiz isn't avaiable on beerorkid repo, so try this: [http://ushineko.com/compiz/](http://ushineko.com/compiz/) )

---

### Post by spockrock on 2006-05-26
hmm..... use gconf-editor, then apps>compiz and see if you can turn down some of the candy, and help speed it up.  as per the yellow border I think thats only if you use a shortcut, and I am not sure how to get rid of it.....

---

### Post by E-Jey on 2006-05-26
I have a nvidia 6600 with twinview configured on two 17" hitachi LCD screens. I'd like to install XGL/Compiz on my computer. It now support xinerama :D I add the [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) repository and update al the packages. To install xgl/compiz i used this howto: [https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto), the first method/way. 

After i've changed the session and I logged in, the xserver went down. I have nog idea to fix it. How can i solve this? Thanks in advance! This is the error file: 

```

  GNU nano 1.3.10                               File: /home/erik/.xsession-errors_backup

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "erik"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
SESSION_MANAGER=local/erik:/tmp/.ICE-unix/6532
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:6553): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  1112
  Current serial number in output stream:  1131
The application 'gnome-session' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :1.0.

** (gnome-panel:6553): WARNING **: FIXME: wait for completion unimplemented
update-notifier: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
gnome-window-decorator: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
X connection to :1.0 broken (explicit kill or server shutdown).
gnome-cups-icon: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :1.0.

```

---

### Post by panurge77 on 2006-05-26
You could try another how-to, there are plenty of them around. Looks like your problem was with the fonts so you might be missing some package... libcairo maybe?

---

### Post by spockrock on 2006-05-26
yeah try using poofy's nvidia how to guide, if you wannna use xinerama I posted my config in this thread.

[http://www.ubuntuforums.org/showthread.php?t=172026](http://www.ubuntuforums.org/showthread.php?t=172026)

---

### Post by Tedd on 2006-05-26
Sigh, a new problem. I get logged off my Xgl to a screen with the white box to log back in with and nothing more. It's also frozen. I have to restart to get off of it.

---

### Post by chavo on 2006-05-26
[QUOTE=E-Jey]I have a nvidia 6600 with twinview configured on two 17" hitachi LCD screens. I'd like to install XGL/Compiz on my computer. It now support xinerama :D I add the [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) repository and update al the packages. To install xgl/compiz i used this howto: [https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto), the first method/way. 

After i've changed the session and I logged in, the xserver went down. I have nog idea to fix it. How can i solve this? Thanks in advance! This is the error file: 

```

  GNU nano 1.3.10                               File: /home/erik/.xsession-errors_backup

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "erik"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
SESSION_MANAGER=local/erik:/tmp/.ICE-unix/6532
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:6553): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  1112
  Current serial number in output stream:  1131
The application 'gnome-session' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :1.0.

** (gnome-panel:6553): WARNING **: FIXME: wait for completion unimplemented
update-notifier: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
gnome-window-decorator: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
X connection to :1.0 broken (explicit kill or server shutdown).
gnome-cups-icon: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :1.0.

```[/QUOTE]

Did you install the latest nvidia drivers 8762? I tried them out and got lots of crashes and IO error just like you got. I went back to the 8756 and all is well.

---

### Post by mcduck on 2006-05-27
[QUOTE=Tedd]
And the second is that when I open programs, this yellow border expands until the program is opened. That's annoying, not to mention ugly.

Can anybody PLEASE point me in the right direction?[/QUOTE]
Open gconf-editor, go to apps/panel/global and unmark 'enable_animations'. That works for about everything, only opening Trash still has those ugly borders (I haven't found any way to disable those). This not only disables those ugly borders, but also makes things work smoother as your machine is not trying to run 2 animations for the same thing at the same time..

Another thing that might improve Compiz performance is, again in gconf-editor, to unselect apps/compiz/general/screen0/options/detect_refresh_rate ans set apps/compiz/general/screen0/options/refresh_rate to 60.  Give it a try, and if you see no improvement then just anable detect_refresh_rate again :)

---

### Post by E-Jey on 2006-05-27
[QUOTE=chavo]Did you install the latest nvidia drivers 8762? I tried them out and got lots of crashes and IO error just like you got. I went back to the 8756 and all is well.[/QUOTE]

Yeah, I use the newest drivers because otherwise Twinview won't work. I tried another how to and I have less errors: 

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "erik"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/erik:/tmp/.ICE-unix/6133

(gnome-panel:6201): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

(gnome-panel:6201): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -21 and height 24

```

I'm absolutely sure that I use the --replace option.

---

### Post by Tedd on 2006-05-27
The yellow boxes error got fixed, thanks. But I still get kicked back to the login screen every ten minutes, if that, only on the XGL login.

---

### Post by cooldudejz on 2006-05-27
i have a few questions
1) i installed the latest nvidia drivers from synaptic, and when i am in a XGL/Compiz session my usual nvidia settings arent there anymore. in a gnome sessions their are a bunch of setting and i am able to see the temp of my GPU. in XGL session i have like 4 options. i have a GeForce 7300 GS with 256mb. i dont think i am using the card right because my cpu usage goes up to like 90% while moving windows and other things, but my GPU should be handling this. should i reintsall the drivers using the guide on this website.
2) Somehow i messed up and XGL/Compiz is the only session i can choose now. how do i kill this session and go back to my old x-session. thanx
3) my widgets are darkened out

---

### Post by InsomniacUK on 2006-05-27
Okay, I now have XGL/Compiz working on my box (running Dapper Drake RC). Everything seems to work, except for one problem. It seems to prevent games like UT2004 from running correctly. The frame rate suffers and textures are missing.

I have XGL/Compiz set to start automatically when I log into Ubuntu. Is there anyone out there who is more skilled than myself who could tell me if it's possible to write some kind of script that would disable XGL/Compiz whilst certain programs (UT2003/2004) run and then start up again afterwards?

---

### Post by ctgray on 2006-05-28
Anyone know where I can get debs of libsvg and libsvg-cairo? They're not in the repo's.

---

### Post by spockrock on 2006-05-28
[QUOTE=cooldudejz]i have a few questions
1) i installed the latest nvidia drivers from synaptic, and when i am in a XGL/Compiz session my usual nvidia settings arent there anymore. in a gnome sessions their are a bunch of setting and i am able to see the temp of my GPU. in XGL session i have like 4 options. i have a GeForce 7300 GS with 256mb. i dont think i am using the card right because my cpu usage goes up to like 90% while moving windows and other things, but my GPU should be handling this. should i reintsall the drivers using the guide on this website.
2) Somehow i messed up and XGL/Compiz is the only session i can choose now. how do i kill this session and go back to my old x-session. thanx
3) my widgets are darkened out[/QUOTE]

1) Thats more then me, but its a bug in nvidia-settings that it doesnt work with xgl.  make sure in the xorg.conf that you are using driver "nvidia" and you have option "RenderAccel" "True"

2)I dunno sorry...

3)umm what do you mean when you press F9 nothing is there but a darkened screen or just nothing is there.  when you add a widget in the state plugin your have to be running the app so it shows in the widget layer.  for example if you have p:cairo-clock:2 in the widget key in the state plugin, then make sure you run cairo-clock.

---

### Post by krang on 2006-05-28
Note:
Xgl and compiz works very fine with the standard ati driver for me.
fglrx messed my dri up, every time I installed it. Not having it in the xorg.conf activated, it killed my dri while only being in the kernel. I uninstalled all fglrx packages and tried the installation of xgl.
After updating compiz, it works very nice. No errors yet and it only slows down, while using compiz plugins like rotate very fast.

hm, dri seems to be also deactivated as glxinfo says, but it works.. :o

---

### Post by Paool on 2006-05-28
hi there :)

I've got problem with mplayer. In fullscreen mode sound is ok, but picture goes slow... in window mode is ok. I've tested xv and x11 video modes :/ gl and gl2 doesn't work :(

aby ideas?

---

### Post by Bazon on 2006-05-28
[QUOTE=Paool]hi there :)

I've got problem with mplayer. In fullscreen mode sound is ok, but picture goes slow... in window mode is ok. I've tested xv and x11 video modes :/ gl and gl2 doesn't work :(

aby ideas?[/QUOTE]
For me, gl2 works more or less in Fullscreen. But if you don't manage it to use gl2, you may want to try starting a seperate Xorg server? Check method 3 and 4 from the link in my sig....

---

### Post by Paool on 2006-05-29
if there's no other way I'll try it :) thanks!

---

### Post by francescob on 2006-05-29
hello, i've installed Xgl/Compiz on my new laptop with a turion64 and ati x200m. Everything works fine, effects and all, but windows have no decoration.
i start compiz and xgl using this commands
Code:

#!/bin/sh 
# Start up Xgl, compiz 
# Run Xgl server on :1, on top of normal X 
/usr/bin/Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer & 
# Tell subsequent X programs to access the Xgl server at :1 
DISPLAY=:1 
# Start Compiz window manager 
sleep 5 
gnome-window-decorator & compiz --replace gconf & 
# Start KDE 
exec startkde


compiz version is 0.0.11
any hint?

---

### Post by g14 on 2006-05-29
[QUOTE=francescob]hello, i've installed Xgl/Compiz on my new laptop with a turion64 and ati x200m. Everything works fine, effects and all, but windows have no decoration.
i start compiz and xgl using this commands
Code:

#!/bin/sh 
# Start up Xgl, compiz 
# Run Xgl server on :1, on top of normal X 
/usr/bin/Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer & 
# Tell subsequent X programs to access the Xgl server at :1 
DISPLAY=:1 
# Start Compiz window manager 
sleep 5 
gnome-window-decorator & compiz --replace gconf & 
# Start KDE 
exec startkde


compiz version is 0.0.11
any hint?[/QUOTE]
Try replacing gnome-window-decorator with "kde-window-decorator" Please note that I don't use KDE, but I know that a kde-window-decorator exists because of some nuances in how kde works.

---

### Post by francescob on 2006-05-29
[QUOTE=g14]Try replacing gnome-window-decorator with "kde-window-decorator" Please note that I don't use KDE, but I know that a kde-window-decorator exists because of some nuances in how kde works.[/QUOTE]

hi, thanx for your answer. I've already tried but no luck even with that. Anyway i'm thinking to switch to a i386 build, to get rid of other problems and hopefully also this

---

### Post by tobey on 2006-05-29
No matter what I do, I can't get it to work... Maybe someone living around Bruges could come and give me some help? Bruges, that's right, lace and chocolate for this big boy :D.

---

### Post by nero2150 on 2006-05-29
this should be added to this forum its been in the wrong section all the time

[http://www.ubuntuforums.org/showthread.php?t=147049](http://www.ubuntuforums.org/showthread.php?t=147049)
If not already added ;) 
Easy install but with some extra (install beagle etc)at your own risk [-(

---

### Post by navil on 2006-05-31
I got my gnome-compiz/aigxl working fine on my intel 915. I did an upgrade last week and for some reason  my "always on top" window setting seems to be disabled. Does any one know any way to get it back :-k

---

### Post by moclippa on 2006-05-31
I wouldn't recommend putting XGL in your startup processes. For a while it was corrupting my nvidia drivers, and I'd get all sorts of xserver faliure errors till I outed it.

---

### Post by PriceChild on 2006-06-02
If the shift+backspace "feature" restarting x has annoyed you, check out here: [http://ubuntuforums.org/showthread.php?t=186714](http://ubuntuforums.org/showthread.php?t=186714)

---

### Post by No_sanctuary on 2006-06-03
[QUOTE=francescob]hi, thanx for your answer. I've already tried but no luck even with that. Anyway i'm thinking to switch to a i386 build, to get rid of other problems and hopefully also this[/QUOTE]
I had this problem at first too.  Try going into gset-compiz and turning off almost all effects. Besides maybe move and minimize. Then logout and log back in.  Click to enable the decorator plugin and it should work. (At least it did for me)  Then go through and enable the rest of the plugins that you want.

---

### Post by moclippa on 2006-06-03
Since I installed compiz, every time I reboot my computer I get a failed Xserve error. 

If I do a full shutdown and restart it fixes itself. Is that normal?

---

### Post by gadgetgirl on 2006-06-03
That's not normal moclippa. I don't have the expertise to say how to fix it though. :/

Here's my setup, in case it is helpful (slightly different than the OP's method). I created this file in /usr/share/xsessions/xgl.desktop :
```
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

then a /usr/bin/startxgl.sh :
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start GNOME
exec gnome-session
```

and a /usr/bin/startcompiz that I added to my autostart list for the gnome session:
```
#!/bin/bash
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus &
```

I did it this way based on pouring through the forums, and since I like to have the option to pick the eye-candy or stable session in GDM when I log in. I'm not sure if this is the optimal aproach, but it works pretty well for me.

---

### Post by nami on 2006-06-05
How do you get the window to stick to the sides, then when you try to pull it away you can see it being stretched as it comes away?

Anyone know how to do these 2 effects?

---

### Post by panurge77 on 2006-06-05
[QUOTE=nami]How do you get the window to stick to the sides, then when you try to pull it away you can see it being stretched as it comes away?

Anyone know how to do these 2 effects?[/QUOTE]

Hold shift while moving it.

---

### Post by sublime on 2006-06-06
anyone else have a problem with the window boarders staying up when a window is closed.  ive heard of this happening everyonce in a while and experienced it once or twice with dapper beta, but i just did a fresh install of the official dapper release and it happens everytime i close or minimize a window now.

---

### Post by eeclark on 2006-06-06
happens to me with picasa if TRAILFOCUS is on

---

### Post by sublime on 2006-06-06
yeah for me its every time i close any window and the first thing i did was turn off trailfocus.

---

### Post by mcpowley on 2006-06-07
Aghh. No matter what I can't get this working. I am currently running on a pretty good system, with a nvidia 7800GTX GO. I installed the latest drivers and have the splash screen but in my xorg.conf my card is labeled as,
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
---
So, i don't know if it's okay that it isn't labeled correctly, but now to the problem at hand.
I've followed a couple of guides and all the first resulted in me having to reinstall all of Dapper(im a complete newbie, coming from windows all my life) I followed every single step in this guide, but at the end when I was supposed to do the gconf etc etc thing, i get the compiz.real no composite error. also, before this when I do the window manager, I get an error that says i already have a window manager running. Anyway, I added the extensions, composite enable tag to the xorg.conf, i then restarted and got to the login screen...I logged in, and I got the whole ubuntu loading, etc. But the desktop never materialized, it just went black screen. I restarted 3 more times with the same result, I finally ended up booting in safemode terminal and removed the composite line in my xorg.conf and everything worked again. Anyone have any suggestions? I'm dying to get this working. Thanks!

---

### Post by nami on 2006-06-07
Have you tried this guide?
[https://wiki.ubuntu.com/CompositeManager/InstallingCompiz](https://wiki.ubuntu.com/CompositeManager/InstallingCompiz)

But before I discovered this guide, I had to do all the following steps to get it to work on my system with twinview using an old graphics card:

This is what I have to do to get compiz working.

Points to remember are:
a. I have an old geforece 4 ti 4200 graphics card
b. These instructions prepare my system to enable twinview

Instructions
1. fresh install of ubuntu

2. installed nvidia drivers from:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

3. in terminal type:
> sudo apt-get install nvidia-glx nvidia-kernel-common linux-386

4. comment out from xorg.conf in the Modules section:
> # Load "dri"
# Load "GLcore"

5. insert in the Device section:
> BusID  "PCI:1:0:0"
Option "RenderAccel"

6. added to the sources.list:
> deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

7. in terminal type:
> wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -> sudo apt-get update> sudo apt-get install xserver-xgl compiz-gnome gset-compiz

8. in gdm.conf-custom insert at the bottom:
> [servers]
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

9. create /usr/local/bin/compiz-start and insert:
> #!/bin/sh 
killall gnome-window-decorator 
wait
xmodmap /usr/share/xmodmap/xmodmap.uk &
gnome-window-decorator & 
compiz --replace gconf &

10. in terminal type:
> sudo chmod +x /usr/local/bin/compiz-start

11. restart and type in terminal
> compiz-start

---

### Post by sublime on 2006-06-07
i have a strange feeling it was from gset-compiz.  i just reinstalled dapper completely and so far so good (knock on wood).  im going to not install gset-compiz for and leave it like it is for a while, see if i get that problem again.

---

### Post by Shadowline on 2006-06-07
Shouldn't this thread be in the How=To section ?

---

### Post by ketsugi on 2006-06-08
Does Compiz support skinnable window decorators yet, or are we still stuck with the default? I tried Compiz a while back and this one thing was enough for me to go back to xcompmgr instead. I really don't like the default window decorator that Compiz uses.

---

### Post by Klaidas on 2006-06-08
Hehe thanks - problems solved ;)

---

### Post by leohart on 2006-06-08
Just dropping by to say that I am another happy compiz user. The whole process was totally painless. I got my Inspiron 6000 (stock Intel i915) to work with Aiglx and Compiz. The performance is great.

Thanks for all the work that you guys have put in.

---

### Post by Attila_fdd on 2006-06-09
hello, i have many problems with xgl and my pc with nvidia card (7600gt)
I have installed succesfully  xgl on ati+nforce2 config with ubuntu dapper. I think it would be more easy with nvidia cards but i was wrong...

i have found and tried many guides to do that but i cant get it works :(

can you help me? which guide have i to use? is it correct to install the latest nvidia drivers 8762?

---

### Post by xerum on 2006-06-09
Bit of a noob here and I was wondering if I could get some assistance. I recently installed xgl and compiz and for some reason i can't seem to get the cube desktop to display. I issued the following command at the prompt and got the error listed below 'compiz gconf' Thanks in advance


compiz.real: Connection Error (No reply within specified time)
compiz.real: Couldn't initiate D-BUS connection
compiz.real: Disabling D-BUS Service
Finishing dbus10786: arguments to dbus_bus_release_name() were incorrect, assert ion "connection != NULL" failed in file dbus-bus.c line 789.
This is normally a bug in some application using the D-BUS library.
10786: arguments to dbus_connection_close() were incorrect, assertion "connectio n != NULL" failed in file dbus-connection.c line 1934.
This is normally a bug in some application using the D-BUS library.
compiz.real: No composite extension

---

### Post by flankker on 2006-06-09
hi, i have gdesklets in ubuntu with xgl/compiz but its really irritating to have them have a shadow like when they are not in focus. is it possible to disable this shadowing of windows in compiz?

thanx

---

### Post by zitch on 2006-06-09
[QUOTE=flankker]hi, i have gdesklets in ubuntu with xgl/compiz but its really irritating to have them have a shadow like when they are not in focus. is it possible to disable this shadowing of windows in compiz?

thanx[/QUOTE]
You can disable the Trailfocus plugin, from what I can see, and that would take off the "shadowing" effect entirely.

Alternatively, if you wish to keep trailfocus on but disable the effect on certain windows, read this page (and Especially pay attention to the Trailfocus section): [https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29](https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29)

It should help tell you how to setup the "exclude" field to prevent certain programs from being affacted (I.E., I have my video players in the exclude list).

---

### Post by leohart on 2006-06-09
Here is another post to this longest post ever (so far that I have seen) on Ubuntu Forum. I have just gotten my desktop (Ubuntu + nvidia + xgl + twinview) and laptop (Ubuntu + intel i915 + aiglx) working with compiz.

I could not get the nice little Quinn Compiz (gset-compiz) icon on the top right corner to work on my desktop (works on my laptop). Other than that everything else is great.

Thanks to the community and great thanks to Compiz + Quinn package and repos. ^_^

- Another happy compizer -

---

### Post by panurge77 on 2006-06-09
That compiz icon thingy is only included in the aiglx packages.
See [http://www.compiz.net/viewtopic.php?id=1170](http://www.compiz.net/viewtopic.php?id=1170) for the xgl version

---

### Post by leohart on 2006-06-09
That's unfair. Totally unfair. I miss that little cute icon ;)

---

### Post by flankker on 2006-06-10
[QUOTE=zitch]You can disable the Trailfocus plugin, from what I can see, and that would take off the "shadowing" effect entirely.

Alternatively, if you wish to keep trailfocus on but disable the effect on certain windows, read this page (and Especially pay attention to the Trailfocus section): [https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29](https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29)

It should help tell you how to setup the "exclude" field to prevent certain programs from being affacted (I.E., I have my video players in the exclude list).[/QUOTE]

thank u very much, that worked perfectly :)

---

### Post by JungleBoy on 2006-06-11
Can some one tell me if some artifacs on totem and xine are normal, everything is working smooth, just totem and xine are giving me some artifact's on the program window, video still plays well tough.

Specs:
Toshiba Satellite pro M30
Pentium M 1.5Ghz
nVidia Geforce FX go 5200 64MB
256MB of mem.

I folowed the tuto here on ubuntu foruns(a easyer one that i foud, using synaptics) latter on i followed the tuto on [http://www.compiz.net/viewtopic.php?id=652](http://www.compiz.net/viewtopic.php?id=652) with give's me an updated XGL, wenever a new version is released, and made my XGL more stable and fast.
If any one here could awanser me, i'd be very glad!:p

---

### Post by Efrain Valles on 2006-06-11
Ok... Let me ask you asimple question

I wanna run all these... I have seen tons of videos using Compiz and xgl... I am interested in installing it... I have a laptop running breezy an old pentium 3 but I want to set up a new desktop pc... 

what hardware set up would you suggest to use compiz and xgl??

I am thinking AMD ...
and NVIDIA but what models???? what processor...???? 64 bits ???

I was really impressed and I am going for this...

---

### Post by arrizaba on 2006-06-11
Thanks a lot for this wonderful thread!
For once, everything worked only by following your instructions to the letter....no extra tweaking was required!

thanks for the nice work. This kind of threads makes ubuntu the best linux distro on the planet ;)

---

### Post by thero on 2006-06-11
Can anyone help me?

Compiz and xgl is working fine for me.  I would like to keep the workspace switcher and not use the cube which takes too much time.  I want an accelerated desktop without the cube, is that possible?

---

### Post by senzapadroni on 2006-06-12
[QUOTE=thero]Can anyone help me?

Compiz and xgl is working fine for me.  I would like to keep the workspace switcher and not use the cube which takes too much time.  I want an accelerated desktop without the cube, is that possible?[/QUOTE]

This should work:
-install gset-compiz
```
sudo apt-get install gset-compiz
```

- open gset-compiz from applications menu;
- search for **cube** plugin in the left column and deactivate it.

---

### Post by RJMacReady on 2006-06-12
Apologies if this has been remedied elsewhere, I cant seem to find an answer!

Also: I tried Xgl and Compiz a while back and my hardware has not changed one bit.

Ok, so, I got my ATI fglrx drivers and glxgears is simply flying, fglrxinfo has ATI written all over it and I'm fully accelerated. I went and followed poofyhairguy's popular tutorial ([http://www.ubuntuforums.org/showthread.php?t=131267)](http://www.ubuntuforums.org/showthread.php?t=131267)).

Everything is installed and fine, so I decide to run an Xgl server from terminal, which I was told to do previously when I was experiencing a problem (This was on the previous install, a few months ago)

```
sudo Xgl :9 -ac (Ctrl-Z, bg)
DISPLAY=:9
compiz (Woo! The screen is blue!)
gnome-window-decorator (Ctrl-Z, bg)
xterm

```

All I get is an Xgl server, with a blue background and an Xterm with no border or controls sitting in the upper left corner of the window. Okay, must be a restart problem! I reboot (Knowing that I've made changes to /etc/gdm/gdm.conf and .conf-custom) to see if it loads properly. The machine sits at a screen with a black and white checkered background with a loading cursor. The only way to break this is to re-edit gdm.conf and .conf-custom and roll-back the changes.

Uh... ok, try a new tutorial! (One from Compiz.net)

This particular tutorial uses Beerorkids repos and an updated Xgl/Compiz package. Awesome! Stability. Wrong. If I do the stuff mentioned above (Sudo Xgl :9 etc) the terminal spits out 'Segmentation fault' and does nothing. If I restart, the screen yoyo's back and forth between a GDM login screen and a black terminal window with a logon at the top. It does this about 10 times and then X spits out fatal errors and gobbledygook.

What am I doing wrong? I think I'm gonna cry! :-({|=

---

### Post by thero on 2006-06-12
no that does not work.  I merely lose the ability to switch to other workspaces/viewports.

---

### Post by nero2150 on 2006-06-13
Compiz works fine but a bit of touble to set the plugin correctly 
I almost had it the way I want except now I cannot move a window on keyboard to the next viewport on the cube. :confused: 
Also it seems when I try to move the window on the viewport menu on the title bar it go only to the next viewport. ](*,) 

I m using compiz 0.0.13 

If someone can help Plz!!! Wander if there is a howto only for the plugin explaining each plugin setup?

Ps: anyone tried the neg plugin :cool:

---

### Post by oocce on 2006-06-14
Is there way to change different wallpaper in each workspace (Compiz&Gnome)?

---

### Post by Punio4 on 2006-06-15
OK... installed it using this guide:
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It works... and it's fluid, until the animation should come to a stop... like wobble, fade in etc... how do i fix that?

---

### Post by kpkeerthi on 2006-06-15
Thank you for stickying this thread. 

I tried all the xgl/compiz guides scattered all over the forums. They all worked but caused a lot of annoying artifacts, DVD playback issues. I followed the ones consolidated here and works like charm. Never thought xgl/compiz can be so silky smooth. Thanks to g14 for picking the most correct ones.

---

### Post by Super-T on 2006-06-15
Hey, all I can say is a heartfelt thanks for all the info in this thread!   I was able to get xgl and compiz working well enough on an older amd athlon with a nvidia geforce 3 card... wow, it looks great!  
I do have a coupl'a questions, tho'  --  where is the neat rain effect (with shift F9 and Ctrl-Super) I have seen on installations of xgl and compiz on SuSE 10.1 and SLED 10?  Is it a plug-in that I don't have installed?   
Cheers, 
T.

---

### Post by CalvinChile on 2006-06-15
May be a stupid question: I have an Inspiron6400 with an Intel Media Accelerator 950 (INTVID). Which one is the right set up to install Xgl/Compiz?

Thanks 
Calvin

---

### Post by Griff on 2006-06-17
I've got it all working...sort of.  I used the method outlined here:
[http://www.compiz.net/viewtopic.php?id=652]("http://www.compiz.net/viewtopic.php?id=652")
The only change I made to it was making a new Xgl session as outlined in the ubuntu wiki.  At first my keyboard setup was wrong, but I changed it and everything worked.  So I edited the startup program to take a us keyboard instead of what it did have:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```
Now when I start my xgl session wobble and things like that work but none of my keyboard commands work so I'm guessing there is still something altering the layout only I can't find it.  Any ideas what could be wrong?  It worked before so there should be an easy fix.

---

### Post by g14 on 2006-06-17
System --> Preferences --> Keyboard and play with the layout to make sure it is correct.

---

### Post by Griff on 2006-06-18
[QUOTE=g14]System --> Preferences --> Keyboard and play with the layout to make sure it is correct.[/QUOTE]

Changed keyboard type to 'Microsoft Internet Keyboard' and it worked.
Thanks for pointing out the obvious.  :rolleyes:

EDIT: Ok. So it's sort of a fix.  All the keyboard shortcuts only work if I change the keyboard layout after logging in.  I.E. it doesn't matter what the setting is so long as I change it after logging in.  What's going on?

---

### Post by elv on 2006-06-18
Hi have Compiz working fine here, but for some reason the ctrl-alt-delete dosent open up the system monitor when running compiz.
But it works fine under metacity

---

### Post by Griff on 2006-06-18
[QUOTE=elv]Hi have Compiz working fine here, but for some reason the ctrl-alt-delete dosent open up the system monitor when running compiz.
But it works fine under metacity[/QUOTE]
Did you do this after installing xgl/compiz?
```
gconftool-2 --set --type string /apps/compiz/general/screen0/options/run_command1 "<Control><Alt>Delete"
gconftool-2 --set --type string /apps/compiz/general/screen0/options/command1 "gnome-system-monitor"
```

---

### Post by wonko on 2006-06-18
I have some problems installing compiz for KDE on my AMD64 with an NVIDIA card. Seems many have problems with this combo since there's no howto for us... Can someone who has got this working please write a howto?

---

### Post by elv on 2006-06-18
[QUOTE=Griff]Did you do this after installing xgl/compiz?
```
gconftool-2 --set --type string /apps/compiz/general/screen0/options/run_command1 "<Control><Alt>Delete"
gconftool-2 --set --type string /apps/compiz/general/screen0/options/command1 "gnome-system-monitor"
```[/QUOTE]




Yes I did.:(

---

### Post by jewishj on 2006-06-18
For the most part, compiz is working great.. a couple of issues I'm having:

1) Whenever do anything that does the dimming effect (such as run administrative tool that takes root pass or click the button in the corner to get to restart/logout/etc. menu) it takes forever
**Fixed:  The problem was that I had to uncheck the "urgent" option in gconfig in apps->compiz->plugins->fade->screen0->options**

2) When I try to play a couple of games (one is Slime Forest [http://lrnj.com/slimeforest.html](http://lrnj.com/slimeforest.html)) the entire window is opens in is transparent (and right-clicking the title bar and setting opacity to 100% does nothing) instead of just the title bar.

3) Whenever I restart/logout (restart X in some fashion) maximizing a window maximizes from the bottom of the top panel bar to the bottom of the screen (behind the bottom panel bar) (instead of the top of the bottom panel bar).  If I minimize any windows, go into the bottom panel bar properties, change the size and change it back, then it maximizes correctly.

4)  OpenGL games are very slow and buggy (Billiard-GL for example) as are some (OpenGL only I assume) screensavers

5) Ctrl+Alt+L no longer locks screen

Thanks for any help with this

Also, is there a list somewhere that describes what all of the effects do?

---

### Post by digiplaya on 2006-06-19
Hi all: I'm just wondering if anyone's got any solutions for the "hourglass and gray screen" problem when you try to run Xgl/Compiz.

It does this to me when run with "startx" or when KDM attempts to load. Can't get any farther than that.

My video is Radeon 9550 w/ fglrx drivers and kernel 2.6.17. (I know this hardware is pesky with XGL/Compiz but bear with me here.) 

rest of specs:

P4 2.4 w/o HT
1 Gig DDR1 RAM
2 120GB hard drives
Kubuntu Dapper full install
and so on.

I'm at the end of my rope, I'm pretty sure. I've tried everything that I can think of already.

Tom

---

### Post by spockrock on 2006-06-19
[QUOTE=digiplaya]Hi all: I'm just wondering if anyone's got any solutions for the "hourglass and gray screen" problem when you try to run Xgl/Compiz.

It does this to me when run with "startx" or when KDM attempts to load. Can't get any farther than that.

My video is Radeon 9550 w/ fglrx drivers and kernel 2.6.17. (I know this hardware is pesky with XGL/Compiz but bear with me here.) 

rest of specs:

P4 2.4 w/o HT
1 Gig DDR1 RAM
2 120GB hard drives
Kubuntu Dapper full install
and so on.

I'm at the end of my rope, I'm pretty sure. I've tried everything that I can think of already.

Tom[/QUOTE]

have you tried the xserver-xorg-driver-radeon packages?

---

### Post by seshomaru samma on 2006-06-19
There are so many XGL threads I don't know where to post this one....
Anyway I installed XGL/Compiz following [this ]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide")guide 

I can get this wobbly effect when I drag the windows with the mouse and the windows move in a cool way and I can switch workspaces in a cube like manner but non of the hot keys work.

Anyone has any advice?

---

### Post by jewishj on 2006-06-19
[QUOTE=elv]Hi have Compiz working fine here, but for some reason the ctrl-alt-delete dosent open up the system monitor when running compiz.
But it works fine under metacity[/QUOTE]

Hey - I had the same issue.  I figured out that the input in the gset-compiz gui is backwards.  So to fix it, If you're using the gset-compiz gui, enter the keycode where it says command and the command where it says keycode.  

Otherwise, you can manually add it via gconfig.

Go to apps->compiz->general->allscreens->options, enter the command (gnome-system-monitor) for the command0 entry, then enter the shortcut (<Control><Alt>Delete) to the run_command0 entry.

You should be able to copy this procedure for command1/run_command1 and so on to add other custom keyboard shortcuts.

On a related note, my Control+Alt+L for lock doesn't work since I installed, does anyone know what the command to lock the screen is?

Thanks

---

### Post by Griff on 2006-06-19
[QUOTE=seshomaru samma]There are so many XGL threads I don't know where to post this one....
Anyway I installed XGL/Compiz following [this ]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide")guide 

I can get this wobbly effect when I drag the windows with the mouse and the windows move in a cool way and I can switch workspaces in a cube like manner but non of the hot keys work.

Anyone has any advice?[/QUOTE]

I had to change my keyboard layout under System > Preferences > keyboard and it got everything working.  This is a sort-of fix though.  At least for me it was.  Everytime I log back in I have to change the keyboard.  It doesn't matter what setting it was on I just have to change it.  Wish I knew a fix to that problem.  :(

EDIT: Problem fixed; had a startup item that was overwriting my keyboard options; XGL/Compiz working at 100% :D

---

### Post by elv on 2006-06-19
[QUOTE=jewishj]Hey - I had the same issue.  I figured out that the input in the gset-compiz gui is backwards.  So to fix it, If you're using the gset-compiz gui, enter the keycode where it says command and the command where it says keycode.  

Otherwise, you can manually add it via gconfig.

Go to apps->compiz->general->allscreens->options, enter the command (gnome-system-monitor) for the command0 entry, then enter the shortcut (<Control><Alt>Delete) to the run_command0 entry.

You should be able to copy this procedure for command1/run_command1 and so on to add other custom keyboard shortcuts.

On a related note, my Control+Alt+L for lock doesn't work since I installed, does anyone know what the command to lock the screen is?

Thanks[/QUOTE]



Hey thanks for that, added the commands to the allscreens, was just using it in Screen0, and it worked like a charm =D>

---

### Post by Griff on 2006-06-19
Is there a list of what all the default plugins do? There are a few things (like wobbly windows :( ) that make my fiance dizzy.  I just need some descriptions of what they are so I don't disable stuff I don't mean to.

---

### Post by panurge77 on 2006-06-19
Griff:
[http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)
I dont know how updated that is, though

---

### Post by NXArmada on 2006-06-19
i am trying to get compix working but i get this error everytime i try to run it:

GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

also when i run it i loose all boarders.

---

### Post by seshomaru samma on 2006-06-20
[QUOTE=Griff]I had to change my keyboard layout under System > Preferences > keyboard and it got everything working.  This is a sort-of fix though.  At least for me it was.  Everytime I log back in I have to change the keyboard.  It doesn't matter what setting it was on I just have to change it.  Wish I knew a fix to that problem.  :(

EDIT: Problem fixed; had a startup item that was overwriting my keyboard options; XGL/Compiz working at 100% :D[/QUOTE]

Change the keyboard layout to what?
The only option I get is U.S english (and my keyboard is US English)

edit: NEVER MIND , I SORTED IT OUT....
THANKS

---

### Post by Z3RatuL on 2006-06-20
Um, using the guide for the AMD64 version (**from pdc303**) of compiz, I would like to know how to load more plugins than the default ones. I want to load widget, water and dock.

I tried using a guide from compiz.net forums, on how to order plugins and it didn't work, because they said it's according which version of compiz you're running. Everytime I tried to load a plugin through gconf-editor it would dissapear after I pressed **OK**. From what I saw at the HOW-TO **pdc303** uses a compiled version of his own and not a default one, so is there a way to load these additional plugins?

---

### Post by hxx4 on 2006-06-20
I'm getting this error when I run sudo apt-get update:
```
W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
```
I'm doing this on ubuntu dapper desktop i386.

---

### Post by copey02 on 2006-06-20
is there way to make all out-of-focus windows transparent or opaque?

---

### Post by oocce on 2006-06-21
[QUOTE=Griff]I had to change my keyboard layout under System > Preferences > keyboard and it got everything working.  This is a sort-of fix though.  At least for me it was.  Everytime I log back in I have to change the keyboard.  It doesn't matter what setting it was on I just have to change it.  Wish I knew a fix to that problem.  :(

EDIT: Problem fixed; had a startup item that was overwriting my keyboard options; XGL/Compiz working at 100% :D[/QUOTE]
Can you tell what startup item you are using? I have same problem...

For others; I have installed Xgl/Compiz like this: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29) , but I cant get transparency working... I have read that alt+mouse wheel should do it to focused window :roll:

---

### Post by angma on 2006-06-21
I am getting soooo angry.... without compiz and xgl, my monitor never goes to sleep because i have told power management... NEVER to do so! But with compiz and xgl, i can't figure out why my monitor keeps going to sleep every 15 to 20 mins. This has nothing to do with any settings I can change in the gnome gui... i've tried. "Power management" is set to "never" on all counts. Am I missing something. I watch movies a lot... sick of monitor blanking. Yes.. I am a HUGE noob to compiz and xgl, but if anyone can tell me the secret answer to my problems... i might even send you an e-card. ^^

---

### Post by YourDoom123 on 2006-06-21
Not sure if this has been posted before or not, but XGL/Compiz stability can be greatly increased by turning OFF the dock/miniwin plugins. When i had one of these two on, compiz would crash randomly when a program was exited, or render me incapable of typing in one of the windows, etc. I turned these off, and haven't had a single problem since.

---

### Post by Griff on 2006-06-21
> **oocce]Can you tell what startup item you are using? I have same problem...

For others said:**
> http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29[/url] , but I cant get transparency working... I have read that alt+mouse wheel should do it to focused window :roll:

If your keyboard option is messed up at boot you may need to insert the following into your System > Preferences > Sessions > Startup Programs tab:
```
xmodmap /usr/share/xmodmap/xmodmap.us-int
```
The part at the end (here: us-int) will need to change depending on your specific keyboard layout.  I know for a lot of people this seems to work:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```
This may correct all your other problems since right now your 'alt' button may not be read as an 'alt' button.
Good luck,
Griff

---

### Post by Griff on 2006-06-21
[QUOTE=hxx4]I'm getting this error when I run sudo apt-get update:
```
W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
```
I'm doing this on ubuntu dapper desktop i386.[/QUOTE]

You're missing the keys for those packages.  They can be obtained by doing the following one at a time.
```
gpg --keyserver subkeys.pgp.net --recv-keys 0x31a5f97fed8a569e 
gpg --export --armor 0x31a5f97fed8a569e | sudo apt-key add -
```
Good luck with the rest of the install.
Griff

---

### Post by BetaguyGZT on 2006-06-22
W: Failed to fetch [http://www.beerorkid.com/compiz/pool/main/p/poppler/libpoppler1_0.5.3-0ubuntu1_i386.deb](http://www.beerorkid.com/compiz/pool/main/p/poppler/libpoppler1_0.5.3-0ubuntu1_i386.deb)
  MD5Sum mismatch

Whats the fix for this?

---

### Post by winter_mute on 2006-06-23
I'm missing the libpool thing, but more importantly, I'm getting an interesting error of the bar on the top of the window not showing up at all.  That, and text typing painfully slow, or at least rendering a response to my tping.

It's not giving me any helpful messages, or even unhelpful error messages.  Anyone run into this before?I used the Wiki's method for installing, if it helps any.

---

### Post by panurge77 on 2006-06-23
From compiz forum:

You can use this repository to install libpoppler

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

sudo apt-get install libpoppler1

Then you can switch back to the beerkoid repository

---

### Post by winter_mute on 2006-06-23
Better description of my issue -- gnome-window-decorator isn't doing anything, so I don't get the titlebars.  Still can't figure out why typing in Firefox is so slow, but...  What should I do about gnome-window-decorator?  I had XGL working in breezy, but decided to uninstall it for a while.  So clearly that was a mistake on my part.

---

### Post by funnyguyfunnyguy on 2006-06-23
I had previously installed XGL + Compiz; however, in an effort to install MythTV, I have attempted to reinstall XGL + Compiz. I have not been able to successfully reinstall XGL + Compiz. I have followed to guide for installing XGL on the wiki, and the guide for installing compiz, which is also on the wiki. When ever I try to run the gnome window decorator and compiz I get the following error

steve@steve-desktop:~$ gnome-window-decorator & [1] 5873 steve@steve-desktop:~$ compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water & [2] 5876
steve@steve-desktop:~$ compiz.real: No composite extension

[2]+  Done                    compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water
steve@steve-desktop:~$
steve@steve-desktop:~$

I have a nvidia 6200 video card. My only concern is that XGL may not be running despite strictly following the wiki. (I have read that you receive the "compiz.real: No composite extension" error when XGL is not running.) Does anyone have any ideas?

---

### Post by jmrush on 2006-06-24
Is there a guide to gset-compiz.I have XGL installed and everything ran without glitches.Suddenly yesterday I modified something and first all the closed windows left some kind of halo once they're closed.After that they turned transparent and cannot see whats inside the any window.
Could I momentary deactivate xgl to fix it?
Thanks

---

### Post by panurge77 on 2006-06-24
You don't need to disable xgl to fix it, you can just switch compiz for metacity temporarily
```
metacity --replace
```
then back again
```
compiz --replace gconf
```

---

### Post by speedsix on 2006-06-29
Can I run XGL/Compiz on a multi-screen dualhead system?

---

### Post by Adamal on 2006-06-29
[QUOTE=speedsix]Can I run XGL/Compiz on a multi-screen dualhead system?[/QUOTE]


I got it to work.  I have a nVidia 7600GT card with dual DVI.  It is pretty sweet, with dual display.

---

### Post by Conan on 2006-07-02
I've got it working with Twinview on a Geforce 7600, and it's excellent. spans the desktop, and the cube is wide, but still allows you to maximize to just one screen, just as it should.

---

### Post by Malta Soron on 2006-07-05
Did you have to do anything special, or was it enough to just install xgl and TwinView? And in which order did you install them?

---

### Post by smartalecks on 2006-07-07
Heya

quick problem with XGL & Compiz- 

Applications such as Open Office open in different workspaces. 
No matter what I do it always opens in a different workspace than the one I am currently viewing. Why is this? How do I change it? It's very annoying.

---

### Post by rynop on 2006-07-07
How do you add plug-ins?  I don't have dock enabled and I want it.  Was this something that should have been specified at compile time? do i not get it cuz whoever make the package didnt include it in the compile?

---

### Post by boakes on 2006-07-08
Are the repo's dead??

---

### Post by _simon_ on 2006-07-10
Are you getting this?

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

If so, you need to do this:

```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -

```

---

### Post by verfruehte on 2006-07-11
excusme, I made allready dist-upgrade without knowing if my Nvidia Geforce Ti gona work with xgl/compiz? My machine is only PII with 500Ram, should I continue?

love

---

### Post by ericesque on 2006-07-12
I'm sure 'one thread to rule them all' seemed like a good idea at the time.  I think it's being abused and has become relatively less useful.

That being said, I'm starting a new thread about my problem and there's nothing you can do to rule it! ... well, maybe you can, but I hope you don't!

---

### Post by Melciah on 2006-07-13
Solutions to the following would be awesome.

Moving the mouse while watching any video in totem fullscreen causes the video to lag a lot. 

If i try to open up a new file in Comix, i get this weird messed up dialog box that cant be used. Im forced to exit the application evertime i want to open up a different file. Check out the attachment to know what im on about.

---

### Post by jvermeulen on 2006-07-13
I have a strange problem, when I empty the wastebasket, the dialog asking me if I really want to remove all items, is in the background, while another window that was open (e.g. Evolution) pops to the front.

Any idea how to fix this as it's really annoying?

Thanks

---

### Post by jvermeulen on 2006-07-13
Apparently this only happens when I use the "Show Desktop" button so that all windows are minimized. Then when I click on "Empty Wastebasket", the minimized windows are pushed to the front again, covering the dialog box asking me to confirm emptying the wastebasket.

Then, when I press the "Show Desktop" button again, all windows are minimized, including the dialog box asking me to confirm ](*,) 

Does anyone else experience the same problem?

---

### Post by utnubu001 on 2006-07-15
can someone help me..

it only works if i type sudo compiz-start.py
if i dont i lose my window borders..

PLEASE HELP

---

### Post by canadianwriterman on 2006-07-17
I installed successfully, but I'm not all that impressed. Should I remove XGL/Compriz or is it safe to just leave it installed? I have to start it manually anyway with "thefuture" otherwise my standard desktop is what boots up.

---

### Post by fyleow on 2006-07-18
I installed Compiz as per the instructions and everything works, but I still don't see the dock plugins.  I tried searching on how to install new plugins but I couldn't find anything.

Can anyone help?

---

### Post by mcduck on 2006-07-18
> **fyleow said:**
> I installed Compiz as per the instructions and everything works, but I still don't see the dock plugins.  I tried searching on how to install new plugins but I couldn't find anything.

Can anyone help?

The dock isn't part of the package now, as it has some bugs that make it rather unusable. It'll return again when somebody has fixed it. If you still want to give it a try, you can probably get it from compiz forums..

---

### Post by Joey French on 2006-07-18
Hi, all. I have installed XGL/Compiz on Kubuntu and it works fine, except for the fact that I lose my window decorations. If I run 
```
/usr/bin/compiz gconf & /usr/bin/gnome-window-decorator &
```
I get my borders, but not the themes I want to use. Any ideas?

---

### Post by mcduck on 2006-07-18
> **Joey French said:**
> Hi, all. I have installed XGL/Compiz on Kubuntu and it works fine, except for the fact that I lose my window decorations. If I run 
```
/usr/bin/compiz gconf & /usr/bin/gnome-window-decorator &
```
I get my borders, but not the themes I want to use. Any ideas?

What do you mean with theme files? Compiz replaces your current window manager, so it needs it's own themes, Metacity or Kwin themes don't work..

---

### Post by Joey French on 2006-07-18
Yes, that's what I mean, no themes, and no window decorations. So, then I can fix it with the previous shell command, but I don't have my KDE preferences, and I can't adjust the theme that it (gnome) defaults to. I guess what I am asking is: Can I run XGL under KDE yet, and have window decorations and such that correspond to the ones I set in my KDE? Right now I am running XGL under KDE with a sort of half arsed way of getting window decorations and such, and I am looking for a better/cleaner way to make this happen.

Joey French

---

### Post by RAOF on 2006-07-19
> **Joey French said:**
> ...Can I run XGL under KDE yet, and have window decorations and such that correspond to the ones I set in my KDE?...
No.  You can't do it under Gnome, either.

The vanilla compiz window decorator currently has no theming possible, and the compiz-quinn decorator has recently gained minimal theming possiblities (change colour/opacity/button pixmaps).

---

### Post by Joey French on 2006-07-20
> the compiz-quinn decorator has recently gained minimal theming possiblities (change colour/opacity/button pixmaps).

Yes, but it barely works at all. I am still unable to get it to save my preferences at all. 

Quick question: How do I go about setting the little "ghost/wave like appearance" of the little box dialogs on my desktop to move more quickly? I think they are neat, but need to move into focus more quickly so my mouse can get onto them. I have tried to change the speed in gset-compiz, but I don't really know what this effect is called, and it doesn't seem to save my preferences anyway.

---

### Post by Owdy on 2006-07-20
> **g14 said:**
> ```

sudo gedit /etc/apt/sources.list

``` Add this to the very end:
```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

``` Whats the difference with these repos [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) ? What should we use?

---

### Post by Uncle Spellbinder on 2006-07-23
I've read many a thread about Xgl + Compiz, xorg-aiglx + compiz (and variations thereof). I really like the default Ubuntu Dapper Drake 6.06 LTS / Gnome look. But it can be somewhat drab. I just want to spice things up a bit.

I'm wondering something I've not located the answer to. If I've missed it, apologies in advance.

Should I even bother with an embedded Intel video controller [82915G/GV910GL Express Chipset Family]? If this will work, which should I choose: *Xgl + Compiz* or *Xorg-Aiglx + Compiz*. And I assume *Quinn Compiz* is the way to go? Or so I've read.

---

### Post by jstueve on 2006-07-23
aiglx works best with the intel chipsets... (at least in my experience)

---

### Post by Uncle Spellbinder on 2006-07-23
> **jstueve said:**
> aiglx works best with the intel chipsets... (at least in my experience)

I think I might give it a whirl. I've been checking out the [**COMPIZ**]("http://www.compiz.net/index.php") forums as well. Hope I don't bork anything. :)

---

### Post by andril on 2006-07-24
I followed the steps for Nvidia and I finally got the wobble effect, Alt+Tab, but I cannot change the themes or get the icon - can anyone help me ](*,)


I used the "compiz-start.py" method also but I can't get the Theme Selector field

---

### Post by east_lander on 2006-07-25
I think the new update is based on the cgwd decorator, so you need to ammend the compiz-start.py,which i'm not sure how

but can start compiz with themes based on the following

[http://www.ubuntuforums.org/showthread.php?p=1283090#post1283090](http://www.ubuntuforums.org/showthread.php?p=1283090#post1283090)

credits to lazyd2

---

### Post by dilidon on 2006-07-27
> **elv said:**
> Hey thanks for that, added the commands to the allscreens, was just using it in Screen0, and it worked like a charm =D>
I'm having the same shortcuts problem. Without a solution however, and its keeping me from using compiz as shortcuts are mandatory from an efficiency point of view. Everything else works like a charm.
Despite the fact that I also discovered that the commands and command keys were swapped like *jewishj* suggested, and I tried to play around with allscreens and Screen0 settings, no custom shortcuts seem to work. The keyboard layout used is correct. The ctrl, alt and shift keys all work on their own, and also, for example with the cube/rotate plugins, in combination.

Additional symptoms: When pressing, say, a combination ctrl+alt+a or ctrl+alt+g while the terminal window is active, it simply gives me the system bell notification. Also, when I wanted to reassing maximize window key from Alt+F10 to ALT+11 (only for testing purposes, to see, if compiz really gets the shortcuts from those key values in gconf at all) and then assign the previously working Alt+10 key to an application of my choice, the ALT+10 still kept maximizing the windows and ALT+F11 simply did nothing. That held true also after restarting compiz. Yet, the combination of ctrl+alt+p, which is assigned via the program options of Amarok, which I run under gnome, works - it pauses the playing song.:confused:

Could anyone offer any additional suggestions as to how to get the custom shortcuts including the ctrl+alt+del to work or have I missed something?

---

### Post by 3rdalbum on 2006-07-27
Sorry to change the subject, but if there are any XFCE users out there who want to run XGL and Compiz, I've added instructions to the appropriate wiki pages.

---

### Post by zxcvbnm on 2006-07-28
> I followed the steps for Nvidia and I finally got the wobble effect, Alt+Tab, but I cannot change the themes or get the icon - can anyone help me


I used the "compiz-start.py" method also but I can't get the Theme Selector field

Did you install cgwd? It's not in any of the official repositories so will have to get it from compiz's site. Then you will need to edit your execution script. Mine is in /usr/bin/startcompiz then once you have cgwd installed: Replace the script with this script:

```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd & 
compiz --replace gconf &
```

That is how I got my card but i have ATI I don't know if it is any different. 


Edit: Ah I justed noticed you did a different method. But I'm guessing the script is similiar. But what do i know :D

---

### Post by andril on 2006-07-29
I used the settings found here - I have the themes and settings working now. 

I am get confused on the things that should be loading in Sessions - I feel like it's partialy working corect.
Even the repos render errors

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

---

### Post by mcduck on 2006-07-31
> **zxcvbnm said:**
> Replace the script with this script:

```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd & 
compiz --replace gconf &
```

That is how I got my card but i have ATI I don't know if it is any different. 


Edit: Ah I justed noticed you did a different method. But I'm guessing the script is similiar. But what do i know :D
You should make it like this:
```
#!/bin/sh 
killall **cgwd** 
wait

cgwd & 
compiz --replace gconf &
```

---

### Post by riivo on 2006-08-01
has anybody gotten xgl or aiglx working on ibm thinkpad t30 (radeom 7500 16mb)?

---

### Post by IeU on 2006-08-02
i get this . . .
```

Get:17 http://au.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:18 http://au.archive.ubuntu.com dapper-updates/main Sources [44.6kB]
Get:19 http://au.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Fetched 251kB in 5s (43.7kB/s)
Reading package lists... Done
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures co uldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED 8A569E
W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97F ED8A569E
W: You may want to run apt-get update to correct these problems

```

---

### Post by Dr. Nick on 2006-08-03
gpg errors mean you dont have the key installed to authencitate the source

run
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -

found here
[http://xgl.compiz.info/](http://xgl.compiz.info/)

---

### Post by SonicTempest on 2006-08-03
I've been having some trouble with XGL+Compiz after I updated my kernel version to the latest version. The kernel can't "see" my Nvidia drivers (I have a GeForceFX Go 5200), so X fails to start when booting. The only way I've been able to fix it is to prevent glx from loading in xorg.conf.

I've tried uninstalling and reinstalling my Nvidia drivers, then reinstalling the Xgl and Compiz packages but it doesn't seem to have worked.

EDIT: Never mind, I just saw the thread about how the latest kernel update breaks a lot of stuff. Ergh...too bad security.ubuntu.com seems to be running rather slow for me atm.

---

### Post by den_ on 2006-08-04
For people with ati radeon cards who have problems with compiz (window borders disappear when compiz starts, compiz doesn't work at all and "compiz.real: GLX_EXT_texture from pixmap is missing" error). try to run compiz with sudo. I have made panel launcher which starts startcompiz script with gksudo and everything works fine.

First I tried to solve the problem with changing a link libGL.so.1 to mesa's libGL.so.1.2. I had to start session with libGL.so.1 pointing to ati's libGL.so.1.2 and then before launcing compiz i had to change it to points on mesa's libGL.so.1.2. Of course to have 3d acceleration again i had to set link on ati's libGL.so.1.2. I have noticed that when compiz alredy run I could change libGL.so.1 to point again on ati's libGL.so.1.2 and compiz will work further fine (probably becouse it is in RAM). 

I have edited the startcompiz script to change link on mesa's libGL.so.1.2, and then again on ati's libGL.so.1.2 but it couldn't work if I don'T start it with sudo and it make sense becouse root permission to create link in /usr/lib directory are needed. 

So I ran unintentional startcompiz script¹ from tutorial with sudo command and i noticed that it works : ).

¹ killall gnome-window-decorator
  wait
  gnome-window-decorator & DISPLAY=:1 LD_PRELOAD=/opt/mesa/libGL.so.1.2               compiz  -- replace  gconf 
  
I had to reinstall ati drivers after upgreding cgwd which anyway doesn't work.

---

### Post by Pathfinder_ on 2006-08-04
i can't install gcompizthemer and gcompizthemer-themes. it says 
```
The following packages have unmet dependencies:
  gcompizthemer: Depends: cgwd (>= 0.9) but it is not going to be installed
E: Broken packages 
```
but cgwd is already installed and is the right version. any help? 
i'm using these repositories
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

edit: nmd i just find out that gcompizthemer is built into cgwd

---

### Post by Rackerz on 2006-08-06
Can anybody help me with the shourtcuts to running the plugins? The water one doesn't seem to work anymore.

---

### Post by yossman on 2006-08-06
i can get cgwd 0.4 installed (with cgwd-themes), and i can run the cgwd themer from system -> preferences.  i see all the themes in there, but when i click on any of them, nothing happens.  from talking to people on IRC freenode.net #ubuntu-xgl, apparently you're just supposed to be able to click on any of the themes in cgwd and it's supposed to apply the theme immediately to your display.  

i have a desktop system that we configured last week; it is still using gcompizthemer and a strange 0.9 cgwd version, which i can't find anymore.  i tested the cgwd themer behaviour on it, and it applies the themes we click on on-the-fly like it should -- but it doesn't work on the same on this laptop we're trying to configure.  nothing happens when we click on themes in cgwd 0.4.  the major difference here is last week we were able to install gcompizthemer and cgwd and everything worked fine, now this week it doesn't (cgwd 0.9 not available when we tried to install gcompizthemer on the laptop).

is there some debug output i can view to see if there is an error being generated every time i click a theme?  so far, no hints that i can find as to why nothing happens..?  i certainly will not be hitting 'upgrade' on the desktop ubuntu at this time, since it's working awesome on that machine and  i don't want it to mysteriously break theme support after upgrading, like what seems to have happened on the laptop. ;(



EDIT: i got it working with the help of freenode.net #ubuntu-xgl (thanks section12! ;).  the problem was gnome-window-decorator was still being run, instead of cgwd.  my startup script for triggering compiz was originally like this:

```

#!/bin/bash
gnome-window-decorator &
compiz --replace gconf decoration wobbly [....]

```

ripping out 'gnome-window-decorator &' and replacing that line with 'cgwd &' seems to have worked awesome, now i click themes in cgwd themer and they change like they're supposed to, without any slowness too.  my script now looks like this in case i want to restart it again and again:

```

#!/bin/bash
killall cgwd
wait
cgwd --replace &
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

```

i still get warnings about 'cannot open pixmap: shade' and other theme-related images not found, but these are small errors that i can live with, since everything else seems to work great now.

btw, i keep hitting shift-backspace while i'm in terminal, which shuts down X right now (geez), but i've read this is a known bug and it's being fixed.


yossman

---

### Post by one_stinky_bum on 2006-08-07
Does edge flip now work? The checkbox unsets itself when I set the properties under Plugins->Rotate
Edit: I'm running compiz-vanilla-aiglx(0.0.13-0ubuntu2)+gset-compiz(0.3.4-3v1ubuntu3)+cgwd(0.4) on 6.06 LTS with a puny i915 chip.

---

### Post by one_stinky_bum on 2006-08-07
Nevermind: just use ght gconf-editor. The preferences-> plugins-> rotate pane doesn't work for me, but I now have edge flipping by doing this:

> **matthinckley said:**
> In gconf-editor under /apps/compiz/plugins/rotate/screen0/options  there is a key called edge_flip.  check this.

Thanks. The bum shall now go take a shower and do a victory dance.

---

### Post by peabody on 2006-08-07
I had the missing borders problem with my xgl/compiz setup for quite some time.  I have fixed the problem however.  I'm running the fglrx ati drivers version 8.27.10.  I followed the instructions to a t at [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) and was able to get compiz working this way but I had to continually run the startcompiz script until compiz finally decided to work.  Launching the script just once didn't work and left my windows without borders.  It seemed to work completely randomly; sometimes it would work right away, other times I needed to launch the script more than 20 times.  Continual research led me to the following thread:

[http://www.compiz.net/topic-389-18.html](http://www.compiz.net/topic-389-18.html)

which led me to a post that said to downgrade the xgl server to solve the problem.  I did that and it worked.  The url to the deb is here:

[http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb](http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb)

you'll then want to pin that deb so it isn't upgraded by apt.  Create a file called /etc/apt/preferences and put the following in it:

```

Package: xserver-xgl
Pin: version 7.0.0-0ubuntu2
Pin-Priority: 1001

```

This will prevent xgl from being updated by apt-get upgrade.  Xgl/compiz seems to work flawlessly for me now.

---

### Post by m0unds on 2006-08-07
Compiz/XGL eyecandy is neat. My laptop didn't like it very much, though-- compiz crashed every time I tried to use it..(kubuntu 6.06) but in ubuntu..no problems.

---

### Post by TJGuitarZ on 2006-08-07
Hey guys, sorry to add again to the overwhelming large number of replies, but I have no where else to turn :sad: 

I put in everything following the directions for nvidia cards. When I rebooted, I got the same problem I did the first time. This is the basic thing it said.

1. Failed to start the X server.
2. Install the X server or correct GDM configuration and restart GDM.
3. X Server disabled.

It then takes me to something like the terminal. When I type in "thefuture" as I am supposed to to start it all up, it says...
1. /usr/bin/thefuture: line 2: gnome-window-decorator: command not found
2. /usr/bin/thefuture: line 2: compiz: command not found

... I'm not sure what I'm supposed to do. Any ideas guys?

---

### Post by Odice on 2006-08-11
> **Pathfinder_ said:**
> i can't install gcompizthemer and gcompizthemer-themes. it says 
```
The following packages have unmet dependencies:
  gcompizthemer: Depends: cgwd (>= 0.9) but it is not going to be installed
E: Broken packages 
```
but cgwd is already installed and is the right version. any help? 
i'm using these repositories
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

edit: nmd i just find out that gcompizthemer is built into cgwd

Im having the same problems, with the same repositories, and when y make a sudo apt-get update, it says that those repositories are ignored.

---

### Post by Weav on 2006-08-11
cgwd is included in gcompizthemer so no need to worry about it.

On a seperate thought, my XGL computer now rotates the cube from the inside of the cube instead of from the outside of the cube. Whenever I turn the cube it appears as if I'm actually inside the cube.

Any ideas how to change it back? Thanks

---

### Post by Rinnan on 2006-08-11
Hello.  Well, I promised myself that I would not get obsessed with XGL, and if I couldn't get it working after an hour or so I would give up, and patiently await OS updates or whatever was needed to get it running easily.

Now that I've broken (more like *shattered*) that promise, let's continue...

I have an Acer laptop with a 945GM chipset.  It works perfectly with the Kororaa XGL LiveCD 0.2, if you change the "Device" setting in the Driver section of the xorg.conf from "i915", to "i810" and restart gdm.

Discovering that it can be made to work, flawlessly, smoothly, beautifully with all features (even the nifty Matrix-GL overlay!) has of course, greatly intensified my pain.

As you might have guessed, I can't get it to work on Ubuntu for blood or money, after many fruitless hours of work.

It gets to the point (after following the instructions in the starter thread) where it seems like it *ought* to be working, but it doesn't.  No window decorations, and manually running "gnome-window-decorations" gives me an error.

Direct Rendering is "Yes", even with an unmodified Dapper.  And my xorg.conf looks like Kororaa's, or many of the other xorg.conf's posted here.  I just can't get any further.

Is there someone else with a 945GM who has got this working?  How?

Erik

---

### Post by Flipper on 2006-08-11
Hi all, i have the eyecandy working, transparency / "expose like " / bubles / windows bouncing.. 

But NO CUBE, ZOOM, RESIZE :\ im running dapper with latest updates, latest  nvidia driver in a GF 6800GS PCI-E.

can anyone help? btw Where is the gset-compiz ?????? i have the repos but i cant find the package!!!!

i believe XGL is not running well :\ oh and when i start compiz, i lose my "workspaces" i normally use 4 but it reduces to 1 :\

---

### Post by Megaqwerty on 2006-08-11
I know I am doing something wrong, but when I do: sudo gedit /etc/X11/xorg.conf, (I enter my password) nothing pops up. 
I have installed the latest Nvidia Driver per instructions...what am I doing wrong?

---

### Post by Dr. Nick on 2006-08-12
> **Weav said:**
> 

On a seperate thought, my XGL computer now rotates the cube from the inside of the cube instead of from the outside of the cube. Whenever I turn the cube it appears as if I'm actually inside the cube.

Any ideas how to change it back? Thanks

In gset-compiz go to plugins - cube and uncheck "inside the cube"

> **Flipper said:**
> Hi all, i have the eyecandy working, transparency / "expose like " / bubles / windows bouncing.. 

But NO CUBE, ZOOM, RESIZE :\ im running dapper with latest updates, latest  nvidia driver in a GF 6800GS PCI-E.

can anyone help? btw Where is the gset-compiz ?????? i have the repos but i cant find the package!!!!

i believe XGL is not running well :\ oh and when i start compiz, i lose my "workspaces" i normally use 4 but it reduces to 1 :\

Mine stays 4 workspaces, gset-compiz is the package name in the repos. here is my sources.list for xgl/compiz

```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```


> **Megaqwerty said:**
> I know I am doing something wrong, but when I do: sudo gedit /etc/X11/xorg.conf, (I enter my password) nothing pops up. 
I have installed the latest Nvidia Driver per instructions...what am I doing wrong?

Do you have gedit? you can try nano instead

sudo nano /etc/X11/xorg.conf

---

### Post by Flipper on 2006-08-12
I removed all the repos and copy / paste yours in my sources.list
Check what happens!
Did they remove the gset-compiz from the repos????

```
flint@Flint:~$ sudo apt-get update
Get:1 http://xgl.compiz.info dapper Release.gpg [189B]
Hit http://xgl.compiz.info dapper Release
Ign http://xgl.compiz.info dapper/main Packages
Get:2 http://xgl.compiz.info dapper/main Packages [12.7kB]
Get:3 http://www.beerorkid.com dapper Release.gpg [189B]
Hit http://www.beerorkid.com dapper Release
Ign http://www.beerorkid.com dapper/main Packages
Hit http://www.beerorkid.com dapper/main Packages
Fetched 12.7kB in 1s (6414B/s)
Reading package lists... Done
flint@Flint:~$ sudo apt-get install gset-compiz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gset-compiz

```

Why cant i have the cube effect? :(

---

### Post by phetre on 2006-08-12
Yeah, same here!  I actually had a working installation earlier this week, but when I tried to upgrade from vanilla to quinn, I ran into exactly the same problem.
Does anybody now how to resolve this?  I couldn't even find a .deb file of gset-compiz to download.

[EDIT:] Oops, I should have checked just a bit longer before posting!  There's a .deb available here: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/). And in case that goes down, I’ll host it on my space for a while: [http://home.uchicago.edu/~pashultz/gset-compiz_0.3.4-3v1ubuntu3_i386.deb](http://home.uchicago.edu/~pashultz/gset-compiz_0.3.4-3v1ubuntu3_i386.deb)  If you're using Dapper, you can just double-click on the file once you're downloaded it.
Hope this helps!

---

### Post by Dr. Nick on 2006-08-12
> **Flipper said:**
> I removed all the repos and copy / paste yours in my sources.list
Check what happens!
Did they remove the gset-compiz from the repos????
  


Just to be clear, that wanst my entire sources.list, only what pertained to xgl/compiz

Im not sure why gset-compiz isnt thier for you, its still in the repo for me.

---

### Post by Megaqwerty on 2006-08-12
That did it, Thanks

---

### Post by Hotaru on 2006-08-13
> **Rinnan said:**
> 
Is there someone else with a 945GM who has got this working?  How?
Erik
I have gma900 graphics chipset on my laptop and it's working smoothly, no problems at all. The only difference is that I'm using compiz with AIGLX, not XGL, because I've heard that 945GM has better performance in AIGLX.
I used this HOW-TO to get this going: [http://www.ubuntuforums.org/showthread.php?t=145068]("http://www.ubuntuforums.org/showthread.php?t=145068")

Hope that helps and good luck! :)

---

### Post by mobin on 2006-08-14
If anyone is having problems getting Control+Alt+Delete to open the System Monitor then try this. The method mentioned in this thread didn't work for me. Type these two commands into a terminal.

gconftool-2 --set --type string /apps/compiz/general/allscreens/options/command1 "gnome-system-monitor"


gconftool-2 --set --type string /apps/compiz/general/allscreens/options/run_command1_key "<Control><Alt>Delete"

---

### Post by quad3d@work on 2006-08-14
Works great, VMWare fullscreen works as well (mods required). Thanks for the great guide!

---

### Post by GhostDawg on 2006-08-15
I tried installing xgl/compiz on 6.6.0.1 and things didn't go good. It seems that nVidia didn't install, now I can only log in from the text screen, gdm broke. I followed the unofficial guide on installing it. Also when I run glxgears its not working.

I'm at work at this moment but if anybody know of a thread that explains how to fix things, I would appreciate it. 

I had to change the xorg.conf file from 'nvidia' back to 'nv' to be able to get back into ubuntu.

I'm using an AMD XP 1700, 1.2ghz, with nVidia FX 5200 card, 768mb of ram.

Thnx.

---

### Post by eljaco on 2006-08-15
I have a really annoying problem: whenever I turn my computer on, I get the command line login, instead of the Ubuntu GUI login. In order for me to get to the GUI, I have to go into /etc/init.d and then run
> sudo gdm stop
so that X will start. Everything except for water seems to be working after that. I would like to know how to solve this problem and what may be causing it. I am using Dapper (x86) with a NV GeForce 4400 Go AGP x8.

This is my gdm.conf-custom file:
```

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
# 
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
# 
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
# 
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
# 
# NOTE: Lines that begin with "#" are considered comments.
# 
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]# Override display 1 to use Xgl
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true


```

Used the > Xgl/compiz on an Nvidia video card
and also ran the things that I saw were different in > Xgl/compiz on an Nvidia video card with KDE since I used to use KDE a lot before. Now that I am off that and using GNOME full time, I only care about XGL on GNOME. Could this have any effects? When I boot up, I get the blue KUBUNTU loading page, which I would like to change to the old UBUNTU one, but don't know how. This could potentially be the problem, but I don't see why. I ran Synaptic and tried to remove everything KDE and KUBUNTU and still got the blue KUBUNTU Loading thing when I booted up.

Thanks so much!

If you need anything else, let me know.

---

### Post by mattlach on 2006-08-16
*double post due to lag*

---

### Post by mattlach on 2006-08-16
Hey...

So I have searched the forums and google without coming up with anything.  I was hoping one of you might have an answer for me.

I am suffering from the white screen (bad refresh) bug.  Everyone in past posts keep suggesting that it is due to outdated packages, but to my knowledge everything I have is new.

I am on an AMD64 system with a GeForce 6800GT.

My sources.list
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.systemadministrator.org dapper eyecandy
deb http://ubuntu.moshen.de/ dapper all
deb http://xgl.compiz.info/ dapper main

```

Versions installed:
compiz-gnome 0.0.13-0quinn31
compiz  0.0.13-0quinn31
cgwd  0.53
xserver-xgl  7.0.0cvs20060625
libglitz-glx1  0.5.6-0ubuntu1
nvidia-kernel 20051028+1
nvidia-glx  1.0.8762+2.6.15.11-3

I have tried everything, including removing comiz-gnome and trying compiz-vanilla without any success.  The white refresh error still remains.

Does anyone have any idea why I am having this problem?

Thanks,
Matt

---

### Post by napsy on 2006-08-17
Hello.
Scrolling is very slow when I'm running XGL and compiz. Is there a way to speed up scrolling?
And how to disable the wobbly effect when minimizing/maximizing windows?

---

### Post by tcollogne on 2006-08-18
I also have a strange problem. When I open an application, that opens maximized (for example firefox), a little part of the screen falls of on the right side. 
When I click inside the window, the screen resizes to the correct size. Does anyone one what could be causing this?

---

### Post by flankker on 2006-08-20
the blur plugin is almost unusable for me, it makes everything extreamly slow. is there anything i can do about it? thanx.

---

### Post by shanepardue on 2006-08-20
so i installed this on an additional session just in case i didn't like it. now i have no shutdown/restart buttons...i've heard the fix is to install  it  on the gnome session. how would i do this?

thanks!

---

### Post by manager48_2000 on 2006-08-21
I'm having the same problem with the title bar disappearing when compiz is started.  was going to try to downgrade my xgl, but the link posted is a 404 ...anyone with more information on that?

---

### Post by Hotaru on 2006-08-21
> **Uncle Spellbinder said:**
> If it's not been mentioned yet, Use: 

*deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx*
or
*deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx*
Or both.


DO NOT....I repeat... [color=#CC0000]**DO NOT**[/color] add **ubuntu.compiz.net** or **xgl.compiz.info** to your sources list. 

Or at least comment them out if you insist on adding them.


See here:  [**_Community Compiz+etc. Packages_**](http://www.beerorkid.com/compiz/)

Worked for me :).

---

### Post by DeemanXu on 2006-08-21
ermmm, in need of a bit of assistance.

I've installed XGL this morning on my machine via the wonderful magic that is Automatix Bleeder. As far as i can see, the install went ok.
The trouble is that when i come to login to my system using XGL as my session, i get as far as the splash screen ( which incidentally is just a brown background, and nothing else ), it hangs for 10 seconds, then mysteriously goes back to the login screen. 

This is quite a recent install of Ubuntu ( had a play with Kubuntu and hated it ! ), and i used Automatix to install my Nvidia drivers for GeForce 5200FX card. Please someone for the love of God put me out of my damn misery ( and i don't mean by popping a spear through my head, either :D ).

DeemanXu ](*,)

***UPDATE***

Issue now resolved. As unthinkable as it may seem, and just as laughable, i didn't have the correct keys :oops: . 

I finally got it all installed by installing everything to do with XGL/Compiz manually ( .deb packages from repositories ). That seemed to do the trick, now everything is lovely, and i have Compiz beautification upon my even-more-so beloved Ubuntu Linux Desktop.

Windows can kiss my arse now :cool:

---

### Post by kelcey_s on 2006-08-21
DeemanXu, could you tell me exactly what you did because I have the same problem. It worked at first but now it just goes back to the login screen.

Also I wonder if anyone might know if installing Xgl/compix is the reason why my gdm won't work anymore (luckily the day before I installed KDE so I can use kdm to login to any session)

---

### Post by frup on 2006-08-22
I had quite alot of trouble getting this to work with all the tutorials that edit xorg.conf and gdm.conf-custom (broken xserver and all). 

This one here though doesnt require any of that and allows you test it for just one session too!

[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

its devided in to three parts... getting the proprietry drivers... what seems to be an advertisement for automatix (to make ubuntu even better for newbies) and then the final comparitivly simple XGL/Compiz installation :) 

Now i just have to get these stupid themes on cgwd to work properlly!

---

### Post by DeemanXu on 2006-08-22
Hi Kelcey.

I understand your pain as far as XGL is concerned. For some, it's a relatively easy process, whilst for others like you and myself, it's somewhat a ferocious beast to handle. Many a day i spent messing about trying to get this damn thing to work, but let me tell you, it is very rewarding and worthwhile.

Firstly, i added these repositories to my sources list (sudo gedit /etc/apt/sources.list) :

```
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://ubuntu.compiz.net/ dapper main
``` 

Then, i obtained the keys for the newly acquired repositories:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -
```

Then, i downloaded these files via Terminal:

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```

Next, comes a bit of editing the xorg.conf.

Find the “Module” section. Comment out the “Glcore” and “dri “ modules and make sure a “glx” module is there. So basically like this:

```

#       Load    "GLcore"
#       Load    "dri" 
         Load "glx"

```

Now find the “Devices” section.

Change every line but the “Identifier” line to look just like mine:

```

Section "Device"
	Identifier- leave this line alone!
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
EndSection

```
(N.B: I left out the BusID as i found that this was one of the problems that caused my xserver to crash - try with, or without, see what works.)

Next:

IF LATER ON COMPIZ DOES NOT WORK FOR YOU (and complains about composite extension):

Add this to the very bottom:

```

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```
( This i had no need for to be honest, but, i tried it anyway, and this also crashed my xserver. So, i had to edit on reboot. sudo -s then enter your password. Then pico /etc/X11/xorg.conf to remove the above code. to save press Escape key twice then O, and to exit press escape key twice then X, then type reboot)

Right, after all that i installed XGL/Compiz via Automatix Bleeder:

```
sudo apt-get install automatixbleeder
```

Installed XGL/Compiz from there, rebooted, chose XGL as session from gdm ( it should be there at kdm too ). After it loads up, go into a terminal and type:

```
toggle-compiz-nividia
```

I know to some of you this may look like taking the longest route round, but, it worked for me straight away. This is just one of many ways i suppose.

(Special thanks to PoofyHairyGuy as i've used parts of his tutorial).

---

### Post by CamB on 2006-08-22
I've got a hopefully quick/easy question...

I've had XGL/Compiz working fine, including sorting out keyboard shortcuts. Last night I thought I'd try upgrade and install cgwd + some themes.

I've got that working, subject to 3 problems. The first two (shortcuts no longer working and <Alt>-Tab not working properly) I think I have found how to fix (at work now - try when I get home). The 3rd prob I'd like some help with.

The Ubuntu splash screen showing the items loading (Window Manager, Update Notifier, Skype, gKrellm etc - the items set to load with the session) is stalling - it stays on the screen for several minutes before gkrellm and the update notifier finally load. I assume that this is because either:

1) the script I'm loading cgwd and compiz with has an error that needs to time out; or

2) gnome is waiting for a window manager and doesn't "get" one, and I have to wait while it times out.

Any ideas on a fix or how to better troubleshoot? Thanks!

---

### Post by frup on 2006-08-23
I'm begining to feel a bit sick with all the wobbling hahah! its ok but i would like to turn it down a bit (shorter and slower shift f10 makes it last too long)

Also every menu and on mouseover message is wobbling too... i think its just a bit too much... also the gdesklets i just downloaded are getting supid shadows all over them when i want them transparent... i only wanted this for the glass and the cube

---

### Post by eightmile on 2006-08-23
I've just updated compiz and now I got the wobbling menus back.. :( How to disable them?

---

### Post by CamB on 2006-08-24
> **CamB said:**
> The Ubuntu splash screen showing the items loading (Window Manager, Update Notifier, Skype, gKrellm etc - the items set to load with the session) is stalling - it stays on the screen for several minutes before gkrellm and the update notifier finally load. I assume that this is because either:

1) the script I'm loading cgwd and compiz with has an error that needs to time out; or

2) gnome is waiting for a window manager and doesn't "get" one, and I have to wait while it times out.

Any ideas on a fix or how to better troubleshoot? Thanks!

I managed to resolve this on my own (yay me).

I run Compiz as a session, selected on the login screen. This means a script is executed as set out below. The important addition was on the end of gnome-session which shortens the wait time on whatever isn't responding.

```
#!/bin/sh

xmodmap /usr/share/xmodmap/xmodmap.us_intl_mod

LIBMESA=/opt/mesa/lib

LD_LIBRARY_PATH=/opt/mesa/lib /usr/bin/cgwd --replace &
LD_LIBRARY_PATH=/opt/mesa/lib /usr/bin/compiz --replace gconf &

exec gnome-session --purge-delay=5000
```

---

### Post by chokes on 2006-08-25
hi all :) my how to should fit in this tread because i think it the easyest way to get Xgl working.... so my how to is here :[http://www.ubuntuforums.org/showthread.php?t=225141](http://www.ubuntuforums.org/showthread.php?t=225141)

I use the quins packages so it have updates almost all days :)

Edit: i almost forgoten... my how to no need a script to start compiz i use gnome-compiz-manager

---

### Post by sergo on 2006-08-25
when i move my mouse or open a new window it shakes my sound as well
someone with the same problem?

SB Live 5.1/ ALSA

---

### Post by chokes on 2006-08-25
someone can let me know if my HOWTO should be in this thread ?

---

### Post by mindtrick on 2006-08-27
I have a video card named VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter___ 

Can't I use xgl or compiz?

---

### Post by chokes on 2006-08-28
if you have opengl working maybe yes... and you can try aiglx it have indirect riendering;)

---

### Post by orbital on 2006-08-29
I use Dapper with Xgl/Compiz and everything's been working great, but now there's something wrong with my ethernet connection and the detection of my network card. I don't have internet access at all (with Windows no problems connecting) and dmesg gives me a bunch of lines like these:

[17179658.148000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179658.148000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xeb891a40 for 516096 bytes
[17179658.148000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xaa4b2000 for 819200 bytes
[17179658.152000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179658.152000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xeb891a00 for 819200 bytes
[17179662.376000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xa9686000 for 3768320 bytes
[17179662.388000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179662.388000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf3ca8600 for 3768320 bytes
[17179666.200000] r8169: eth0: link down
[17179671.768000] r8169: eth0: link up
[17179674.076000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0x08d3f000 for 57344 bytes
[17179674.076000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179674.076000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xdf8f2980 for 57344 bytes
[17179674.576000] [fglrx:firegl_pcie_lock_pages] *ERROR* locking memory at 0xaa550000 for 172032 bytes
[17179674.576000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17179674.576000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf4ee4180 for 172032 bytes

Any ideas what's the problem and what to do?

---

### Post by peanutplanters on 2006-08-29
is it possible to flip the compiz cube while running VMPlayer fullscreen?

---

### Post by nilsh on 2006-08-30
I have now installed compiz, but have some difficulties. When I start Ubuntu everything works great. But when I try to load preferences or theme selector from the systray menu I get these errors in terminal :

```
Traceback (most recent call last):
  File "/usr/bin/compiz-start.py", line 33, in configure_menu_activate
    gobject.spawn_async(['gset-compiz'], flags=gobject.SPAWN_SEARCH_PATH)
gobject.GError: Failed to execute child process "gset-compiz" (No such file or directory)
Traceback (most recent call last):
  File "/usr/bin/compiz-start.py", line 36, in gcompizthemer_menu_activate
    gobject.spawn_async(['gcompizthemer'], flags=gobject.SPAWN_SEARCH_PATH)
gobject.GError: Failed to execute child process "gcompizthemer" (No such file or directory)
```

Have I installed compiz the wrong way?

---

### Post by Servus on 2006-08-31
Hi 
cgwd starts randomly. I have to run several times startcompiz in order to make window borders appear. It seems the same problem of page 37 in this thread. Solution proposed: downgrade to a previous version of xserver-xgl,but the link [http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb](http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb)
does not work anymore and I cannot find this package.
Could someone help me to find this package? You could post it or send me by mail.
Thanks a lot!!

---

### Post by Flavian on 2006-08-31
This is question seems to me a little dumb, I am sorry...
but I know there is two ways of configuring XGL/Compiz
The easy and the advanced way.
The easy way is "gnome-compiz-preferences" and the advanced way I can not remember!

Can somone help me? - I want to customize compiz a little more than the basics. And I already made some changes in there, I can't find the command though to get in the gui :(

Thanks in advance!
Flo

---

### Post by ~LoKe on 2006-08-31
**Easy:** GSet-Compiz
**Advanced:** gconf-editor

---

### Post by testube_babies on 2006-08-31
> **~LoKe said:**
> **Easy:** GSet-Compiz
**Advanced:** gconf-editor

gset-compiz is out of date.  You need to go to /apps/compiz in gconf-editor.

---

### Post by wilsonad on 2006-08-31
> Um, using the guide for the AMD64 version (from pdc303) of compiz, I would like to know how to load more plugins than the default ones. I want to load widget, water and dock.

I tried using a guide from compiz.net forums, on how to order plugins and it didn't work, because they said it's according which version of compiz you're running. Everytime I tried to load a plugin through gconf-editor it would dissapear after I pressed OK. From what I saw at the HOW-TO pdc303 uses a compiled version of his own and not a default one, so is there a way to load these additional plugins?

I am having the exact same problem with my installation. After following the **HOWTO: Xgl + Compiz on AMD64 (Easy / Packages)** guide here:
[http://ubuntuforums.org/showthread.php?t=133427](http://ubuntuforums.org/showthread.php?t=133427)

It seems there is no water plugin, has anyone figured out how to add this functionality?

I even tried using gnome-compiz-manager, but even when I would enable it in this it would not work.

The water plugin is included in this package:
[http://xgl.compiz.info/pool/main-amd64/c/compiz-plugins/compiz-plugins_0.4-0ubuntu1_amd64.deb](http://xgl.compiz.info/pool/main-amd64/c/compiz-plugins/compiz-plugins_0.4-0ubuntu1_amd64.deb)
but the way compiz was installed only separate plugins were installed and not compiz-core.  Is there a way to just install this one plugin??

---

### Post by aleska on 2006-09-01
Sorry in advance if this has already been noted in this thread, but Stian Karlsen's updated Ubuntu tutorial for enabling XGL/Compiz is incredibly easy to follow, and it just works.  For me at least.  
[http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/](http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/)

I know everyone is pointing to YouTube videos for demonstartions, but here's a [cool screenshot]("http://www.skarulis.com/?p=29") I took in case anyone wants to share with others.  I just loaded XGL/Compiz this evening and I'm truly blown away!

---

### Post by Flavian on 2006-09-01
> **testube_babies said:**
> gset-compiz is out of date.  You need to go to /apps/compiz in gconf-editor.

Dang it, I am SO sure there was a GUI for this... A more gui like thing than the gconf editor.
Why am I so dumb, not to find that thing :( ?

---

### Post by wilsonad on 2006-09-02
aleska -  Are you running the amd64 ubuntu?

For some reason at least from what I have been reading the articles on justpretending.net were not working for the amd64 users including myself.

---

### Post by general_error on 2006-09-02
I've got Compiz/XGL installed on Ubuntu, but got no dock.

When I go into gconf-editor and try to add dock to the list of plugins to load it just vanishes when I click ok.

Am I doing something wrong?

---

### Post by obi-nine on 2006-09-08
Just to let you know... there is now an updated guide to installing AIGLX on the i915 chipset, on the Compiz wiki:

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

Perhaps you could change the link on the first message...

obi9

---

### Post by flankker on 2006-09-08
guys just to clarify both gset-compiz and gconf-editor have been replaced by "csm" which can be installed by "sudo aptitude install csm"

csm is very user friendly and has all the compiz options.

---

### Post by ButteBlues on 2006-09-09
The Ubuntu wiki needs to be updated to note that with Quinn's new packages, creating your own script is now deprecated due to the compiz-start script created by installing her packages.

---

### Post by raven65az on 2006-09-15
well,.I either messed up, or missed something.
I used the latest repository for compiz, and installed all the necessaries that I'm aware of...but upon reboot, its not running.  Here is my .Xsession error log.  Hopefully someone can advise me on what I can change.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "raven"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'raven' found
SESSION_MANAGER=local/raven-laptop:/tmp/.ICE-unix/5060
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...

(gnome-panel:5385): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_set_size: assertion `width >= 0 && height >= 0' failed

(gnome-panel:5385): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5385): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 25
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Initializing nautilus-open-terminal extension
seahorse nautilus module initialized
--sm-config-prefix: unknown option

Usage: gnubiff [OPTION...]

General command line options:
  -c, --config=file     Configuration file to use
  -n, --noconfigure     Skip the configuration process
  -v, --version         Print version information and exit

Help options:
  -?, --help            Show this help message
  --usage               Display brief usage message
Link points to "/tmp/ksocket-raven"
Link points to "/tmp/kde-raven"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Uh oh.. can't write data..
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2400085
compiz: No composite extension
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error
WARNING: DCOPReply<>: cast to 'QString' error

Thank you all in advance for your help...I truly appreciate it!

Scott

---

### Post by BLTicklemonster on 2006-09-19
Bleh:

> ticklemonster@ticklemonster:~$ compiz-start.py
Traceback (most recent call last):
  File "/usr/bin/compiz-start.py", line 81, in ?
    pixbuf = gtk.gdk.pixbuf_new_from_file("/usr/share/compiz/logo24.png")
gobject.GError: Failed to open file '/usr/share/compiz/logo24.png': No such file or directory


---

### Post by nero2150 on 2006-09-20
I have install the new compiz package and theme cwgd but 
when Im in xwindow it does not respond to any of my clicks :confused: 

also when i drag the cursor it save a picture file on my desktop of the 
inside of the drag area of the the mouse. I use to have the old compiz themer
but i took everything off and reinstall. 
I doing just like on the HOWto here the 2nd method

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

If someone could help plz .... :cool: 
Thanx

---

### Post by tehkain on 2006-10-09
Well I followed [this guide  ]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit")and this is the result when I start beryl.
]
> XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension



Any ideas?

Xgl yeilds

> Xgl

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

/etc/gdm/gdm.conf-custom
> # GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

xorg.conf
> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection




I am on a Nvidia card by the way.

---

### Post by PriceChild on 2006-10-10
Hey all.
I just thought i'd mention that this thread is EXTREMELY outdated.
There is another sticky in this forum: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)
With more up to date howtos (nothing pointing to dapper dev forums etc.)

Pricey

---

### Post by Perfect Storm on 2006-10-10
This thread will be closed for further discussion.

---

