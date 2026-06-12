---
title: "ATI Radeon 9000 and Ubuntu 9.10"
date: 2009-10-29
forum: General Help
---

### Post by Jimmyguns on 2009-10-29
Hey guys, definately a new linux user here.  I have just finished installing 9.10 on a Latitude D600 with  Mobile Radeon 9000 video card.  I log in ok using gnome but when ever i try to open any app or anything that brings up the admin pw prompt the machine locks up and i have to do a hard shutdown. I am currently running the machine fine under the failsafe gnome option.

 I really don't even know where to being troubleshooting this as up until now i have been a windows user.  After doing quite a bit of poking around I realize that getting this particular ATI card to function properly can be quite a task.  

Most of the solutions being recommended that I have come across involve editing the xorg.conf file.  I don't really understand where this information is stored in 9.10 because it appears things have changed quite a bit.  

Basically I'm looking for a good walkthrough on troubleshooting video issues in ubuntu, commands to view current settings, change drivers, etc.  Also appreciated would be a some info regarding required packages and what exactly the packages do.

Anyone else having difficulty with this particular laptop model or video card out there that can shed some light on things?

Thanks for your time!

---

### Post by Giblet5 on 2009-10-29
I don't have a Radeon but the consensus seems to be that is a driver issue, and if you change the Device section of xorg.conf, that will "fix" it.

Open a terminal window (Applications -> Accessories -> Terminal) and enter the following commands:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

Look for the Device section and change the entire section to this ```
Section "Device"
 Identifier "ATI Radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic" "greedy"
 Option "AccelDFS" "true"
 Option "EnablePageFlip" "true"
 Option "EnableDepthMoves" "true"
EndSection
```

Then scroll down to the "Screen" section and change the Device value to "ATI Radeon".

Save it and exit gedit.

Now enter (in the terminal) ```
/etc/init.d/gdm restart
```

That will log you off and restart the Xorg server, picking up the new settings.

Does that fix it?

---

### Post by Jimmyguns on 2009-10-29
Thanks for the reply.  As I mentioned before (I know it was a long post and some points may have gotten lost) the xorg.conf file doesn't exist in the fresh install of 9.10 from the live CD.  I think they have changed how the config is stored or it is created on the fly or something.  I did, however, create one and inserted the code you mentioned.  Upon logging in there was alot of strange artifacting and it eventually locked up and I was forced to pull the plug.

---

### Post by Giblet5 on 2009-10-29
It's used if it's there... :/

Here's a complete xorg.conf that should work 
```
Section "Device"
        Identifier "ATI Radeon"
        Driver "ati"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device          "ATI Radeon"
	DefaultDepth	24
EndSection
```

Use the code from before to gedit xorg.conf, copy/paste that in, overwriting everything. Save it, then restart X as before.

If it still doesn't work, just remove the new xorg.conf cuz it ain't helpin'.

---

### Post by kevanj on 2009-11-02
Thanks Giblet5...

your solution worked for me using the same system as the OP. My installation was an upgrade from Jaunty which had what I guess was a 'default' xorg.conf. Replacing it with your version worked a treat.

---

### Post by toulousain on 2009-11-03
Well, this solution did not work for me. But finally I found a workaround that works well. I cannot activate compiz, but it's useless for me at the moment.

I installed Ubuntu 9.10 from scratch, from a CD, on my D600 and I got some freezes just after login (and some time even before the login!). It was completely random. I had a look at this post and tried this solution. There was no /etc/X11/xorg.conf after the install. I created one with the config mentioned above, I restarted the X server and the PC several times but it did not fix the issue. It was still freezing... And I had new issues with the display that was not well refreshed.

Finally I decided to install the Catalyst proprietary driver and it fixed the problem.

I downloaded the driver from here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)

Then in a terminal (Applications -> Accessories -> Terminal) I executed the following command from where I downloaded the driver:

```
sudo ./ati-driver-installer-9-10-x86.x86_64.run --buildandinstallpkg
```I accepted the installation of the new packages. Everything ran well during the installation.

Important: when the installation complete I deleted the file /etc/X11/xorg.conf I created above.

```
sudo rm /etc/X11/xorg.conf
```Finally I restarted my PC and it fixed all my problems.

---

### Post by nomnex on 2009-11-03
@toulousain,

I am looking for the proprietary driver for my ATI Radeon 9000 on a Fujitsu notebook (I use Jaunty), where did you find yours - the full web site address please.

Your driver seems different than those available there: [http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

To anyone: on the official ATI page (link above), there are 3 download options (2 seems identicals - the XFree 86)
Option a (one choice):
- XFree 86 4.3 Drivers
Option b (two choices):
- XFree68 4.3 Drivers
- X.Org 6.8 Drivers

What's the one for Ubuntu 9.04/9.10? Thanks

---

### Post by nomnex on 2009-11-03
Update: I found the link [http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)

But I am still unsure of the proper driver to choose, the on in the link above (see: toulousain post) or the ones in my previous post.

---

### Post by jocko on 2009-11-03
> **nomnex said:**
> Update: I found the link [http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)

But I am still unsure of the proper driver to choose, the on in the link above (see: toulousain post) or the ones in my previous post.
You already have the proper driver (the open source driver named radeon) installed and used by default. The proprietary driver (fglrx/catalyst) does not support your card.

---

### Post by nomnex on 2009-11-03
thanks jocko

not sure if I am hijacking this thread? ATI radeon 9000 on notebook Fujitsu and Jaunty 9.04: the rendering is not good (it is a bit dark and it lacks shinning) and the frame rate is too low (windows break when I move them on the screen).

Display is 1400 x 1050 (4:3) SXGA [http://www.fmworld.net/product/hard/pcpm0305/biblo_loox/nh/index.html](http://www.fmworld.net/product/hard/pcpm0305/biblo_loox/nh/index.html)

1) How do I fix it - by editing the xorg file as above with the same value?

2) The second notebook as an ATI radeon 9200, can I use the fglrx/catalyst driver? Advice.

---

### Post by nomnex on 2009-11-03
Edit: Please check this thread [http://swiss.ubuntuforums.org/showthread.php?p=7664533](http://swiss.ubuntuforums.org/showthread.php?p=7664533)

Do I rather edit the xorg file as explain in this thread (see: top of the thread) or as the link above in my message?

Thanks

---

### Post by jocko on 2009-11-04
> **nomnex said:**
> 2) The second notebook as an ATI radeon 9200, can I use the fglrx/catalyst driver? Advice.
No. amd dropped support for anything below radeon 9500 three years ago, and a few months ago they dropped support for anything below the radeon hd cards.

---

### Post by toulousain on 2009-11-04
[@nomnex]("http://www.uluga.ubuntuforums.org/member.php?u=822863")

I found it on the french Ubuntu website: [http://doc.ubuntu-fr.org/catalyst](http://doc.ubuntu-fr.org/catalyst)

There is a post at the beginning that mentions the new version is 9.10 and gives the link I posted above: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)

---

### Post by jocko on 2009-11-04
> **toulousain said:**
> [@nomnex]("http://www.uluga.ubuntuforums.org/member.php?u=822863")

I found it on the french Ubuntu website: [http://doc.ubuntu-fr.org/catalyst](http://doc.ubuntu-fr.org/catalyst)

There is a post at the beginning that mentions the new version is 9.10 and gives the link I posted above: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)
Ehh... Anyway, the catalyst driver does not support his card, so there's no point for him to check that post...

---

### Post by nomnex on 2009-11-06
Correct, the first card ATI radeon on the AMD drivers download page for Linux is 9600. Nothing below.

regarding the xorg.conf

```
/etc/X11/xorg.conf
```I have edited it with both settings - the one at the beginning of the thread and the one in the link I give in one of my post above (see: check this thread)

No of them changed the display. It is not getting clearer, better and the windows still breaks when I move them on screen - i.e. the frame rate is bad.

Any idea? Might Karmic and its new Intel driver fix the problem?

---

### Post by jocko on 2009-11-06
> **nomnex said:**
> Correct, the first card ATI radeon on the AMD drivers download page for Linux is 9600. Nothing below.
Actually, the limit for using any of the drivers released the last 6 months is radeon hd 2xxx, so radeon 9600 is also too old...

> **nomnex said:**
> regarding the xorg.conf

```
/etc/X11/xorg.conf
```I have edited it with both settings - the one at the beginning of the thread and the one in the link I give in one of my post above (see: check this thread)

No of them changed the display. It is not getting clearer, better and the windows still breaks when I move them on screen - i.e. the frame rate is bad.

Any idea? Might Karmic and its new Intel driver fix the problem?
The linked one will not work as it will only affect xaa acceleration, which is not used by default anymore (exa is used instead).
Why would the intel driver fix the problem? It of course does not work with ati cards...

Here's the relevant parts from my xorg.conf, which improves performance a lot for my radeon 9600. I don't know exactly which setting(s) made the difference, but it's one or more of the options in the device section (and some of the options don't do anything as they are used by default anyway)...
```

Section "Device"
        Option        "EnableDepthMoves"    "True"
        Option        "EnablePageFlip"    "True"
        Option        "DMAForXv"        "True"
        Option        "AccelDFS"        "True"
        Option        "ColorTiling"        "True"
        Option        "RenderAccel"        "True"
        Option        "VGAAccess"        "True"
        Option        "AccelMethod"        "EXA"
        Option        "DRI"            "True"
        Option        "MigrationHeuristics"    "greedy"
        Option        "TripleBuffer"        "True"
        Option        "EXAOptimizeMigration"  "true"
        Option        "EXANoComposite"    "No"
        Option        "BackingStore"        "true"
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AP [Radeon 9600]"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Option     "Accel"    "True"
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection
```

---

### Post by nomnex on 2009-11-06
Could you take a look at this link. It is called legacy drivers.

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.1&#9001;=English&rev=9.3&ostype=Linux%20x86]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.1&lang=English&rev=9.3&ostype=Linux%20x86")

There is a valid download driver for several cards starting from 9500 - including your card 9600 (driver: **ATI Catalyst™ 9.3 Proprietary Linux x86 Display Driver**). Could it conflict with your information in your post above?

Regarding your xorg.conf, first thanks for sharing, then I have copied/past the xorg.conf from the thread [http://swiss.ubuntuforums.org/showthread.php?p=7664533](http://swiss.ubuntuforums.org/showthread.php?p=7664533)

It s my first experience editing the xorg.conf. I could use your expertise. Can I merge your options in the xorg.conf below? As aforementioned, I did not notice any difference using the xorg.conf below (as is), or the one at the beginning of the thread - you pointed out the reason: it will only affect xaa acceleration -  vs. the default xorg.conf (i.e. no configuration).

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Radeon 900"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```PS: Karmic and the Intel driver was a confusion on my side.

---

### Post by nomnex on 2009-11-06
I did try to merge both xorg.config

```
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option         "XAANoOffscreenPixmaps"
        Option         "EnableDepthMoves" "True"
        Option         "EnablePageFlip" "True"
        Option         "DMAForXv" "True"
        Option         "AccelDFS" "True"
        Option         "ColorTiling" "True"
        Option         "RenderAccel" "True"
        Option         "VGAAccess" "True"
        Option         "AccelMethod" "EXA"
        Option         "DRI" "True"
        Option         "MigrationHeuristics" "Greedy"
        Option         "TripleBuffer" "True"
        Option         "EXAOptimizeMigration" "True"
        Option         "EXANoComposite" "No"
        Option         "BackingStore" "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
        Option "RENDER" "Enable"
        Option "XVideo" "Enable"
        Option "XINERAMA" "False"
EndSection
```Sadly, not to avail. With xorg.conf edited or not, it makes no difference on my notebook screen. I was expecting to notice a difference (good or bad) but no change. It it possible?

---

### Post by jocko on 2009-11-06
> **nomnex said:**
> I did try to merge both xorg.config

...

Sadly, not to avail. With xorg.conf edited or not, it makes no difference on my notebook screen. I was expecting to notice a difference (good or bad) but no change. It it possible?
Try changing:
```
        Option         "AccelMethod" "EXA"
```To:
```
        Option         "AccelMethod" "XAA"
```That changes the method used for 2d acceleration (EXA should perform better than XAA, but it's worth a try...)

---

### Post by Himself2007 on 2009-11-06
> **nomnex said:**
> @toulousain,

I am looking for the proprietary driver for my ATI Radeon 9000 on a Fujitsu notebook (I use Jaunty), where did you find yours - the full web site address please.

Your driver seems different than those available there: [http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

To anyone: on the official ATI page (link above), there are 3 download options (2 seems identicals - the XFree 86)
Option a (one choice):
- XFree 86 4.3 Drivers
Option b (two choices):
- XFree68 4.3 Drivers
- X.Org 6.8 Drivers

What's the one for Ubuntu 9.04/9.10? Thanks

nomnex

Problem similar to yours.
Look carefully the titles in this page...they say 64 !!!
These are 64 bits drivers...I guess.
And whatever you choose 32 or 64 bits driver from the preceding page, it will bring you in the same page anyway!

Luc

---

### Post by SeePU on 2009-11-12
There seems to be too many variations on this configuration.

Could someone who has a working ATI Radeon driver pm me their xorg.conf and/or post it here?  -Must have Mobility Radeon 9000 and using ati driver.

I'd be interested in giving it one more try.   I have copy/pasted at least two different yet related xorg.conf files from this thread with unsuccessful results.  The screen would flicker like mad and have artifacts and have screens overlapping one another (repaint issue?).

---

### Post by Himself2007 on 2009-11-12
I've had a problem similar to yours.
And I tried to get the right driver pack to install.
But nothing below 9500 seems to be available and confirmed by some.
Anyway... I did nothing about update packs and my ATI is fine now.
I just did something else.
Consider post#6 in this link:

[http://ubuntuforums.org/showthread.php?t=1305306](http://ubuntuforums.org/showthread.php?t=1305306)

If this can help...

Luc

---

### Post by nomnex on 2009-11-12
@Luc
What specific difference before/after passing the commands in post #6 do you experience

@everybody on the thread
I have done a fresh install 9.10. Fujistu notebook (Japan) Biblo-NH28D with Mobility Radeon 9000.

The output is (of course) the same as under 9.04. There are not obvious bug, it is just the graphic is very poor considering the capacity of the card. Do you people have the same complain with your card/notebook, or do you experience a more serious matter?

Editing the xorg.conf did not change a thing. I guess, the system use already the best config automatically, unless there is a different/proper way to load the xorg.conf - but it seems not.

Regarding the drivers, I wonder which one renders better (the open source in the Ubuntu package) or the proprietary (no available)

---

### Post by SeePU on 2009-11-12
> **nomnex said:**
> @Luc
What specific difference before/after passing the commands in post #6 do you experience

@everybody on the thread
I have done a fresh install 9.10. Fujistu notebook (Japan) Biblo-NH28D with Mobility Radeon 9000.

The output is (of course) the same as under 9.04. There are not obvious bug, it is just the graphic is very poor considering the capacity of the card. Do you people have the same complain with your card/notebook, or do you experience a more serious matter?

Editing the xorg.conf did not change a thing. I guess, the system use already the best config automatically, unless there is a different/proper way to load the xorg.conf - but it seems not.

Regarding the drivers, I wonder which one renders better (the open source in the Ubuntu package) or the proprietary (no available)
nomnex, don't even bother with the proprietary/fglrx with your/that Radeon 9000 card.  It's only supported by ATI with the open source radeon/ati driver (I know, for sure, that you use 'ati driver' and it's a wrapper that encompasses the radeon driver.  I didn't explain it exactly but it's close enough.

Just keep trying to tweak the xorg.conf because there's a lot of people with the same card trying to optimize their xorg config file.  Some users claim to get a decent working system although I don't know how.  I've had nothing but problems trying to create an xorg.conf file that works without crashing or allows desktop effects to work properly.  

I'd like someone who can use Rendering and OpenGL to provide their xorg.conf for hardware that includes the Mobility Radeon 9000 and to mention whether they have 32, 64, or 128MB DDR-SDRAM video memory.

---

### Post by buntuchimp on 2009-11-17
Bumping. I have the same problem on a fresh 9.10 with a radeon x1600 (cpu thrashing everytime a windows is moved). I don't even have a xorg.conf file. Where does X read configuration from then? Can I generate an xorg.conf file to edit - if so how? Is there someplace else I should look for help?

---

### Post by Himself2007 on 2009-11-17
> **nomnex said:**
> @Luc
What specific difference before/after passing the commands in post #6 do you experience

@everybody on the thread
I have done a fresh install 9.10. Fujistu notebook (Japan) Biblo-NH28D with Mobility Radeon 9000.

The output is (of course) the same as under 9.04. There are not obvious bug, it is just the graphic is very poor considering the capacity of the card. Do you people have the same complain with your card/notebook, or do you experience a more serious matter?

Editing the xorg.conf did not change a thing. I guess, the system use already the best config automatically, unless there is a different/proper way to load the xorg.conf - but it seems not.

Regarding the drivers, I wonder which one renders better (the open source in the Ubuntu package) or the proprietary (no available)

Question 1 : black screen problems for appearance settings are gone.
Video is now top-notch.

Luc

---

### Post by nomnex on 2009-11-22
I experience a crash when running a simple photo slide-show (F-spot) - default xorg. or edited xorg. does not change a thing. I launch the slide-show, the screen flickers then freezes and I can only recover doing a cold boot.

If anybody could come with a solution or idea (or a different xorg.conf file)? The notebook is in good condition, I am only limited by the graphical capability.

@himself2007: you don't experience any problem ever since? the rest of the thread after you post is pretty scary (fonts messed up, configuration problem, etc.)
- I will try this command at last.

---

### Post by Himself2007 on 2009-11-23
> **nomnex said:**
> I experience a crash when running a simple photo slide-show (F-spot) - default xorg. or edited xorg. does not change a thing. I launch the slide-show, the screen flickers then freezes and I can only recover doing a cold boot.

If anybody could come with a solution or idea (or a different xorg.conf file)? The notebook is in good condition, I am only limited by the graphical capability.

@himself2007: you don't experience any problem ever since? the rest of the thread after you post is pretty scary (fonts messed up, configuration problem, etc.)
- I will try this command at last.

Nomnex

The fonts messed up have disappeared with the updates.
Everything have looked nice since.
But right now, everything has been messed up again due to a *%&*((% Windows XP restored backup on my dual-boot XP/Ubuntu computer!
I will have to reinstall Ubuntu again.
But fortunately I had a precise collection of  backuped "how to solve my specific problem in Ubuntu" files of everything I did since my first install of Ubuntu 9.10!
Anyway it's fun!
But I confirm you can apply what I suggested as it worked fine by after.

Luc

---

### Post by nomnex on 2009-11-24
Thanks Luc,

Will backup too, and give the command a try.
Good luck with your new fresh install/restore

PS: how can a XP sys restore interfere with your Ubuntu dual booting? What's your config. partition?

---

### Post by Himself2007 on 2009-11-24
> **nomnex said:**
> Thanks Luc,

Will backup too, and give the command a try.
Good luck with your new fresh install/restore

PS: how can a XP sys restore interfere with your Ubuntu dual booting? What's your config. partition?

It's hard to figure out the reason why.  Let's hypothetize...
Actually I had a XP backup on my dual-boot XP/Ubuntu station.
I used my recovery disk from Acronis true Image workstation 9.1 backup software.
From what I learned from the forum and else is that Windows have this %/&?%/?%& habit of taking control of the full computer.
Something surely changed as Ubuntu was not available at all!
Not even from GRUB who was erased (?).
So I tried several techniques but none worked actually.
That why I decided to reinstall everything but it went fast and good.
And this is why I will return with Acronis Disk director suite's OS Selector instead of GRUB for multi-booting management.
And I have the working trick to avoid automatic GRUB on Ubuntu's installation.
By the way it's not that I don't like Grub...
I won't be using it anymore as it seems to be vulnerable to some of Window$'s infamous practices!
It makes me think about something...investigate on separate backup softwares for Ubuntu.
I'll open up a thread on this!

Luc

---

### Post by mikeollie1 on 2009-11-27
Look at it [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139) post #41, it works perfect with my Radeon 9200 and karmic koala.

---

### Post by Zuhaira on 2009-12-04
Hello everybody!

Giblet5 your method works fine with me except for some issues
When I try some screen savers the whole system stuck
that let me to shut down my computer by force.

I tried Neverball game which uses great power of the gpu it works but a small black line flickering on the top and then quit after entering some levels.

back time when I first used Ubuntu 6.06, I installed the proprietary fglrx driver which was great for this card..
I tried Beryl and various 3D games like Neverball, Nexuiz and many without any problem before they drop support.

I hope that issue will be solved especially for people who can't afford a new device. :)

Thanks in advance!

---

### Post by gypsumwolf on 2010-01-16
I have Ubuntu 9.10 and an ATI 9000 gpu on a Toshiba Satellite A85 laptop.

I have native resolution, but only partially working 3D (System is using 9200 open-source driver). To bad there is no driver for older cards. The open source drivers go down to 9200 and not any lower. Where is the lost versatility of Linux? It is supposed to work well on older systems! And why is there no xorg config file created to use as a reference? (It would be useful to have the file automatically created with a new install!) What went wrong?? Worthless politics?

---

### Post by jocko on 2010-01-17
> **gypsumwolf said:**
> I have Ubuntu 9.10 and an ATI 9000 gpu on a Toshiba Satellite A85 laptop.

I have native resolution, but only partially working 3D (System is using 9200 open-source driver). To bad there is no driver for older cards. The open source drivers go down to 9200 and not any lower. Where is the lost versatility of Linux? It is supposed to work well on older systems! And why is there no xorg config file created to use as a reference? (It would be useful to have the file automatically created with a new install!) What went wrong?? Worthless politics?
You are misinformed. There are open source drivers that support 3d on every ati card from the old mach64, rage128 and all radeons from the first 7000 cards to somewhere in the radeon X or HD series. So when ati dropped support for the "older" cards in the fglrx driver, the only cards that were yet not fully supported by the open source driver were some cards in the X series (I'm not sure, but I would guess that these cards are supported by some more recent radeon driver).
The reason there is no xorg.conf is because it is not needed anymore. xorg detects what card you have and uses the correct driver automatically. But with some cards the default settings are not very good, so to tweak it to work better you may need to make a xorg.conf.

---

### Post by gypsumwolf on 2010-01-18
> **jocko said:**
> You are misinformed. There are open source drivers that support 3d on every ati card from the old mach64, rage128 and all radeons from the first 7000 cards to somewhere in the radeon X or HD series. So when ati dropped support for the "older" cards in the fglrx driver, the only cards that were yet not fully supported by the open source driver were some cards in the X series (I'm not sure, but I would guess that these cards are supported by some more recent radeon driver).
The reason there is no xorg.conf is because it is not needed anymore. xorg detects what card you have and uses the correct driver automatically. But with some cards the default settings are not very good, so to tweak it to work better you may need to make a xorg.conf.

Then how come the computer tells me it is a 9200 instead of a 9000?

---

### Post by jocko on 2010-01-18
> **gypsumwolf said:**
> Then how come the computer tells me it is a 9200 instead of a 9000?
No idea. *How* does your computer tell you that? And how do you know it's a 9000 if your computer tells you it's a 9200?

What's the output of:```
sudo lshw -class display

```

---

### Post by gypsumwolf on 2010-01-18
I know that the documentation from the laptop says 9000. [Read it here]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=1042296&rpn=PSA82U&modelFilter=A85-S107&selCategory=3&selFamily=1073768663#contentArea") (click on detailed specs and read the pdf).

The sysinfo program says it is a 9200 for sure. lshw said like 9200 or 9100. I am not able to run the command on the computer at the moment because we are heading out for a little while. I do know it is not 9000 and it does say 9200 or 9100.

---

### Post by jocko on 2010-01-19
> **gypsumwolf said:**
> I know that the documentation from the laptop says 9000. [Read it here]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=1042296&rpn=PSA82U&modelFilter=A85-S107&selCategory=3&selFamily=1073768663#contentArea") (click on detailed specs and read the pdf).

The sysinfo program says it is a 9200 for sure. lshw said like 9200 or 9100. I am not able to run the command on the computer at the moment because we are heading out for a little while. I do know it is not 9000 and it does say 9200 or 9100.
As far as I understand, there is nothing in the driver that can cause the card to be misdetected. The card is detected before the driver is loaded. Either there is a bug in the kernel or whatever it is that is supposed to detect the card, or there is a bug in your laptop's bios. Apparently your problem is nothing new ([same laptop, same problem 2007]("http://ubuntuforums.org/showthread.php?t=496633")).

I'm not sure if misdetecting a 9000 as a 9100 or 9200 really cause any problem. Those cards use the same driver.

---

### Post by gypsumwolf on 2010-01-20
Hm.. Interesting. I don't have an xorg.conf file to edit so I can't try configuring it. I will check on my bios.

More info:
```
~# glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

More info (2):
```
~# glxinfo | grep "direct rendering"
direct rendering: Yes

```

Here is the Xorg.0.log file:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux silvermoon 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=828999ff-0c25-4b33-9122-40c459fbd9aa ro splash quiet
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 20 19:50:42 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:7835:1179:ff00 ATI Technologies Inc Radeon Mobility 9200 IGP rev 0, Mem @ 0xf0000000/134217728, 0xe8100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default ati Device 0"
		Driver	"ati"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default ati Screen 0"
		Device	"Builtin Default ati Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default ati Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000e8100000
(II) RADEON(0): MMIO registers at 0x00000000e8100000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9200 IGP 7835" (ChipID = 0x7835)
(--) RADEON(0): Linear framebuffer at 0x00000000f0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 100, max_in_pll: 1350, xclk: 16500, sclk: 222.000000, mclk: 165.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=35000; xclk=16500
(II) RADEON(0): Panel ID string: SHP                     
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 8, HSyncWidth: 136
VBlank: 38, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC-J
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC2
  DDC reg: 0x60
(II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x0
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1024x768
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit f0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 65536 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00400000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00404000
(II) RADEON(0): Will use 4096 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 4096 kb for back buffer at offset 0x00408000
(II) RADEON(0): Will use 4096 kb for depth buffer at offset 0x00808000
(II) RADEON(0): Will use 26368 kb for textures at offset 0x00c08000
(II) RADEON(0): Will use 26848 kb for X Server offscreen at offset 0x025c8000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xf0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 8x
(II) RADEON(0): [agp] Mode 0x1f00020a [AGP 0x1002/0x7831; Card 0x1002/0x7835 0x1179/0xff00]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xec000000
(II) RADEON(0): [agp] Ring mapped at 0xb77c7000
(II) RADEON(0): [agp] ring read ptr handle = 0xec101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb78e7000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xec102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3556000
(II) RADEON(0): [agp] GART texture map handle = 0xec302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb3076000
(II) RADEON(0): [drm] register handle = 0x2d020000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x0fff0c00 is: 0x0fff0c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xec7fec00
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R200 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Offscreen pixmap area of 27492352 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable TVDAC
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event6"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) PS/2 Mouse: initialized for relative axes.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1360x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1032 1168 1344  768 771 777 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video

```

When I watch flash movies it uses up the CPU to 100% instead of using the GPU to help.

---

### Post by gypsumwolf on 2010-01-20
Also,

```
~# lshw -class display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility 9200 IGP
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:f0000000-f7ffffff(prefetchable) ioport:9000(size=256) memory:e8100000-e810ffff memory:e8120000-e813ffff(prefetchable)

```

---

### Post by zimin on 2010-01-22
people help
all that I have done nothing helped
 that's why i ask:
1. when i configure xorg i should instal ati driver or this only for fglrx ??
2. When i tried to install ati rdiver program said that i neet to uninstall fglrx folder at plase where is no such lofder/

could you tell me like a chiled whot i must to do&:confused::confused::confused::confused::confused::confused::confused::confused::confused:
my video radeon 9200.

---

### Post by cmx on 2010-01-30
> **zimin said:**
> people help
all that I have done nothing helped
 that's why i ask:
1. when i configure xorg i should instal ati driver or this only for fglrx ??
2. When i tried to install ati rdiver program said that i neet to uninstall fglrx folder at plase where is no such lofder/

could you tell me like a chiled whot i must to do&:confused::confused::confused::confused::confused::confused::confused::confused::confused:
my video radeon 9200.
 no support in fglrx for your card,use open source driver,xorg.conf's from this thread seems to bee working

---

### Post by SeePU on 2010-01-31
> **cmx said:**
> no support in fglrx for your card,use open source driver,xorg.conf's from this thread seems to bee working
What xorg.conf (from this thread)?

I think I checked this thread a while ago and I had to come up with my own xorg.conf which (after several tweaks) finally worked.  This is in 9.10.

Fortunately, I don't have to do any tweaking or editing in Lucid 10.04 Alpha 2 so it seems they fixed it?

---

### Post by hufemj on 2010-03-09
Thanks! The xorg.conf file above got my primary display working for my frozen D600 laptop. But, the external display wasn't working. I tried fooliing around with the xorg.conf per some posts on the web, but didn't get there. The driver fix worked perfectly.

---

### Post by nomnex on 2010-03-11
> **hufemj said:**
> Thanks! The driver fix worked perfectly.

A poster above said there **were no proprietary ATI driver any more** for an ATI Mobility Radeon 9000 card on a 32 bit architecture. The only current ATI driver available is the open source ATI driver in the repo. What's your ATI card and CPU architecture please?

```
lspci | grep "Radeon && uname -m"
```

---

### Post by kuric on 2010-11-27
> **SeePU said:**
> There seems to be too many variations on this configuration.

Could someone who has a working ATI Radeon driver pm me their xorg.conf and/or post it here?  -Must have Mobility Radeon 9000 and using ati driver.

I'd be interested in giving it one more try.   I have copy/pasted at least two different yet related xorg.conf files from this thread with unsuccessful results.  The screen would flicker like mad and have artifacts and have screens overlapping one another (repaint issue?).

As long as I know, you can't use "ati" proprietary driver on Ubuntu 9 or higher. But you can use generic "radeon" opensource driver. That's what I'm using now on a ATI Mobility Radeon 9000 IGP. Here's my xorg.conf in the attachment.

I was experiencing a lot of crashes and I've tried a billion solutions, here's some of the most successful:

1) Enable **Option "AGPMode" "4"** in xorg.conf.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
[I]
"3D may hard-freeze X-server unless AGP mode is set correctly in Xorg.conf. If you have this problem, try adding Option "AGPMode" "4" to the device section of Xorg.conf"[/I]

For those who don't have a xorg.conf file, follow these steps:
Ctrl+Alt+F1
$ sudo service gdm stop
$ sudo Xorg -configure
$ sudo service gdm start
Rename xorg.conf.new (in your home folder) to xorg.conf and copy it into /etc/X11 folder

2) Turn off **Compiz**. Go to Synaptic and remove all packages related to compiz.

3) Enable **nohz=off** option.
$ sudo gedit /boot/grub/grub.cfg and add nohz=off option on the first menuentry, should look something like this:
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec5f3463-a301-4f6f-aa23-3cbb44dc140d ro quiet splash nohz=off

4) Disable **3D acceleration** (poor solution). Install driconf from Synaptic. Select Preferences > Administration Tools > 3D Acceleration. Go to Debugging tab and disable 3D acceleration.

5) Uninstall applications with unstable activity like **Firefox** (due to flash player, try Google Chrome instead), **Firestarter** or **Ubuntu One**.

6) Remove **pulseaudio** and install alsa. 
[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)
[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

7) Disable **Hyper Threating** in Bios options. This is very effective.

---

