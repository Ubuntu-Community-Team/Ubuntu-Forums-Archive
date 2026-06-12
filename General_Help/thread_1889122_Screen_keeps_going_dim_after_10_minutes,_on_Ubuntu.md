---
title: "Screen keeps going dim after 10 minutes, on Ubuntu 11.10"
date: 2011-11-30
forum: General Help
---

### Post by pretty_whistle on 2011-11-30
After no activity the screen dims though I set it not to.

How do I get this to stop?

I have Ubuntu 11.10 and Unity desktop.

---

### Post by gennatolls on 2011-11-30
Could it be some setting in your graphics card's x server settings? I've had problems in the past when (in my case) Nvidia X server settings conflicted with the other gnome/ubuntu apps.

---

### Post by pretty_whistle on 2011-11-30
> **gennatolls said:**
> Could it be some setting in your graphics card's x server settings? I've had problems in the past when (in my case) Nvidia X server settings conflicted with the other gnome/ubuntu apps.
I wonder where to look to find that out.


P.S.  Still luvin your name.  ROF.  :)

---

### Post by pretty_whistle on 2011-11-30
Well, I went to Nvidia X server settings and found nothing there that could cause this.

---

### Post by pretty_whistle on 2011-11-30
I found the solution was to restart the computer for the changed settings to take effect.

---

### Post by gennatolls on 2011-11-30
lol good, I had to think of something to say to your thread after the other day. glad it got fixed.:P

---

### Post by pretty_whistle on 2011-12-01
I was wrong.  That didn't solve it but delayed its occurrence.

Now I'm back where I started....:(.

---

### Post by Frogs Hair on 2011-12-01
Open Screen and check the lock screen time . The default is 10 minutes I think and the screen will go dark when beginning to lock.

---

### Post by pretty_whistle on 2011-12-01
> **Frogs Hair said:**
> Open Screen and check the lock screen time . The default is 10 minutes I think and the screen will go dark when beginning to lock.
I don't want it to lock either.

---

### Post by pretty_whistle on 2011-12-01
I just need my setting to stick.  I set it to 'never' dim the screen.

---

### Post by stinkeye on 2011-12-01
In previous releases this was controlled by DPMS (Energy Star).

It could be turned off with
```
xset -dpms
```

but even if 
```
xset -q
```
shows
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  [COLOR="Red"]DPMS is Disabled[/COLOR]
```
the screen still blanks when idle for 10 mins.
I even uninstalled the screensaver but it still turns off.

---

### Post by pretty_whistle on 2011-12-01
> **stinkeye said:**
> In previous releases this was controlled by DPMS (Energy Star).

It could be turned off with
```
xset -dpms
```

but even if 
```
xset -q
```
shows
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  [COLOR="Red"]DPMS is Disabled[/COLOR]
```
the screen still blanks when idle for 10 mins.
I even uninstalled the screensaver but it still turns off.
It still turns off despite uninstalling that?  That sucks.

---

### Post by stinkeye on 2011-12-02
See if you have any luck with
```
xset s off
```

---

### Post by pretty_whistle on 2011-12-02
> **stinkeye said:**
> See if you have any luck with
```
xset s off
```
That fixed it!

Thanx!
:)

---

### Post by cmcanulty on 2011-12-02
none of that helps mine, always restarts to dimmed

---

### Post by cmcanulty on 2011-12-03
Got it try this post sad that a lame amateur like me has to find this
[http://ubuntuforums.org/showthread.php?p=11510086#post11510086]("http://ubuntuforums.org/showthread.php?p=11510086#post11510086")

---

### Post by stinkeye on 2011-12-03
> **cmcanulty said:**
> Got it try this post sad that a lame amateur like me has to find this
[http://ubuntuforums.org/showthread.php?p=11510086#post11510086]("http://ubuntuforums.org/showthread.php?p=11510086#post11510086")
Sad that your problem is completely different than the problem in this thread.

---

### Post by pretty_whistle on 2011-12-03
Well.......

I just marked this thread as unsolved because the problem came back.

Weird.

---

### Post by stinkeye on 2011-12-03
> **pretty_whistle said:**
> Well.......

I just marked this thread as unsolved because the problem came back.

Weird.
Now that's sad.
:(

---

### Post by ezsit on 2011-12-03
Have you looked into your BIOS yet? Most BIOS contain a power down section for the screen. Its worth a shot.

---

### Post by cmcanulty on 2011-12-03
Mine seems OK I have shut down and restarted and logged in and out several times.

---

### Post by pretty_whistle on 2011-12-03
> **ezsit said:**
> Have you looked into your BIOS yet? Most BIOS contain a power down section for the screen. Its worth a shot.
Dead end.

---

### Post by pretty_whistle on 2011-12-04
What I wonder, since this hasn't been solved, is will the screen dimming cause any program I'm running to suspend itself.  (I had this happen on Windows)

??

---

### Post by cmcanulty on 2011-12-04
That seems unlikely the problem seems to be getting the LCD to be loaded into grub properly at boot. That's why it starts out OK and as boot continues goes dim.

---

### Post by mike555 on 2011-12-04
I got my Xubuntu to not blackout by;

 open leafpad and save this in your home folder as 
.dpms-off
 

Code:


#!/bin/bash
xset -dpms
xset s off


Right click on the saved file
 Properties > permissions
 and mark Execute 

Then right click on the file and copy.
 Open startup applications and paste the file copy as the command. (See pic)don&#8217;t forget dot .
 
Log out/in and in the terminal run 



Code:


xset -q


to check if dpms is disabled.



[IMG]http://i44.tinypic.com/25a83yx.jpg[/IMG]
of course change " mike " to your username

---

### Post by pretty_whistle on 2011-12-04
What about doing it this way?...............
[IMG]http://i41.tinypic.com/rvlwck.png[/IMG]

Notice the checked boxes.  What do I do, uncheck idle dim and idle dim battery?

---

### Post by pretty_whistle on 2011-12-04
I'll try it, unchecking them, and report back once I've tested to see if it worked.

---

### Post by cmcanulty on 2011-12-04
I  had no luck with that

---

### Post by pretty_whistle on 2011-12-04
> **cmcanulty said:**
> I  had no luck with that
I deleted them.  Wonder if that will help.
Probably not.

---

### Post by pretty_whistle on 2011-12-04
So far it's not dimming, but is it solved?  Don't know, considering I thought it was solved before but then the dimming returned.

If it's unpredictable like this the only way I'll have to tell if it's solved is to wait like a week and see.

A week, that's too much, but at this point it's all one can do.........

---

### Post by pretty_whistle on 2011-12-06
Instead of dimming every 10 it now dims after a half hour.

---

### Post by cantenna on 2011-12-13
*Reposting* This solved my problem with screen dimming interrupting movie
			 		   		 		 		
Also, xbmc crash if launched from gnome 3 ubuntu 11.10.

workaround, 

install xbmc standalone script and launch from logon

install xbmc
follow/install xbmc standalone script

then change to

[Desktop Entry]
Name=XBMC
Comment=This session will start XBMC Media Center
Exec=xbmc
TryExec=xbmc
Type=Application

**change xbmc-standalone to xbmc in Exec & TryExec, otherwise  workaround below will not work and your screen turns off during movie**

 	Quote:
 	 	 		 			 				 					Originally Posted by **cantenna** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11534510#post11534510") 				
 				[I]Greetings!:grin:

Solved this problem by,

Open Terminal and paste:

cd /etc/X11/xinit

sudo gedit xinitrc 

**(Now change contents of xinitrc file to**

#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
setterm -blank 0 -powersave off -powerdown 0
xset s off
. /etc/X11/Xsession[/I]

---

### Post by pretty_whistle on 2011-12-13
> **cantenna said:**
> *Reposting* This solved my problem with screen dimming interrupting movie
                                                  
Also, xbmc crash if launched from gnome 3 ubuntu 11.10.

workaround, 

install xbmc standalone script and launch from logon

install xbmc
follow/install xbmc standalone script

then change to

[Desktop Entry]
Name=XBMC
Comment=This session will start XBMC Media Center
Exec=xbmc
TryExec=xbmc
Type=Application

**change xbmc-standalone to xbmc in Exec & TryExec, otherwise  workaround below will not work and your screen turns off during movie**
_____________________________________________________
     Quote:
                                                                      Originally Posted by **cantenna**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11534510#post11534510")                 
                 [I]Greetings!:grin:

Solved this problem by,

Open Terminal and paste:

cd /etc/X11/xinit

sudo gedit xinitrc 

**(Now change contents of xinitrc file to**

#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
setterm -blank 0 -powersave off -powerdown 0
xset s off
. /etc/X11/Xsession[/I]
Everything above the line I drew in your post I didn't understand.  The rest I was able to get done.

??

---

### Post by cmcanulty on 2011-12-14
I would also like a beginners explanation as I am dealing with library computers and can't screw them up. I want something that keeps screen all the way bright for all users with nothing needed to be done after it is set up. Thank you. This is a widespread bug with 11.10 upgrade and really causes problems as some screens are so dim you can't even access the system tools as the mouse is not visible.

---

### Post by pretty_whistle on 2011-12-14
> **cmcanulty said:**
> I would also like a beginners explanation as I am dealing with library computers and can't screw them up. I want something that keeps screen all the way bright for all users with nothing needed to be done after it is set up. Thank you. This is a widespread bug with 11.10 upgrade and really causes problems as some screens are so dim you can't even access the system tools as the mouse is not visible.
I second that.

---

### Post by pretty_whistle on 2011-12-14
I just tried an idea-so far, so good.  I've tested it twice and it's still working.  Here's what I did:

-Go to system settings>screen.  Check the box where it says "Dim screen to save power"
-Restart computer.
-Go to screen again and see if it's still checked to dim screen.  It should be.
-Now uncheck to dim it.
-Restart computer.
-Go to screen again and see if it's still unchecked.  It should be.

That's it.

My thought was that maybe it needed to be reset.

P.S.  I am using Gnome Classic desktop but that shouldn't matter.  I had unity when I started this thread, FWIW.

---

### Post by cantenna on 2011-12-14
Hi there:
[U]To elaborate on my earlier post,

[/U]I also use XBMC as a media center on my 11.10 Ubuntu install.

XBMC and Boxee have known bugs where they crash on start if launched through the latest gnome on ubuntu 11.10

There are tutorials in which you can add XBMC and Boxee to the logon screen which gets you around the startup bug from within gnome, however, the screen will still dim after 10 min's into watching your movie because of this bug

In order to add xbmc to login you need to install an xbmc standalone script. 
which add an entry to xsessions (XBMC.desktop)

XBMC.desktop entry calls for XBMC-standalone. You want to change to just XBMC if you don't want the screen to go black after 10 mins.

---

### Post by cantenna on 2011-12-15
o display> **pretty_whistle said:**
> Everything above the line I drew in your post I didn't understand.  The rest I was able to get done.

??

Did it fix the problem?

Did for me. its a script that disables all power save options related to display.

---

### Post by pretty_whistle on 2011-12-15
> **cantenna said:**
> o display

Did it fix the problem?

Did for me. its a script that disables all power save options related to display.
No, I still had the problem (I couldn't do all of it and that's probably why)....until I did what I posted above in post #36.

---

### Post by pretty_whistle on 2011-12-15
Well.... it dimmed anyway!

It dims at varied times so there's no pattern to it, which means if you think it's not doing it again you could be way off.

I was way off.

I am giving up trying to resolve it.  It's a stubborn feature, if that's what it meant to be, or a stubborn bug.

:(

---

### Post by cmcanulty on 2011-12-18
I guess I am about done with Ubuntu I volunteer at our library and run 10 ubuntu laptops but since 11.10 upgrade it is a full time job to keep them from going black, printing etc it has turned to total ***. I am spending about full time and still screen constantly turns black, won't print ad nauseum. I have stopped recommending it to anyone. I tried xfce and kde and they all turn black constantly which requires the librarian to get up and restart each one. I am so steamed and disappointed with all the time I spent learning ubuntu to have it end like this.I have googled for weeks and tried everything but this is too much of a mess for our patrons.I am in working on sunday and again everything turns black. Screen dimming resets itself constantly. I would try another linux distros but this has totally soured me on linux.Maybe if an admin helped it wouldn't be so frustrating. I have wasted an entire weekend again trying to make it work with no luck,. and now I am stuck until I waste another several days going back to win7 and reconfiguring everything.Does Ubuntu realize how many people they lose by releasing distros that are no where near ready!!!I guess this will be deleted *** too negative but how much time is reasonable to make something work?

---

### Post by mike555 on 2011-12-18
Did you try what I posted (#25)  it has worked for me on many xubuntu computers

---

### Post by cmcanulty on 2011-12-18
I think so but I tried so many things I get mixed up. Today I figured I had it. I did the 2 fixes here and by the time I did all 10 on both users they were black again. Power button still lit and I can see it there barely but not enough to see a cursor. Won't wake without a restart
[http://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management]("http://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management")

---

### Post by mike555 on 2011-12-18
> **cmcanulty said:**
> I think so but I tried so many things I get mixed up. Today I figured I had it. I did the 2 fixes here and by the time I did all 10 on both users they were black again. Power button still lit and I can see it there barely but not enough to see a cursor. Won't wake without a restart
[http://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management]("http://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management")

    I too tried many fixes till I did this one that I posted ....... it's a bit of work but worth it.

---

### Post by cmcanulty on 2011-12-18
I will try it next time I go in thanks. I am pretty discouraged and ave to get this fixed fast or they will insist goodbye ubuntu and I wouldn't blame them this is extremely irritating

---

### Post by cmcanulty on 2011-12-19
Does your fix need to be set up with both users? And will it automatically start for all users?

---

### Post by 2009Prius on 2011-12-19
I would like to turn off the screen dimming "feature" as well. Just went through the entire thread and no definite solution it seems. :(

---

### Post by D_E_H0987 on 2011-12-19
I have noticed a small qwerk in screen or power saver features that mite help you guys figure this out.

What hapens on my system with ubuntu 11.10 is if I start ubuntu and don't run anything right away the video will shut off.

Now if I run an app or do anything on the system right away this will not happen.

I have my bios set to disable all power saver modes (I shut off my systems when I'm not going to be using them, and shut off the monitor if I have something running but won't be looking at the screen for a while.).   

I have power settings off in ubuntu.  

I have screen saver off. 

Once it goes into this video off mode it will shut off video after a while of unactivity and will continue to do so even if you go in and change the power saver and screen saver functions.

Only way to turn this off is to shut down restart and then do something on the machine right away.

Then the system will follow the power and screen saver settings like it should.


What I think is happening(this is a guess, but windows does this so....) is that ubuntu is now doing as windows does and turning on the BIOS power saver functions at startup and then not turning them off unless you use the system right away.

Some BIOS have a setting to shut off reconfiguring the BIOS from the operating system which I think would be a work around on this bug, but this board doesn't have it.

Anyway this mite help you guys figure what has been changed.

---

### Post by 2009Prius on 2011-12-19
I have to agree with an earlier poster that forcing innocent beginners to deal with this kind of bugs is really bad PR. Maybe Linux is **only **for geeks after all?

---

### Post by cmcanulty on 2011-12-19
Our computers do this constantly and not while watching video. I also have turned off all powersaver and screensavers and even edited grub and some other files but no fix in sight.

---

### Post by mike555 on 2011-12-26
> **cmcanulty said:**
> Does your fix need to be set up with both users? And will it automatically start for all users?

   Yes, needs to be done for all users ,because your saving the " .dpms-off " file in the /home folder.
   It will automatically start if you put it in the startup list as directed.

 I have used this cure on 6 different xfce installs with success .

---

### Post by salmanahmedtariq on 2012-10-14
this will help also for ubuntu

please visit
[http://xubuntugeek.blogspot.com/2012_01_01_archive.html](http://xubuntugeek.blogspot.com/2012_01_01_archive.html)

---

