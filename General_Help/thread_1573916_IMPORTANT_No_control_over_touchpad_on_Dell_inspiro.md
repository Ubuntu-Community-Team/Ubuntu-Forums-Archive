---
title: "IMPORTANT: No control over touchpad on Dell inspiron 15R makes Ubuntu unuseable"
date: 2010-09-13
forum: General Help
---

### Post by jasminetea on 2010-09-13
I have ubuntu 10.04 on a dell inspiron 1525 -- bought with linux on it ... 

I ordered a dell Inspiron 15R ... 64 bit etc decent spec ... in europe you cannot order an 'ubuntu' dell anymore .. was a happy customer ...

Ordered it with windows on it .. didn't want windows - wiped it (I will claim a refund when I get round to it) ...

Straight away I notice problems .... 'tap to click' I think it is
is on the 15R causing the touchpad to interrupt your typing by raising the window which the mouse pointer is over (as if you have 'tapped' to click) ...

On the dell inspiron 1525 'system preferences mouse' you get a 'Touchpad' tab.   This on standard install the checkboxes 'disable touchpad while typing' checked, also 'enable mouse clicks' with touchpad ... this gives you control over the touchpad and enables you to stop it interrupting what you type ..

On the dell 15R there is no tab there.  This means that the touch pad can't be controlled.  

I go to the web as to how to fix this and I am given two options

.. for ubuntu intrepid and jaunty edit the file 

/etc/hal/fdi/policy/shmconfig.fdi

and insert:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>

reboot (some people have reported that it needs a reboot not just an X restart) and you should be able to use 

This does not succeed (on jaunty which I have tried)

'gsynaptics' which -- when it doesn't run asks for 'SHMConfig is not set as True '

which you are told you need for later versions ... in order to do this you are told to perfom the following:

edit the file /etc/X11/xorg.conf (on later versions of linux you will have to generate this file) and add Option "SHMConfig" "true" at Input Device section ...


Sample :

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "true"
EndSection

^ the general sample from the web ...

1 problem with this ... on the dell 15R there is no section for the 'synaptics touchpad' and even if you put the above in it doesn't work ...

big problem ... rather disappointed because apart from there having been no straight upgrade path from an ubuntu 1525 to the newest standard cheap laptop (15R) this problem exists ... 

I have noticed people complaining about this all over the place .. there is even an ubuntu bugfix for it ... why is this not fixed?  I have spent over 24 hours on this and am not happy

---

### Post by jasminetea on 2010-09-13
I read eventually that 'gysnaptics' touch pad control has been deprecated -- use gnome gpointing-device-settings ....

there is a debian install file:

[http://packages.ubuntu.com/karmic/amd64/gpointing-device-settings/download](http://packages.ubuntu.com/karmic/amd64/gpointing-device-settings/download)

this debian package does not install ... I get

"Error: Dependency is not satisfiable: libgpds0 (>= 1.5.0)"

I'm on 10.04 lucid lynx (64 bit)

---

### Post by jasminetea on 2010-09-13
> **jasminetea said:**
> I read eventually that 'gysnaptics' touch pad control has been deprecated -- use gnome gpointing-device-settings ....

there is a debian install file:

[http://packages.ubuntu.com/karmic/amd64/gpointing-device-settings/download](http://packages.ubuntu.com/karmic/amd64/gpointing-device-settings/download)

this debian package does not install ... I get

"Error: Dependency is not satisfiable: libgpds0 (>= 1.5.0)"

I'm on 10.04 lucid lynx (64 bit)

Right -- you can install libgpds0 from synaptic -- but it's too early a version -- have installed 

libgpds0_1.5.1-2_amd64.deb

from: [http://ftp.pl.debian.org](http://ftp.pl.debian.org)

....


now debian package install of gpointing-device-settings says:

Error: Dependency is not satisfiable: gconf2 (>= 2.28.1-2)

gconf2 in synaptic says already installed but 2.28.1-0ubuntu1

... is that earlier than 2.28.1-2?  -- 0ubuntu1??

trying to uninstall gconf2 has many dependencies - leaving it alone and now trying to install the 'gconf2' it wants.

---

### Post by jasminetea on 2010-09-13
> **jasminetea said:**
> Right -- you can install libgpds0 from synaptic -- but it's too early a version -- have installed 

libgpds0_1.5.1-2_amd64.deb

from: [http://ftp.pl.debian.org](http://ftp.pl.debian.org)

....


now debian package install of gpointing-device-settings says:

Error: Dependency is not satisfiable: gconf2 (>= 2.28.1-2)

gconf2 in synaptic says already installed but 2.28.1-0ubuntu1

... is that earlier than 2.28.1-2?  -- 0ubuntu1??

trying to uninstall gconf2 has many dependencies - leaving it alone and now trying to install the 'gconf2' it wants.

I'm removing gconf2 so I can install the latest version and it's removing lots of other stuff (ongoing) ... is that right?  I just want to install the later gconf2 -- have supposed that you have to remove the existing one before the later one -- uninstalling through synaptic.

---

### Post by jasminetea on 2010-09-13
> **jasminetea said:**
> I'm removing gconf2 so I can install the latest version and it's removing lots of other stuff (ongoing) ... is that right?  I just want to install the later gconf2 -- have supposed that you have to remove the existing one before the later one -- uninstalling through synaptic.

right I managed to remove the existing gconf2 now It can't install the later gconf2 

-- failed to install package gconf2_2.28.1-3_amd64.deb

reasons:

maybe i re-install ubuntu (again) -- start again ....

Selecting previously deselected package gconf2.
(Reading database ... (Reading database ... 5%(Reading database ... 10%(Reading database ... 15%(Reading database ... 20%(Reading database ... 25%(Reading database ... 30%(Reading database ... 35%(Reading database ... 40%(Reading database ... 45%(Reading database ... 50%(Reading database ... 55%(Reading database ... 60%(Reading database ... 65%(Reading database ... 70%(Reading database ... 75%(Reading database ... 80%(Reading database ... 85%(Reading database ... 90%(Reading database ... 95%(Reading database ... 100%(Reading database ... 111811 files and directories currently installed.)
Unpacking gconf2 (from .../gconf2_2.28.1-3_amd64.deb) ...
Setting up gconf2 (2.28.1-3) ...
update-alternatives: using /usr/bin/gconftool-2 to provide /usr/bin/gconftool (gconftool) in auto mode.
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 38, in <module>
    for f in os.listdir(schema_location):
OSError: [Errno 2] No such file or directory: '/usr/share/gconf/schemas'
dpkg: error processing gconf2 (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 gconf2

---

### Post by jasminetea on 2010-09-13
maybe this has something to do with not having installed the later gconf2 common - trying that ....

---

### Post by jasminetea on 2010-09-13
> **jasminetea said:**
> maybe this has something to do with not having installed the later gconf2 common - trying that ....

should I try ubuntu 10.10?

this is RIDICULOUS - this is a BASIC ISSUE - ubuntu is non serviceable on the Dell basic laptop

---

### Post by uRock on 2010-09-13
Your first post says you are using 9.04 on this machine. Is that what you are using or 10.04?

---

### Post by jasminetea on 2010-09-13
> **uRock said:**
> Your first post says you are using 9.04 on this machine. Is that what you are using or 10.04?

I installed 9.04 to try the earlier fix -- will go back to 9.04 if if fixes this ....

Later documented fixes on 10.04 I run 10.04.

10.04

But I'm now going to try 10.10 because maybe it has the later gconf etc and can run 'gpointing-device-settings'.

---

### Post by uRock on 2010-09-13
I hope 10.10 works out. 9.04 is one of the best I have used, but it will hit the end of its road very soon. 

If you install 10.10 and need help with getting things working, then you may want to start a thread [here]("http://ubuntuforums.org/forumdisplay.php?f=385") to insure help from people who have been working with the dev version.

Best of wishes,
uRock

---

### Post by jasminetea on 2010-09-13
> **uRock said:**
> I hope 10.10 works out. 9.04 is one of the best I have used, but it will hit the end of its road very soon. 

If you install 10.10 and need help with getting things working, then you may want to start a thread [here]("http://ubuntuforums.org/forumdisplay.php?f=385") to insure help from people who have been working with the dev version.

Best of wishes,
uRock

10.10 install gpointing-device-settings &

Dependency is not satisfiable: libgpds0 (>= 1.5.0) 

(no)

---

### Post by uRock on 2010-09-13
Have you searched [Launchpad]("https://launchpad.net/+search?field.text=&field.actions.search=Search") to see if there is a bug report and workaround listed for this?

---

### Post by jasminetea on 2010-09-13
> **uRock said:**
> Have you searched [Launchpad]("https://launchpad.net/+search?field.text=&field.actions.search=Search") to see if there is a bug report and workaround listed for this?

right -- managed to install gpointing-device-settings on the new laptop -- no options for touchpad - would be ok if not for that

.... on the 1525 (touchpad compatible laptop) -- the settings show up ...

installed from synaptic - should have tried there first - but was being pessimistic -- also gsynaptics installs from there - but for the newer laptop the same response as the manual install of that package (set SHMConfig to true).

will check launchpad now

---

### Post by jasminetea on 2010-09-13
From that forum (launchpad) -- I see the probable origin of my problem :(

people assume that 'because I use it everyone uses it (in this case 'tap to click') --- 

"
Currently in 9.10 touchpad tap to  click is disabled by default. This behaviour is expected behaviour for a  touch pad to work by default. Also Ubuntu has had this as a default  behavior for a very long time. New driver & the ability to  manipulate synapatic touch pad functionality have lead to the regression  from the community. I see the same problem in other distributions as  well.
 The gconf key is:
desktop->gnome -> peripherals -> mouse -> tap_to_click
 Currently users have to go into the preferences->mouse .. then to  the touchpad tab to enable this feature. Though early testing many are  seeing it as a fault in the driver and unaware of this new tab.
 If this is on by default when a user taps their touchpad for a mouse click, they will get expected behaviour."


maybe I now look for the way that tap to click is disabled specifically -- but I think it may be a problem specific to this laptop (inspiron 15R).

---

### Post by jasminetea on 2010-09-13
reading this from:

[http://who-t.blogspot.com/2010/05/how-to-enable-tapping-tap-to-click-on.html](http://who-t.blogspot.com/2010/05/how-to-enable-tapping-tap-to-click-on.html)

now less hopeful -- hardware?  -- thing is the gnome system expects 'synaptics' touchpad  :(

"As pointed out in the comments, sometimes the control panel doesn't show  a touchpad tab. The tab is conditional on whether a property  initialized by the X.Org synaptics driver could be detected. So if the  tab is missing, the usual cause is that the touchpad isn't detected  correctly by the kernel and looks like a mouse to userspace. This can  get confusing if the touchpad does tapping and other features in  hardware but to userspace a tap looks like a left button press, etc. The  latest versions of elantech touchpad suffered from this."

then ...

"What can I do if I don't have a "Touchpad" tab? Can I just edit some configuration file or setting somewhere instead?"  

..... I have no idea either

am downloading 'kubuntu' overnight -- don't really want to ditch gnome but I must fix this

---

### Post by cloyd on 2010-09-13
What about getting a mouse?  They are cheap. I realize you want to fix the issue. A mouse would only be a work around. But it would help until you could figure out the problem. I know the problem, I have a "heavy" touch. The very first thing I have to do on any laptop is to disable the 'tap to click' option.

---

### Post by jasminetea on 2010-09-13
this looked hopeful:

[http://crunchbanglinux.org/forums/topic/654/disabling-touchpad-taptoclick/](http://crunchbanglinux.org/forums/topic/654/disabling-touchpad-taptoclick/)

"after installing CB i found no easy way to disable the pesky tap-to-click "feature" on the synaptics touchpad on my laptop..(no synaptics-tab in mouse-setup)
Configuring X changed since ubuntu 8.10, configuring X by manually changing xorg.conf is not possible..so i googled it and finally found a solution on the ubuntu-forums that worked for me 
(important thing is to place the three lines in the right place in the file..it didnt work on my first try)
[http://ubuntuforums.org/showthread.php?](http://ubuntuforums.org/showthread.php?) … ost6563109
------cut here---
(1) Find out the value of the info.product key for your touchpad, by searching 'input.touchpad' in the output of lshal: mine was 'AlpsPS/2 ALPS GlidePoint'.
code: lshal > hal.txt && gedit hal.txt"

(snip)

up until there -- I cannot identify from my lshal -- what the touchpad is ... lshal determines the HAL devices

lshal | grep input.touchpad gives me nothing

---

### Post by jasminetea on 2010-09-13
> **cloyd said:**
> What about getting a mouse?  They are cheap. I realize you want to fix the issue. A mouse would only be a work around. But it would help until you could figure out the problem. I know the problem, I have a "heavy" touch. The very first thing I have to do on any laptop is to disable the 'tap to click' option.

No. I bought a laptop for the convenience ... this should be fixeable .. If I wanted to use a mouse I would have bought a desktop.  It renders the laptop unuseable IMO.  Such a simple thing to fix -- who uses 'tap to click' -- I never have ... its highly intrusive -- the assumption even right through the bug reports that it should always there - recent why is it 'off by default' - NO should be on all the time - hence a problem (no way to turn it off).  Retrograde.

---

### Post by jasminetea on 2010-09-13
> **cloyd said:**
> What about getting a mouse?  They are cheap. I realize you want to fix the issue. A mouse would only be a work around. But it would help until you could figure out the problem. I know the problem, I have a "heavy" touch. The very first thing I have to do on any laptop is to disable the 'tap to click' option.

At least you are able to disable it - and that you take for granted.

---

### Post by jasminetea on 2010-09-13
Take this for instance -- "#1 option needed" ... & it's been deprecated:

"There should be a new tab on the gnome-mouse panel and have a checkbox about enabling/disabling the tap-to-click, because this is the No1 option people with laptops want regarding the touchpad. First the tap-to-click (to enable or disable, depending on their preference) and believe it or not, wheel scroll support comes second."

[https://bugs.launchpad.net/gnome-control-center/+bug/92128](https://bugs.launchpad.net/gnome-control-center/+bug/92128)

---

### Post by jasminetea on 2010-09-13
This is depressing -- somebody in February - same problem - no resolution - frustrated - why no solution for something so simple etc? -- Must I stop using linux he says - move back to windows? - & no resolution posted :(

I'ts a shame I have no option -- bought new laptop dell 15R obliterated windows on it - no way back - will have lost money.  No way I go back to windows I would just have to sell the laptop at a loss much time lost -- gain another one with touch pad compatible with ubuntu.

This cannot be happening :cry:

3 days after buying expensive (for me) new laptop & I'm still ](*,) and unable to use it

---

### Post by Slade Winstone on 2010-09-13
Hi Jas,

I've been reading this thread because I'm planning on buying a 15R.  I've had a quick google and noticed that somebody has stated that you should be able to access configuration of "touch to click", etc within gconf.

Can't check this, because I'm at work and don't have the laptop yet, but the instructions said the touchpad settings can currently be configured with the following gconf keys:

/desktop/gnome/peripherals/touchpad/disable_while_typing (bool)
/desktop/gnome/peripherals/touchpad/tap_to_click (bool)
/desktop/gnome/peripherals/touchpad/scroll_method (int 0=off, 1=edge-scrolling, 2=two-finger-scrolling)
/desktop/gnome/peripherals/touchpad/horiz_scroll_enabled (bool)

Hopefully, these will work for you and ease your considerable pain ;)  Let me know if they fix the problem.

Regards,
Slade.

---

### Post by jasminetea on 2010-09-13
> **Slade Winstone said:**
> Hi Jas,

I've been reading this thread because I'm planning on buying a 15R.  I've had a quick google and noticed that somebody has stated that you should be able to access configuration of "touch to click", etc within gconf.

Can't check this, because I'm at work and don't have the laptop yet, but the instructions said the touchpad settings can currently be configured with the following gconf keys:

/desktop/gnome/peripherals/touchpad/disable_while_typing (bool)
/desktop/gnome/peripherals/touchpad/tap_to_click (bool)
/desktop/gnome/peripherals/touchpad/scroll_method (int 0=off, 1=edge-scrolling, 2=two-finger-scrolling)
/desktop/gnome/peripherals/touchpad/horiz_scroll_enabled (bool)

Hopefully, these will work for you and ease your considerable pain ;)  Let me know if they fix the problem.

Regards,
Slade.

Hi Slade - thanks for understanding - hate to be seen to whine but its 1.33am after 2+ days of trying on the old laptop dell inspiron 1525 bought from dell installed with ubuntu -- Bought from dell again for convenience - they do not ship with ubuntu (too late I find they may do it by phone).  I buy dell because it's what I understand & also even though they (in the UK) do not do it any more (why I ask) - it seemed to me to be the closest thing most likely to work with (U) etc .... also value for money I think (mass produced - will be robust) .. this thing I am on has certainly been hammered & has only just started failing after a few years of hammered use - the hitachi deskstar (which some people call the 'deathstar') has begun to fail & hence freeze up the entire system ... As I say it's 1.33am and hearing from you gives me some hope .. will try this tomorrow and report back.  An hour or so ago I saw a utility called 'keyfreeze' which turns the touch pad off with an adjusteable second delay while typing ... I think right away that this is not a solution - the solution is to turn off tap to click completly as I do not use it & I hate 'solutions' which are kludges or compromises on something so basic ...

---

### Post by Slade Winstone on 2010-09-13
Hi Jas,

Its OK.  Like I said, I'm researching carefully before I buy a 15R :)  Been using Linux and Ubuntu for years now, so I check support very carefully before I purchase.  So, I actually appreciate seeing your problems.

I really hope that the gconf keys will sort out your problems.  Let me know how it goes tomorrow.

One last, quick question(s), could you confirm that for your 15R that on your laptop the WIFI and the webcam are working OK?  Also, do you have integrated Intel video, or the ATI video and how is that going?  Finally, how hot does the 15R run?  Is it fairly cool or is it running hot all the time?

Thanks,
Slade.

---

### Post by jasminetea on 2010-09-14
> **Slade Winstone said:**
> 
One last, quick question(s), could you confirm that for your 15R that on your laptop the WIFI and the webcam are working OK? 


WIFI working but not out of the box (as with inspiron 1525) ... had to connect wireless USB dongle then click on administration > hardware drivers it automatically flags up you need the broadcom network driver - installs ok - works ok.  So there is a native driver but it is not on the CD. 

> **Slade Winstone said:**
> 
Also, do you have integrated Intel video, or the ATI video and how is that going?  


No idea -- just works - pretty small video memory on the 15R - works ok fine picture.

> **Slade Winstone said:**
> 
Finally, how hot does the 15R run?  Is it fairly cool or is it running hot all the time?

lm_sensors is installed as standard on the 15R. The inspiron 1525 was originally running hot - overheating permanently until it went back to the dell factory for something else -- they fixed that - but still running pretty hot - fan on all the time whining all the time - will sometimes overheat if access to ventilation blocked etc.  Critial temperature on the inspiron 1525 is 98degc on the 15R it is higher - I think about 105. That machine has no cooling problems temp consistantly around 45degc.  Fan not whirring as much.
> **Slade Winstone said:**
> 
Thanks,
Slade.

Yer welcome
jas

---

### Post by jasminetea on 2010-09-14
Right (Slade) or anyone .... 

edited /home/userdir/.gconf/desktop/gnome/peripherals/touchpad

disable_while_typing (file) - file contains a 1
tap_to_click (file)         - file contains a 0

**Is this how you configure 'gconf' keys?  Have I set up these keys correctly?**

rebooted to be sure (not just restarting X) ...

problem still there. 

BTW I also tried the 'touchfreeze' utility I talked about which is not really a solution just a 'kludge' to stop use of the touch pad while typing with a delay - adustable.  This appears to make the proble WORSE.

BTW (slade) re: graphics - going back to the graphics on the 15R - this definitely needs attending to because looking at it - it is not as sharp as the 1525 and actually reminds me of windows 95 on a cga monitor.  So the graphics needs configuring also.

---

### Post by jasminetea on 2010-09-14
Meanwhile I will try 'kubuntu' just to see - not that I particularly want to stop using gnome.

---

### Post by jasminetea on 2010-09-14
**Bug filed**: 

Cannot disable 'tap to touch' on touchpad Dell Inspiron 15R or machines without synaptic touchpad driver 

[https://bugs.launchpad.net/ubuntu/+bug/638025](https://bugs.launchpad.net/ubuntu/+bug/638025)

Description of bug/status/progression in forum post below ("IMPORTANT: No control over touchpad on Dell inspiron 15R makes Ubuntu unuseable").

[http://ubuntuforums.org/showthread.php?t=1573916](http://ubuntuforums.org/showthread.php?t=1573916)

This bug renders Ubuntu UNUSEABLE with the Dell Inspiron 15R (standard laptop from Dell) and also laptops which don't use the 'synaptic' touchpad driver (see forum post).

---

### Post by jasminetea on 2010-09-14
Testing on the Inspiron 1525 -- gconf-editor - unchecking the 'tap to click' box stops the 'tap to click' RIGHTAWAY. Checking it again enables it.

---

### Post by jasminetea on 2010-09-14
Just for reference for anyone who may want to help me with this -- here is the reference to the problem by someone else in February (when it was not resolved) ....

[http://newyork.ubuntuforums.org/showthread.php?p=8775891](http://newyork.ubuntuforums.org/showthread.php?p=8775891)

quote: "What I dont understamd is why using gconf-editor there is an option in the Ububuntu registry (? windows??) to turn it off but it doesnt do anything? Seems pointless?"

---

### Post by jasminetea on 2010-09-14
Further information from this thread:

[http://ubuntuforums.org/showthread.php?t=441552](http://ubuntuforums.org/showthread.php?t=441552)

[b]"Can Ubuntu be forced to identify an input device differently?
Users of various touchpad input devices are unable to get the linux Synaptics driver applied to them. They function as mice, but that's all. If Ubuntu could be forced to identify these touchpads as "AlpsPS/2 ALPS TouchPad", this might solve the problem.

As I understand the issue:

Synaptics, the company, is the major provider of touchpads for portables. The Synaptics driver for linux makes the extended touchpad features and adjustments available under linux. This driver has been expanded to cover Alps touchpads, a lesser but significant provider of touchpads for portables. Alps touchpads for portables implement the technology of Cirque, which makes its own touchpad devices, and licenses the technology to other device makers, like Adesso.

The problem is that while the Synaptics driver functions with Cirque based touchpads by Alps, it doesn't with Cirque's own touchpads, or Adesso keyboards, or Fellowes touchpads - I have one of each. None of the non-Synaptics/ Alps touchpads are recognized by Ubuntu as touchpads. As the Synaptics linux driver Trouble-Shooting Guide states: "The touchpad must be identified a "SynPS/2 Synaptics TouchPad" or an "AlpsPS/2 ALPS TouchPad". If it is identified as a "PS/2 Generic Mouse" or "PS/2 Synaptics TouchPad", something is wrong.""[/b]

The "issue" is that only through synaptics can you get complete control of the touch pad - to disable the annoying 'tap to click' for instance.  

On my system "/proc/bus/input" renders this for my touchpad (on Inspiron 15R):

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

As you can see this is 'PS/2 Generic mouse'.

On the Inspiron 1525 (which works) - as well as the entry above for "PS/2 Generic Mouse" - you also get:

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=1000003

Which as the above thread states means you have problems as synaptic will not identify it.  It's treated as a dull generic PS/2 mouse and not a touchpad which gnome can configure.

---

### Post by jasminetea on 2010-09-14
Having read this thread:

[https://bugzilla.kernel.org/show_bug.cgi?id=14660](https://bugzilla.kernel.org/show_bug.cgi?id=14660)

Which is a duplicate bug to the one which I have filed - but was filed in March of this year I have to admit defeat.  The problem has not been addressed at all.  Nobody wants to know.  I will have to phone Dell up and ask them now to take back the laptop.  I feel destroyed.  After 3 days on this I have been let down totally by Dell and Linux (because it's not just an Ubuntu problem).  Let down by Dell because I had already bought a Dell Ubuntu laptop.  Let down by Linux because nobody sees fit to fix such an obvious problem which has been reported multiple times and has put many people through this. 

out

absolutely disgusted - I really hope Dell will take that laptop back.

---

### Post by jasminetea on 2010-09-14
Just one further thing. Lucid Lynx will run the display on the Inspiron 15R in the most basic mode -- not well at all.  Fedora 13 runs the display nicely, sharp and clean.  So if anyone would want to progress this (Ubuntu on Inspiron 15R), that person would have to get involved in researching and manually installing the driver (I would suggest trying Fedora 13 as I did to see what goes on there).

---

### Post by uRock on 2010-09-14
Posting in the [Dell sub-forums]("http://ubuntuforums.org/forumdisplay.php?f=342") might bring better help, as the people who read those threads know more about dell and ubuntu compatibility issues.

---

### Post by jasminetea on 2010-09-14
> **uRock said:**
> Posting in the [Dell sub-forums]("http://ubuntuforums.org/forumdisplay.php?f=342") might bring better help, as the people who read those threads know more about dell and ubuntu compatibility issues.

It's not just a Dell laptop issue. It applies to all laptops which which have a touchpad which is not recognised by the synaptic touchpad driver (and hence by gnome), but recognised only as a standard generic PS/2 mouse.  I did post this issue into the Dell sub-forum with a link back to this thread yesterday.

---

### Post by Slade Winstone on 2010-09-18
Hi again Jas,

Hey, I picked up a 15R today.  Its a NZ model, the i5-540 with dedicated ATI 1GB.  

Anyhow, the strange thing is that it does have a Touchpad tab under the Mouse Preferences!

I did a clean install of Lucid 10.04.1 and ran all the updates.  

So, its VERY strange if you have a new 15R, that you don't have that tab.  Is there anything I can check on my laptop to help out?

Slade.

---

### Post by jasminetea on 2010-09-19
Slade -

Could be model 1545

Ordered as Inspiron 15R

Label on back: 

Ref Number 08225
Model No: PP41L

Further down - Inspiron 1545

What does yours say on the label on the back.  No model number on front (apart from "Inspiron").

I get the impression "15R" as advertised may cover more than one model.  This could be true, where the actual specification is the same.

---

### Post by Slade Winstone on 2010-09-20
Hi Jas,

I have an Inspiron N5010.
Reg. Model: P10F
Reg. Type Number: P10F001

I know that the N5010 is the international name for the 15R.

Your 1545 is an Inspiron 15.

Have you had anymore luck with it?  Is there anything I can lookup, on my machine?  Maybe try some searches with the 1545 as the model number?

Slade.

---

### Post by Slade Winstone on 2010-09-20
Hi again Jas,

Looks like there are a LOT of people having problems with that Alps touchpad on the 1545.  If you ordered a 15R (N5010), I'd go back to Dell and get them to ship the right model.

I have a 15R and no real problems with the touchpad.

Try a quick google for "1545 ubuntu touchpad", and you'll see what I mean.

Slade.

---

### Post by stratosvoukel on 2010-12-04
Hey guys, I have recently bought an Dell Inspiron 15R and I have some major problems with the touchpad. Even though it is recognised I cant do anything other than one finger operations. When I try to use more than one fingers the cursor goes crazy and starts going from one random point to another. As a result I cant scroll etc., any ideas?

---

### Post by Slade Winstone on 2011-05-27
Sorry, but the 15R (at least my now slightly older model) doesn't support multi-touch on the trackpad.

---

### Post by Nayar on 2011-07-11
Is the 15R and Inspiron N5010 the same laptop with different names?

I can use 2 fingers to scroll since Ubuntu 11.04 Beta 1.

---

