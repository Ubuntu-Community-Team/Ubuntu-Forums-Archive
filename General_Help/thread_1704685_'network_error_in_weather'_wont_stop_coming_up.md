---
title: "'network error in weather' wont stop coming up"
date: 2011-03-11
forum: General Help
---

### Post by mons00n on 2011-03-11
I found that indicator-weather was taking up a huge amount of memory recently so I removed it via:

apt-get remove indicator-weather

I then started to get periodic indicator messages saying 'Network error in weather", so I reinstalled the indicator applet and the messages continue!  Has anyone run into this before and have a possible solution?  Thanks!

---

### Post by sjalv on 2011-03-11
I have the same problem in Maverick, fresh install. I haven't changed or removed any indicators and I still get it even though I don't have any connection issues and the weather updates itself just fine. This is annoying as I'm using a netbook and the recurring notifications eat the screen estate quite effectively. 

Don't know how to get rid of this, hopefully someone does. :)

---

### Post by mons00n on 2011-03-11
yea it's starting to drive me nuts.  I've removed and reinstalled all of the misc weather items in the package manager and it just wont go away.  I'm not even sure where to look.

---

### Post by Mikux on 2011-03-11
Having the same issue on a relatively new install of Maverick.  No connectivity issues, weather updates fine on both my Gnome Panel and AWN Dock, but still getting a constant "Network Error In Weather" notification.

Removing the weather indicator doesn't seem to fix it, nor does deleting the Gnome Panel.

---

### Post by Reaved on 2011-03-11
I'm having the same issue with an older install of Maverick and it only started a few days ago. Even with an update I just installed it still happens. Mine updates just fine as well. Maybe weather.com changed something on their end?

version is 0.4.1~bzr822+201102140003~maverick1
from repository: [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu)

---

### Post by MrGrey1 on 2011-03-11
Same problem, network is fine but keep getting this error coming up. No memory issues though.

---

### Post by Rasa1111 on 2011-03-11
Mine just started doing it a few days ago also. 

I was running the weather applet from AWN.

Earlier though, I removed the applet from my AWN dock,
and havent seen it come up since.

So i just added the weather indicator to my top panel, about 20 minutes ago..
we'll see if it comes back up.. lol

---

### Post by mons00n on 2011-03-11
> **Rasa1111 said:**
> Mine just started doing it a few days ago also. 

I was running the weather applet from AWN.

Earlier though, I removed the applet from my AWN dock,
and havent seen it come up since.

So i just added the weather indicator to my top panel, about 20 minutes ago..
we'll see if it comes back up.. lol

Interesting, I'll remove my AWN applet as well and see if that solves the problem.  Does everyone having this problem also use the AWN weather dock app?

---

### Post by Rasa1111 on 2011-03-12
Well,

 Since I removed it from AWN,
and put the "weather report" one into the top panel..
the error message has not come back up! :)

hmmm....

---

### Post by Mikux on 2011-03-12
Was also using Awn (Testing).  Have just removed my weather applet, so we'll see.

---

### Post by mons00n on 2011-03-12
I haven't seen the message since I removed the AWN weather applet.

---

### Post by sjalv on 2011-03-12
Yup, using AWN too and its' weather applet seems to be the culprit. I played with Gwibber too and every time I got Gwibber notifications, the weather error popped up as the last notification in the series. So I removed the weather applet and waited for Gwibber notifications -> no weather error. Then I added the weather applet back to the dock -> got the error immediately.

edit: I tried to find the weather update interval settings so I could test it more, but the AWN applet and the panel indicator don't have them. I'm guessing the interval is set somewhere in  Gnome settings. Or maybe they use the Gwibber interval settings as default if they are set? Dunno.

---

### Post by ToasterThief on 2011-03-12
Can confirm that it's the AWN weather applet. Seems like it's polling like crazy. It still works through. I'll file a bug report.

---

### Post by Rasa1111 on 2011-03-12
Yep,
 havent seen it still,
since removing the AWN applet. 

I just noticed awhile ago though that there were a few AWN updates in update manager when it came up..
So maybe that had a fix.. I dunno..
 Guess Ill add it back to AWN and see if it still happens., lol

edit:
 Nope, nevermind.
Just added it back to AWN, and less than a minute later..
the "network error in weather" has returned, 3 times! lol  :rolleyes:

---

### Post by Kir_B on 2011-03-12
+1 - Add me to the boat.

I am also using the AWN testing (love it!).

The other day I was trying to figure out what has been mysteriously eating small bits of my bandwidth and in the course of trying things, I removed the weather applet, found no difference in bandwidth usage and so I put the applet back.

Shortly after that, I began getting the messages.

I'm not sure if the removal and replacement of the weather applet had anything to do with it, but the timing would suggest that it may have.

Good luck all.
Kirby

---

### Post by Mikux on 2011-03-12
Removing the AWN applet also fixed the problem for me.  It seemed to have been working just fine up until a few days ago.  A little frustrating since I prefer not to use a Gnome Panel, and would rather not go the screenlets/widgets route to display the weather on my desktop.

---

### Post by sites on 2011-03-13
This has been annoying me for several days.  Removing/replacing it in the dock didn't fix it for me.

---

### Post by nmcgrew on 2011-03-14
same issue w/ the weather error pop-up notice.

---

### Post by SonicSteve on 2011-03-14
I also use awn though not the testing branch. I'm running 0.4.0

Same error, I just removed the weather applet because my patience ran out. I'll post if I see the message again.

EDIT
2+ hours no more messages.

EDIT

It seems that we're all running different versions of AWN, I think an update in the Gnome desktop must have broken this otherwise some versions of AWN would be affected not all versions.

---

### Post by graphius on 2011-03-15
Any further info on this? It does seem to be the awn applet, and it does seem to have started after an update, either to awn or gnome.

---

### Post by Ertepeller on 2011-03-16
I suspect the problem is the satellite map ("Show map" in the context menu is greyed out), because the other stuff (temperature & forecast) seems to work fine. 

So the "network error" might be the fact that the applet can't retrieve the map image. So what, I never look at it. 

But the popup every few minutes is driving me mad :) Very, VERY irritating.

Solution seems obvious: disable the notification in the weather applet and my blood pressure will return to a more healthy level.

You have to edit this file: /usr/share/avant-window-navigator/applets/weather/weather.py 
(The file is only writable by root, so remember to use sudo when you start your editor)

And comment out the notification call in line #240 (by putting a "#" before "self.notification.show")

Result should look like this:
```
    
    def network_error_cb(self, e, tb):
        if type(e) is NetworkException:
            print "Error in Weather:", e
#           self.notification.show()

```Then kill the weather applet:
```

ubuntu@ubuntu:~$ ps aux | grep weather.py
root      9559  0.0  0.2 234080 10792 pts/0    Sl+  03:33   0:00 vim weather.py
ubuntu    9630  0.0  0.8 424132 32316 ?        Sl   03:36   0:00 python /usr/share/avant-window-navigator/applets/weather/weather.py --uid=9 --window=23068717 --panel-id=1
ubuntu    9684  0.0  0.0   8956   872 pts/1    S+   04:00   0:00 grep --color=auto weather.py
ubuntu@ubuntu:~$ kill 9630
ubuntu@ubuntu:~$ 
```And restart the applet by clicking on it.

I haven't seen the obnoxious popup since. Yay!

---

### Post by graphius on 2011-03-16
Thanks, this seems to have fixed it for me as well.
 I am guessing the satellite maps are no longer available, or have changed in some way that broke the applet.

---

### Post by swiftsam on 2011-03-16
I'm seeing the same error.  This thread on the AWN forums seems to identify the problem.  Nobody seems to have said a developer is working on a fix or anything though

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2540&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2540&page=1&isLive=true)

---

### Post by Gunnodayak on 2011-03-16
Same problem here, I am a newbie in Ubuntu, and these are the kind of problems that are forcing me to keep a dual boot system (Windows 7/Ubuntu 10.04).

---

### Post by Rasa1111 on 2011-03-16
> **Gunnodayak said:**
> Same problem here, I am a newbie in Ubuntu, and these are the kind of problems that are forcing me to keep a dual boot system (Windows 7/Ubuntu 10.04).

There are other methods of getting weather on ones desktop.
Conky and gnome-panel are 2 other methods....

Ubuntus weather apps work fine.
its AWN that has gone a lil whacky..
Not Ubuntu..

---

### Post by Ertepeller on 2011-03-16
> **Rasa1111 said:**
> There are other methods of getting weather on ones desktop.
Conky and gnome-panel are 2 other methods....

Ubuntus weather apps work fine.
its AWN that has gone a lil whacky..
Not Ubuntu..

But I don't use conky or gnome-panel... just AWN. 

Conky is nice for showing off with screenshots, but useless for normal daily usage. Simply because you don't see it. I don't see even one pixel of the background, it's always covered with windows.

And I replaced gnome-panel with AWN, it doesn't even run. It's redundant when you have AWN running. My screen is only 900 pixels high and I don't want to waste any pixels (especially vertically) on some toolbar I don't use.

---

### Post by Gunnodayak on 2011-03-16
> **Rasa1111 said:**
> There are other methods of getting weather on ones desktop.
Conky and gnome-panel are 2 other methods....

Ubuntus weather apps work fine.
its AWN that has gone a lil whacky..
Not Ubuntu..

I know that there are alternatives, but I hate this thing about Ubuntu as a principle: today one thing is working, and tomorrow, for instance after some updates, it is not working anymore. I've experienced this problem in Ubuntu more than one time, this Weather issue in AWN is just one of them. The best thing in all the bad ones is that there's a strong and helpful community around here and I really appreciate that from Ubuntu experienced users.
I am really hoping that Ubuntu and the software for Ubuntu will get better in time (and more than better, more casual user friendly), because I really want to get rid of Windows completely.

---

### Post by Rasa1111 on 2011-03-16
> But I don't use conky or gnome-panel... just AWN. 

Conky is nice for showing off with screenshots, but useless for normal daily usage. Simply because you don't see it. I don't see even one pixel of the background, it's always covered with windows.

And I replaced gnome-panel with AWN, it doesn't even run. It's redundant when you have AWN running. My screen is only 900 pixels high and I don't want to waste any pixels (especially vertically) on some toolbar I don't use.


Gotcha.

 I do use (look at) my conky quite often though. 
on a 'normal,daily' basis. 
and find it quite useful.

Least you got your AWN fixed now though, yea?

---

### Post by Rasa1111 on 2011-03-16
> **Gunnodayak said:**
> I know that there are alternatives, but I hate this thing about Ubuntu as a principle: today one thing is working, and tomorrow, for instance after some updates, it is not working anymore. I've experienced this problem in Ubuntu more than one time, this Weather issue in AWN is just one of them. The best thing in all the bad ones is that there's a strong and helpful community around here and I really appreciate that from Ubuntu experienced users.
I am really hoping that Ubuntu and the software for Ubuntu will get better in time (and more than better, more casual user friendly), because I really want to get rid of Windows completely.


 I understand.

 but honestly..
 I experienced these same kinds of thing when i used to use windows also.

and really..
Ive had far less issues with Ubuntu in the year Ive been using it, than I ever had with windows in a year.  lol

 I think you will be able to ditch windows soon enough.

---

### Post by Ertepeller on 2011-03-16
> **Rasa1111 said:**
> Gotcha.

 I do use (look at) my conky quite often though. 
on a 'normal,daily' basis. 
and find it quite useful.

Least you got your AWN fixed now though, yea?

I should have said "MY normal daily usage", because it's just an opinion of course. :)

I did use conky in the past, spent hours and hours to come up with the ultimate conkyrc (for me), but after that... I actually almost never looked at it :) 

So I don't bother install it anymore. The few times I want to know what's eating cpu cycles or filling up memory I fire up Gnome System Monitor which shows everything I want to know in great detail (more than conky in fact).

Well at least conky was fun to play with, learned a few useful things from it and one more package under my belt I'd say.

---

### Post by jasonhaley on 2011-03-16
Just so everyone knows: I just updated my AWN system today. The problem seems to have gone away.

So I think they fixed the bug and pretty quickly.

---

### Post by Vaphell on 2011-03-16
i think it was related to the map you can show in rightclick menu. When the error was occuring on last few days it was grayed out/unavailable. Maybe weather.com changed the feed parameters recently or something and the applet failed to download that map, thus displaying the error message?
indeed, recent updates of awn fixed the issue.

---

### Post by swiftsam on 2011-03-17
It's fixed for me as well after an update.  thanks AWN team!

---

### Post by Gunnodayak on 2011-03-17
I still have the problem, and I don't know how to make that damn update you were talking about. I don't know the meaning of the term "update" in Ubuntu, OK, I update my software in Ubuntu via Update Manager or via Ubuntu Tweak, but I don't know how to update AWN manually. Removing it and reinstalling? Or how?
Any help would be really appreciated.

---

### Post by Rasa1111 on 2011-03-17
> **Gunnodayak said:**
> I still have the problem, and I don't know how to make that damn update you were talking about. I don't know the meaning of the term "update" in Ubuntu, OK, I update my software in Ubuntu via Update Manager or via Ubuntu Tweak, but I don't know how to update AWN manually. Removing it and reinstalling? Or how?

Check your "update manager".
The updates for AWN should be in there. 

Once I saw (from this thread), that there were updates available for it, I opened update manager to see, and sure enough..
the only updates it found were for AWN.

Dont have to "update manually".

---

### Post by Gunnodayak on 2011-03-17
> **Rasa1111 said:**
> Check your "update manager".
The updates for AWN should be in there. 

Once I saw (from this thread), that there were updates available for it, I opened update manager to see, and sure enough..
the only updates it found were for AWN.

Dont have to "update manually".


Thank you, Rasa111, you're a good fellow for trying to help me, but ti doesn't work for me. I don't have any AWN update, altough I have enabled Awn-Core PPA in Ubuntu Tweak/Source Center. Here's my sources list, just for reference:
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) lucid main ## Cairo-Dock-PPA-Stable
 

I also have 
deb [http://ppa.launchpad.net/awn-core/ppa/ubuntu](http://ppa.launchpad.net/awn-core/ppa/ubuntu) lucid main #Awn-Core PPA
and 
# deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) lucid main #Awn Testing Team PPA


I seem to have AWN 0.4.0 installed on my PC
Show map is not working also, but it's not grayed out.

---

### Post by ndstate on 2011-03-17
Mine is also not updating and I am still having the problem

---

### Post by Rasa1111 on 2011-03-17
dang, sorry bout that. 

Only thing I can think to suggest..
Is to try AWN Trunk, rather than the AWN in the repos/software center. 

got it's own PPA~ 

Install~ [http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)

 A simple command to remove the current AWN you have,
and 2 other commands, and your good to go.

Sorry I cant think of anything else...

---

### Post by jasonhaley on 2011-03-18
You guys may also need to restart AWN or your whole system after the update. :D

---

### Post by Rasa1111 on 2011-03-18
yeah that might help.
my AWN weather is working alright now.
I saw a handful more updates for AWN in update manager today to.

---

### Post by Tanker Bob on 2011-03-19
> **Rasa1111 said:**
> dang, sorry bout that. 

Only thing I can think to suggest..
Is to try AWN Trunk, rather than the AWN in the repos/software center. 

got it's own PPA~ 

Install~ [http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)

 A simple command to remove the current AWN you have,
and 2 other commands, and your good to go.

Sorry I cant think of anything else...

After following the instructions on the PPA page and restarting my system, all is good. Thanks for the help!

---

### Post by Rasa1111 on 2011-03-19
Very good!
Glad to hear it. :)
No problem. :)

---

### Post by shenmeister on 2011-04-05
> **Ertepeller said:**
> I suspect the problem is the satellite map ("Show map" in the context menu is greyed out), because the other stuff (temperature & forecast) seems to work fine. 

**You have to edit this file: /usr/share/avant-window-navigator/applets/weather/weather.py** 
(The file is only writable by root, so remember to use sudo when you start your editor)


I didn't feel like adding another PPA or ignoring error messages, so I went hunting for the offending lines in the file and manually updated them. It turns out that it's just two lines.

Line 620:
```
map_url = "http://www.weather.com/outlook/travel/businesstraveler/map/%s" % location_code
```
needs to be changed to:
```
map_url = "http://www.weather.com/weather/map/%s" % location_code
```
Line 622:
```
mapExp = """<IMG NAME="mapImg" SRC="([^\"]+)" WIDTH=([0-9]+) HEIGHT=([0-9]+) BORDER"""
```
needs to be changed to:
```
mapExp = """<img name="mapImg" src="([^\"]+)" width="([0-9]+)" height="([0-9]+)" border"""
```

Then just make sure you restart AWN. I've only recently installed AWN 0.4.0 from the official Lucid repository, so I'm not sure what type of maps the Weather applet used to display. All I know is that instead of getting that error message and no maps, I now get a nice satellite map with no errors. 

If you're not comfortable editing code, DON'T TRY THIS. Hope this helps.

---

### Post by MrGrey1 on 2011-04-05
> **shenmeister said:**
> I didn't feel like adding another PPA or ignoring error messages, so I went hunting for the offending lines in the file and manually updated them. It turns out that it's just two lines.

Line 620:
```
map_url = "http://www.weather.com/outlook/travel/businesstraveler/map/%s" % location_code
```
needs to be changed to:
```
map_url = "http://www.weather.com/weather/map/%s" % location_code
```
Line 622:
```
mapExp = """<IMG NAME="mapImg" SRC="([^\"]+)" WIDTH=([0-9]+) HEIGHT=([0-9]+) BORDER"""
```
needs to be changed to:
```
mapExp = """<img name="mapImg" src="([^\"]+)" width="([0-9]+)" height="([0-9]+)" border"""
```

Then just make sure you restart AWN. I've only recently installed AWN 0.4.0 from the official Lucid repository, so I'm not sure what type of maps the Weather applet used to display. All I know is that instead of getting that error message and no maps, I now get a nice satellite map with no errors. 

If you're not comfortable editing code, DON'T TRY THIS. Hope this helps.

Worked a treat. Got the map back which I think has been missing for some time before the errors started as well. Thanks.

---

### Post by shenmeister on 2011-04-05
Glad to help. I guess weather.com updated their website, which necessitated the change in the applet. Since I made my post, I went ahead and upgraded my version of AWN to the awn-testing PPA, despite my earlier hesitation. Generally I don't add non-stable PPA's, but there were some nifty new features in the testing version. Anyways, the weather applet has been updated to work, but they didn't change the 1st line that I changed. It seems the original URL still redirects properly. It was just a matter of updating the 2nd line to correct for the image parsing.

---

### Post by Kaiel on 2011-04-08
> **swiftsam said:**
> I'm seeing the same error.  This thread on the AWN forums seems to identify the problem.  Nobody seems to have said a developer is working on a fix or anything though

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2540&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2540&page=1&isLive=true)


I changed "/usr/share/avant-window-navigator/applets/weather/weather.py" and now the applet is working fine for me.

Here is my [weather.py]("http://www.mediafire.com/?twtbvyy39wcqldq")

---

### Post by shimoda on 2011-05-09
> **shenmeister said:**
> I didn't feel like adding another PPA or ignoring error messages, so I went hunting for the offending lines in the file and manually updated them. It turns out that it's just two lines.

Line 620:
```
map_url = "http://www.weather.com/outlook/travel/businesstraveler/map/%s" % location_code
```
needs to be changed to:
```
map_url = "http://www.weather.com/weather/map/%s" % location_code
```
Line 622:
```
mapExp = """<IMG NAME="mapImg" SRC="([^\"]+)" WIDTH=([0-9]+) HEIGHT=([0-9]+) BORDER"""
```
needs to be changed to:
```
mapExp = """<img name="mapImg" src="([^\"]+)" width="([0-9]+)" height="([0-9]+)" border"""
```

Then just make sure you restart AWN. I've only recently installed AWN 0.4.0 from the official Lucid repository, so I'm not sure what type of maps the Weather applet used to display. All I know is that instead of getting that error message and no maps, I now get a nice satellite map with no errors. 

If you're not comfortable editing code, DON'T TRY THIS. Hope this helps.

thanks, also worked for me... :)

---

### Post by cpsully69 on 2011-05-10
Thank you, shenmeister!!!
I'm just starting to learn python, it's kinda cool to see it in action.  I hope to be able to contribute help like you someday!

---

### Post by pakito15191 on 2011-05-25
I know this is an Ubuntu forum, and I had this same trouble in there
Just today I've switched from a broken Ubuntu 11.04 to Fedora 15, and I had the same problem! So I decided to solve it, and luckily (well, thanks to shenmeister) I could fix it.

There's just one little difference, in Fedora that bits of code are at the lines 649 and 651

---

### Post by Simstud on 2011-06-02
Thank you, Ertepeller! That patches it! Now lets hope someone fixes it!

---

### Post by SirPaPa on 2011-07-21
Mark it as **solved** for now

---

### Post by wujastyk on 2011-08-26
Worked for me.  Thanks!
Dominik

---

### Post by BrainwreckedTech on 2011-10-19
This is just begging for some sed.  :)

I took a look at the script, and there's no other occurrence of "outlook" so...

```
sed -i 's/outlook\/travel\/businesstraveler/weather/g' \
/usr/share/avant-window-navigator/applets/weather/weather.py
```

There's also no other occurrence of the ALL-CAPPED HTML, but there are some added quotes for width and height, so...

```
sed -i 's/IMG/img/g' /usr/share/avant-window-navigator/applets/weather/weather.py 
sed -i 's/SRC/src/g' /usr/share/avant-window-navigator/applets/weather/weather.py
sed -i 's/NAME/name/g' /usr/share/avant-window-navigator/applets/weather/weather.py
sed -i 's/WIDTH=/width="/g' /usr/share/avant-window-navigator/applets/weather/weather.py
sed -i 's/ HEIGHT=/" height="/g' /usr/share/avant-window-navigator/applets/weather/weather.py
sed -i 's/ BORDER/" border/g' /usr/share/avant-window-navigator/applets/weather/weather.py
```

---

### Post by nolajohn on 2011-10-19
Thank you shenmeister! Worked perfectly and had been driving me crazy.

---

### Post by shenmeister on 2011-10-19
You're welcome! I agree that this thread should be marked as solved.

---

### Post by MrGrey1 on 2011-11-06
Well... mine is broken again. Thought an update must have reset the modified lines so went looking through weather.py again but the modified lines have moved and appear to be as previously entered. But no worky any longer?

Anyone else broken again?

---

### Post by shenmeister on 2011-11-06
If you mean that no weather conditions are showing up in the applet, then mine is also broken. I still get the weather maps without problem,  but I no longer get the current weather or 5-day forecast. I'm pretty sure this is a result of weather.com retiring their free XML feed and now deciding to charge a fee for a similar service. As such, the partner and license keys that the weather applet uses to request XML feeds from weather.com are no longer valid. Here's a little snippet from the weather.com API FAQ:

> [COLOR=#000000][FONT=Times New Roman][COLOR=#2C2C2C][FONT=Arial]**Why is the weather.com XML Data Feed being retired?** 

[FONT=Verdana]The weather.com XML Data Feed was originally launched in 2003 as a non-commercial, personal use, offering that developers could use to incorporate weather data into their website. In return, The Weather Channel would receive logo attribution and links back to [/FONT][[FONT=Verdana]www.weather.com[/FONT]]("http://www.weather.com/")[FONT=Verdana].  It was one of the first offerings made available to webmasters and developers from The Weather Channel. Since that time, the Internet has evolved, mobile use has exploded, and The Weather Channel has launched a plethora of products to address this market including our [/FONT][[FONT=Verdana]Weather On Your Website (or WOWs) JavaScript modules[/FONT]]("http://www.weather.com/services/oap.html")[FONT=Verdana] and our AddThis Flash modules. _***Both are available for free from The Weather Channel and can be used to present weather data on a website***_. As such we are retiring the weather.com XML Data Feed. Our new offering, The Weather Channel API, is specifically structured for commercial use. Subscribers to this offering may choose to use it on the world wide web, in downloadable Web or PC desktop applications, on the mobile web, or in downloadable mobile phone or smart phone applications or any combination thereof.   For more information on our free offerings, please go to [/FONT][[FONT=Verdana]www.weather.com/services/weather-gadgets[/FONT]]("http://www.weather.com/services/weather-gadgets")[FONT=Verdana].[/FONT]
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Shocker on 2011-11-06
Noticed it coming up again after the radar map fix...

As far as I understood, it seems that the awn weather applet is not under development anymore.

Would there be any way to update with a different service?

Please advise!

---

### Post by naurus on 2011-11-07
[http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap](http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap)

Check out that link. The license the applet was using is expired. So I created a new one :D I have no idea how long it will last.

Change line 606 from
```
__ws_key = "&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap"
```
to
```
__ws_key = "&prod=xoap&par=1287722164&key=e11ec82daa20d876"
```

in [FONT="Courier New"]/usr/share/avant-window-navigator/applets/weather/weather.py[/FONT] and restart avant.

Hope this works for everyone.

---

### Post by Shocker on 2011-11-07
Working great! :popcorn:

Thank you

Shocker

---

### Post by CEB2nd on 2011-11-07
> **naurus said:**
> [http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap](http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap)

Check out that link. The license the applet was using is expired. So I created a new one :D I have no idea how long it will last.

Change line 606 from
```
__ws_key = "&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap"
```
to
```
__ws_key = "&prod=xoap&par=1287722164&key=e11ec82daa20d876"
```

in [FONT="Courier New"]/usr/share/avant-window-navigator/applets/weather/weather.py[/FONT] and restart avant.

Hope this works for everyone.

Works great, thanks.  Still can't get the radar map to work with Ubuntu 11.10. :(

---

### Post by shenmeister on 2011-11-08
> **naurus said:**
> [http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap](http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap)

Check out that link. The license the applet was using is expired. So I created a new one :D I have no idea how long it will last.

Change line 606 from
```
__ws_key = "&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap"
```
to
```
__ws_key = "&prod=xoap&par=1287722164&key=e11ec82daa20d876"
```

in [FONT="Courier New"]/usr/share/avant-window-navigator/applets/weather/weather.py[/FONT] and restart avant.

Hope this works for everyone.
naurus:

Was signing up for the new keys free? I was under the impression that to continue getting the same XML feeds would require a fee.

---

### Post by GaryParr on 2011-11-08
New key works great, thanks!

---

### Post by betete on 2011-11-09
Works great!!!! A few days ago a stopped receiving updates and the applet keep showing nothing. Did the key thing and it works now.

Thanks.

---

### Post by trelirodia on 2011-11-10
Works great! Many thanks

---

### Post by guiliker on 2011-11-11
Thanks for the fix as it has solved my problem too. 

I got it from AWN forums here: [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true)

---

### Post by waster2007 on 2011-11-17
They removed XML Data Feed for free and offering The Weather Channel API for commercial use. Bad news...O_o

[http://feedback.weather.com/knowledgebase/articles/35599-why-is-the-weather-com-xml-data-feed-being-retired](http://feedback.weather.com/knowledgebase/articles/35599-why-is-the-weather-com-xml-data-feed-being-retired)

---

### Post by hpbrantley on 2011-11-17
Yes they removed the XML feed as a free service.  You can get your own partner id and key if you abide by the EULA.

Another note is this still doesn't fix the weather map.  You can get this working again by editing the same script, around line 653.

```
            map_url = "http://www.weather.com/weather/map/%s" % location_code
            with closing(urllib2.urlopen(map_url)) as usock:
                mapExp = """<IMG NAME="mapImg" src="([^\"]+)" WIDTH="([0-9]+)" HEIGHT="([0-9]+)" BORDER"""
                result = re.findall(mapExp, usock.read(), re.IGNORECASE)
```

Couple of things changed in their page. 
1. The url changed.
2. They changed the case of the IMG line to all lower case.  Adding re.IGNORECASE should fix that.
3. They added quotes around the width and height values.

Another way to fix the original problem without using the partner id is to parse the forcast page in this same manner.  I may try that.

---

### Post by BenB1 on 2011-11-18
):P Everyone, hope we're all doing well. :)

> **naurus said:**
> [http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap](http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap)

Check out that link. The license the applet was using is expired. So I created a new one :D I have no idea how long it will last.

Change line 606 from
```
__ws_key = "&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap"
```to
```
__ws_key = "&prod=xoap&par=1287722164&key=e11ec82daa20d876"
```in [FONT=Courier New]/usr/share/avant-window-navigator/applets/weather/weather.py[/FONT] and restart avant.

Hope this works for everyone.

This part works like a charm, thank you.:guitar:

> **hpbrantley said:**
> Yes they removed the XML feed as a free  service.  You can get your own partner id and key if you abide by the  EULA.

Another note is this still doesn't fix the weather map.  You can get  this working again by editing the same script, around line 653.

```
            map_url = "http://www.weather.com/weather/map/%s" % location_code
            with closing(urllib2.urlopen(map_url)) as usock:
                mapExp = """<IMG NAME="mapImg" src="([^\"]+)" WIDTH="([0-9]+)" HEIGHT="([0-9]+)" BORDER"""
                result = re.findall(mapExp, usock.read(), re.IGNORECASE)
```Couple of things changed in their page. 
1. The url changed.
2. They changed the case of the IMG line to all lower case.  Adding re.IGNORECASE should fix that.
3. They added quotes around the width and height values.

Another way to fix the original problem without using the partner id is  to parse the forcast page in this same manner.  I may try that.

This part causes applet to go "crash". :( :-k Also applied revision suggested [here]("http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true#26993") in hopes of being given ability to show map.

After each revision, killed and restarted awn. The first revision solves one part and does so well, again thanks. The next two revisions seem to lead to crashing of the applet. Actually the first in the two, does allow it to remain functional, only not as robustly as desired. And then ... apply a third revision, not hpbrantley's, applet crashes. May be desiring to view a map is too much to query.

Such problems cause me to think outside a bit. Perhaps, this error is on behalf of the service provider and not the applet. We all know web designers are human, too. Humans make mistakes, and with all that code it does seem a possibility. Not accusing or abasing the web developers, merely offering a possibility. 

Is it possible to use another weather content service provider? What process would one use to do so? I think it may resolve around the urls listed in the revisions but am not quite sure, only around 65-75%. That is still too great of a margin for me to consider attempting using different urls for fear and aversion of "Really Mucking Everything Up Royally!(tm)" :)

---

### Post by supergormiti on 2011-12-06
> **naurus said:**
> [http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap](http://xoap.weather.com/weather/local/52806?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap)

Check out that link. The license the applet was using is expired. So I created a new one :D I have no idea how long it will last.

Change line 606 from
```
__ws_key = "&prod=xoap&par=1048871467&key=12daac2f3a67cb39&link=xoap"
```
to
```
__ws_key = "&prod=xoap&par=1287722164&key=e11ec82daa20d876"
```

in [FONT="Courier New"]/usr/share/avant-window-navigator/applets/weather/weather.py[/FONT] and restart avant.

Hope this works for everyone.

Very thanks! Brilliant!

---

### Post by ParadoxBlue on 2011-12-28
> **CEB2nd said:**
> Works great, thanks.  Still can't get the radar map to work with Ubuntu 11.10. :(


This is the one. After ignoring this problem for a couple months I finally sat down today and decided to do something about it. The other fixes didn't work for me but this one did. Now the weather applet is fully functional. Oddly enough though my map always worked properly. I just had no current weather or forecast (only the weather channel logo and a broken connection icon were shown in the dock). I also had the "network error" message popping up all the time.

---

### Post by Pablo Pablovski on 2012-01-11
Looks like the AWN applet's link to the Weather.com API has failed again - I'm back to the old error "connectivity" error message that was fixed by the change to the XML - and no weather forecast. Maybe it's just me...?

Anyone know of a new fix? Further edit to the XML?

---

### Post by kainalu on 2012-01-11
The Weather Channel went to a paid API. The developers now have to pay for access. 

I'm pretty sure this will hose this feature until they change to a new provider. I for one deleted the applet, because the idea of being charged to know the weather is is absolutely stupid to me. That and being told every half hour that it don't know the weather seems silly too.

[http://portal.theweatherchannel.com/](http://portal.theweatherchannel.com/)

---

### Post by Laen on 2012-01-12
> **kainalu said:**
> The Weather Channel went to a paid API. The developers now have to pay for access. 

I'm pretty sure this will hose this feature until they change to a new provider. I for one deleted the applet, because the idea of being charged to know the weather is is absolutely stupid to me. That and being told every half hour that it don't know the weather seems silly too.

[http://portal.theweatherchannel.com/](http://portal.theweatherchannel.com/)

Ugh, great...

Thanks for the update, kainalu.

Time to remove mine as well.

---

### Post by Pablo Pablovski on 2012-01-12
Me, too. 

Turns out all I need to do is look outside. Who knew? :D

---

### Post by shimoda on 2012-01-14
Oh, really bad news... :(

If anyone found an alternative, please post in this thread...

---

### Post by rodgerfox on 2012-01-16
I used these solutions. They worked great.

Just recently it stopped working again. Did it stop working for anyone else?

---

### Post by vagrale13 on 2012-01-21
To fix the problem, 
edit the file **/usr/share/avant-window-navigator/applets/weather/weather.py**
search and find the **3** lines with [http://xoap.weather.com/](http://xoap.weather.com/)
and change to [http://xml.weather.com/](http://xml.weather.com/)
The 3 lines must be towards the end of file.

The solution posted from here [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true)

---

### Post by Shocker on 2012-01-22
Perfectly working again!

Thank you for the report,

Shock99er

---

### Post by shimoda on 2012-01-22
also here!! thanks!! :D

---

### Post by Mike Chelen on 2012-02-11
> **vagrale13 said:**
> To fix the problem, 
edit the file **/usr/share/avant-window-navigator/applets/weather/weather.py**
search and find the **3** lines with [http://xoap.weather.com/](http://xoap.weather.com/)
and change to [http://xml.weather.com/](http://xml.weather.com/)
The 3 lines must be towards the end of file.

The solution posted from here [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true)

To replace those lines with sed:
```
sudo sed -i s/xoap.weather.com/xml.weather.com/g /usr/share/avant-window-navigator/applets/weather/weather.py
```

Also apply fix from #59 [http://ubuntuforums.org/showpost.php?p=11435261&postcount=59](http://ubuntuforums.org/showpost.php?p=11435261&postcount=59) if you did not already, and restart AWN when done.

---

### Post by shenmeister on 2012-02-12
Yup that resolves the issue again. I hope the new license key holds up and weather.com doesn't make any more changes in the near future.

---

### Post by peter86 on 2012-04-18
Thank you to all who posted solutions, I went through and edited it and after making all of the changes the applet works perfectly.

---

### Post by CEB2nd on 2012-05-03
Looks like the problem has returned. The fixes above
corrected the problem for awhile, but now  in the last few days
problem has returned. Anyone else experiencing this?

---

### Post by ptviperz on 2012-05-03
> **CEB2nd said:**
> Looks like the problem has returned. The fixes above
corrected the problem for awhile, but now  in the last few days
problem has returned. Anyone else experiencing this?

I started using the weather applet in Docky after a couple episodes of this. I can report the Docky one works fine...

I prefer the AWN applet but what can you do?

---

### Post by shimoda on 2012-05-04
> **CEB2nd said:**
> Looks like the problem has returned. The fixes above
corrected the problem for awhile, but now  in the last few days
problem has returned. Anyone else experiencing this?

I'm using weather in AWN an works without problems... :confused:

---

### Post by viperdvman on 2012-05-04
> **CEB2nd said:**
> Looks like the problem has returned. The fixes above
corrected the problem for awhile, but now  in the last few days
problem has returned. Anyone else experiencing this?

the problem's returned in my AWN weather applet. seems like the **[http://xml.weather.com/](http://xml.weather.com/)** fix isn't working this time. I even tried the old [http://xoap.weather.com/](http://xoap.weather.com/) and it still didn't work.

Hope it gets fixed soon.

---

### Post by Shocker on 2012-11-03
Hi Guys,

it seems that the "show Map" feature messed up again.

Did anyone else notice the same issue with the annoying "Network error in weater" warning coming up?

Any workaround?

Thanks in advance,

Shocker

---

### Post by CEB2nd on 2012-11-03
> **Shocker said:**
> Hi Guys,

it seems that the "show Map" feature messed up again.

Did anyone else notice the same issue with the annoying "Network error in weater" warning coming up?

Any workaround?

Thanks in advance,

Shocker

Having the same problem here, don't know of any workaround
yet.

---

### Post by d-man97 on 2012-11-05
Apparently, TWC updated their maps to Flash-based interactive maps. So, the old ones (the ones used for AWN's weather applet) are now the "Classic" maps.

```
/usr/share/avant-window-navigator/applets/weather/weather.py
```

You will need root to edit the file.

Goto around line 653.

Find:
```
map_url = "http://www.weather.com/weather/map/%s" % location_code
```

Change it to:
```
map_url = "http://www.weather.com/weather/map**/classic**/%s" % location_code
```

Save the file.

Remove the applet and add it back again; or, log out and back in; or, kill and restart AWN; or, anything else that results in reloading the weather.py file.

Hope this works for you as it did for me.

---

### Post by Shocker on 2012-11-06
Work perfectly!
Thanks for your help
Have a great day,

Shocker

---

### Post by CEB2nd on 2012-12-23
> **d-man97 said:**
> Apparently, TWC updated their maps to Flash-based interactive maps. So, the old ones (the ones used for AWN's weather applet) are now the "Classic" maps.

```
/usr/share/avant-window-navigator/applets/weather/weather.py
```

You will need root to edit the file.

Goto around line 653.

Find:
```
map_url = "http://www.weather.com/weather/map/%s" % location_code
```

Change it to:
```
map_url = "http://www.weather.com/weather/map**/classic**/%s" % location_code
```

Save the file.

Remove the applet and add it back again; or, log out and back in; or, kill and restart AWN; or, anything else that results in reloading the weather.py file.

Hope this works for you as it did for me.

Fixed it. Thanks. 8-)

---

### Post by shenmeister on 2013-01-31
The whole app works with all the URL fixes and new API key. It seems like every few months weather.com changes something to break the app. It's a good thing this topic wasn't marked as fixed :p.

---

### Post by shimoda on 2013-07-16
Anyone is yet using AWN & weather app? :-P xD

I'm in ubuntu 12.04 LTS and recently returned to AWN. All the tricks in this thread work! :)
But not the last! Now, the line 653 in weather.py contains ```
http://www.weather.com/outlook/travel/businesstraveler/map/%s
```
and changing it to ```
http://www.weather.com/weather/map/classic/%s
``` doesn't improves nothing...

any ideas?

---

### Post by d-man97 on 2013-07-16
Here is a pastebin of my entire weather.py that is currently working.

[http://pastebin.com/aqzPLcQC]("http://pastebin.com/aqzPLcQC")

You should save it to your filesystem, then do a diff against the one you have installed. That should point out where your issue is.

Good luck!

---

### Post by shimoda on 2013-07-17
> **d-man97 said:**
> Here is a pastebin of my entire weather.py that is currently working.

[http://pastebin.com/aqzPLcQC]("http://pastebin.com/aqzPLcQC")

You should save it to your filesystem, then do a diff against the one you have installed. That should point out where your issue is.

Good luck!
thanks a lot d-man, solved ;P 

the problem was with next line, in my case:
```
mapExp = """<IMG NAME="mapImg" SRC="([^\"]+)" WIDTH=([0-9]+) HEIGHT=([0-9]+) BORDER"""
```

and in your version:
```
mapExp = """<img name="mapImg" src="([^\"]+)" width="([0-9]+)" height="([0-9]+)" border"""
```

I suppose that's a problem with capital letters...

And if anyone interested, I changed something to detect some more themes (in my case 2 o 3). Changing lines 299-305:
```
# Only use themes that are likely to provide all the files
        def filter_theme(theme):
            return os.path.isfile(os.path.join(theme_dir, theme, "scalable/status/weather-clear.svg")) \
                or os.path.isfile(os.path.join(theme_dir, theme, "48x48/status/weather-clear.png")) \
                or os.path.isfile(os.path.join(theme_dir, theme, "48x48/status/weather-clear.svg"))
        themes = sorted(filter(filter_theme, os.listdir(theme_dir)))
        self.themes = [system_theme_name] + themes + ["moonbeam"]
```

with
```
# Only use themes that are likely to provide all the files
        def filter_theme(theme):
            return os.path.isfile(os.path.join(theme_dir, theme, "scalable/status/weather-clear.svg")) \
		or os.path.isfile(os.path.join(theme_dir, theme, "status/48/weather-clear.png")) \
		or os.path.isfile(os.path.join(theme_dir, theme, "status/48/weather-clear.svg")) \
                or os.path.isfile(os.path.join(theme_dir, theme, "48x48/status/weather-clear.png")) \
                or os.path.isfile(os.path.join(theme_dir, theme, "48x48/status/weather-clear.svg"))
        themes = sorted(filter(filter_theme, os.listdir(theme_dir)))
        self.themes = [system_theme_name] + themes + ["moonbeam"]
```

---

### Post by shimoda on 2014-02-03
Any news here? XD

I continue using AWN and weather applet, anyone more using it? :P I'm also using UB 12.04 LTS

What happens me now is that everytime I click on weather applet, the 5 weather icons doesn't appear. And applet crashes.
I see in terminal this:
> Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/weather/forecast.py", line 282, in expose_event_cb
    self.draw_days(widget, event, context)
  File "/usr/share/avant-window-navigator/applets/weather/forecast.py", line 251, in draw_days
    self.drawSingleDay(cache_context, xpos, ypos, day, text_color)
  File "/usr/share/avant-window-navigator/applets/weather/forecast.py", line 193, in drawSingleDay
    icon_name = self.__parent_weather.get_icon_name(day['CODE'], self.__parent_weather.applet.settings["theme"])
  File "/usr/share/avant-window-navigator/applets/weather/weather.py", line 578, in get_icon_name
    hint = int(hint)
ValueError: invalid literal for int() with base 10: ''

any ideas?

thanks!!

---

### Post by shenmeister on 2014-02-03
When the app fetches for the forecast, I believe that the returned XML is missing information and the applet runs into problems when trying to parse it. I have noticed this occasionally when I click the applet for the forecast.

---

### Post by shimoda on 2014-02-04
> **shenmeister said:**
> When the app fetches for the forecast, I believe that the returned XML is missing information and the applet runs into problems when trying to parse it. I have noticed this occasionally when I click the applet for the forecast.

But is strange because the icon of the applet itself, is the current weather. It connects to the site and takes the information. Why it doesn't work with forecast? What's different?

thanks!

---

### Post by d-man97 on 2014-02-06
Didn't feel like getting into the parsing this time, so I simply made get_icon_name() always return a static icon.

```
    def get_icon_name(self, hint, theme):
        #if hint == "twc":
        #    return "twc-logo"

        #hint = int(hint)

        #if hint in (32, 34, 36):
            return "weather-clear"
        #elif hint in (23, 24, 25, 28, 30, 44):
        #    return "weather-few-clouds"
        #elif hint in (26, ):
        #    return "weather-overcast"
        #elif hint in (5, 6, 7, 8, 9, 10, 11, 12, 39, 45):
        #    # Special conditional for the extreme weather in moonbeam's Ottawa
        #    if theme == "moonbeam" and hint in (5, 6, 7):
        #        return "weather-snow-and-rain"
        #    return "weather-showers"
        #elif hint in (40, ):
        #    return "weather-showers-scattered"
        #elif hint in (13, 14, 15, 16, 17, 18, 41, 42, 43, 46):
        #    return "weather-snow"
        #elif hint in (19, 20, 21, 22):
        #    return "weather-fog"
        #elif hint in (4, 35, 37, 38, 47):
        #    return "weather-storm"
        #elif hint in (0, 1, 2, 3):
        #    return "weather-severe-alert"
        #elif hint in (31, 33):
        #    return "weather-clear-night"
        #elif hint in (27, 29):
        #    return "weather-few-clouds-night"
```

---

### Post by shimoda on 2014-02-08
thanks d-man, I'll try it!!!

---

### Post by shimoda on 2014-02-17
Hi!!

I think the problem is with the XML received from weather.com; I discovered it because one day the applet suddenly work as spected. It seems that sometimes (in my case almost ever), there's a problem with the first day of the forecast. 

For example, this saturday the applet worked well... And extracted from the XML:
[HTML]<day d="0" t="Sunday" dt="Feb 16">
<hi>56</hi>
<low>44</low>
<sunr>7:43 AM</sunr>
<suns>6:23 PM</suns>
<part p="d">
<icon>11</icon>
<t>Light Rain</t>[/HTML]

and today, as usual, not works. And from the XML:
[HTML]<day d="0" t="Monday" dt="Feb 17">
<hi/>
<low>48</low>
<sunr>7:42 AM</sunr>
<suns>6:24 PM</suns>
<part p="d">
<icon/>
<t/>[/HTML]

No Hi Temp, No Icon, No Forecast... I think that's what crashes the applet.

I did a little trick, and modifiyed the applet. I don't know python, but I discovered that if I pass the value from weather.com without converting it to integer, the applet continues working. I changed a little the code to show a "weather channel" icon when there's a problem with the XML. 

		```

                def get_icon_name(self, hint, theme):
                # if hint == "twc":
                # return "twc-logo"

                # hint = int(hint)   
		if hint in ("32","34","36"):
			return "weather-clear"
		elif hint in ("27","29"):
			return "weather-few-clouds-night"
		elif hint in ("23","24","25","28","30","44"):
			return "weather-few-clouds"
		elif hint == "26":
			return "weather-overcast"
		elif hint in ("5","6","7","8","9","10","11","12","39","45"):
			return "weather-showers"
		elif hint == ("40"):
			return "weather-showers-scattered"
		elif hint in ("13","14","15","16","17","18","41","42","43","46"):
			return "weather-snow"
		elif hint in ("19","20","21","22"):
			return "weather-fog"
		elif hint in ("4","35","37","38","47"):
			return "weather-storm"
		elif hint in ("0","1","2","3"):
			return "weather-severe-alert"
		elif hint in ("31","33"):
			return "weather-clear-night"
		else:
			return "twc-logo"
```
Maybe there are better solutions :roll: I'm not a programmer XD :mrgreen:

---

### Post by Tom_Vitale on 2014-05-27
Tried it, looks good!  I recommend that instead of commenting out the "hint = int(hint)" statement, wrap it in a try/except block like this:

try:
    hint = int(hint)
except:
    pass

---

### Post by shimoda on 2014-05-29
Thanks Tom!! 

I'll try it!!!

---

### Post by d-man97 on 2014-09-01
I recently upgraded from 12.04.x to 14.04.1 and had to redo all the weather.py changes to get it working again. I am using the saucy ppa, as trusty is not available.

I incorporated all previous changes, including shimoda's "show the twc icon on failure" and Tom_Vitale's "try/except".

Here is another paste of the entire file:
[http://pastebin.com/rDqahbu5]("http://pastebin.com/rDqahbu5")

---

