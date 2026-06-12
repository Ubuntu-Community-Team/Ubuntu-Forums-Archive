---
title: "Precise Gnome classic now has Unity panel"
date: 2012-08-10
forum: General Help
---

### Post by Cavsfan on 2012-08-10
This is strange but, I select to login into Precise Gnome Classic and when it comes up the Unity panel is there and 
at the top left the Applications and System menus are gone. :confused:

I don't think I have done anything to cause this as I have been using 12.10 most of the time.
If any one has a clue as to what is going on I would very much appreciate some help!
Thanks!:)

---

### Post by Cavsfan on 2012-08-10
Oh and while I am talking about Precise. Does any one know if there is a way to put "Restart" back in the left top menu?
I know it is there on the left when you click on Shutdown but, was just wondering as I have accidentally clicked shutdown instead of restart a couple of times.

---

### Post by bogan on 2012-08-10
Hi!, **Cavsfan**,

I do not know how many others have found this Unity /Classic mix up, but my 12.04 LTS pae Gnome Classic, has had the Unity Launcher, with Dash but no Topbar menu headings, ever since it was installed on the first day of release.

I Posted a thread about it, back in APRIL, asking for clarification and if it was intentional & others got the same, but got no response, so I supposed it was not common. Logging-in to gnome classic(no effects) is as one would expect - no unity.
[h]("http://ubuntuforums.org/showthread.php?t=1969961")[ttp://ubuntuforums.org/showthread.php?t=1969961]("http://ubuntuforums.org/showthread.php?t=1969961")

Entering:```
  echo $DESKTOP_SESSION
```Shows "gnome classic".

Since April the only change has been that originally the Launcher Icons were 48 pixels in the 2d Launcher mode and could not be reduced. In the course of various updates that has altered and I can now reduce them to 32 pixels al la 3d launcher.

So I will be interested to see if you get any more response than I did.

Chao!,** bogan.**

---

### Post by Primefalcon on 2012-08-10
Can you post a screenshot?

---

### Post by Cavsfan on 2012-08-10
Sure can. Just give me a second I am in Quantal right now.

---

### Post by Cavsfan on 2012-08-10
Here it is. You can tell it's Classic with effects because you can see the top and bottom panels.
However, where it says "Ubuntu Desktop" at the top left, there are no Applications or Places menus and the Unity bar is there.

[[IMG]http://ompldr.org/tZjI4NQ[/IMG]]("http://ompldr.org/vZjI4NQ")

---

### Post by Cavsfan on 2012-08-10
> **bogan said:**
> Hi!, **Cavsfan**,

I do not know how many others have found this Unity /Classic mix up, but my 12.04 LTS pae Gnome Classic, has had the Unity Launcher, with Dash but no Topbar menu headings, ever since it was installed on the first day of release.

I Posted a thread about it, back in APRIL, asking for clarification and if it was intentional & others got the same, but got no response, so I supposed it was not common. Logging-in to gnome classic(no effects) is as one would expect - no unity.
[h]("http://ubuntuforums.org/showthread.php?t=1969961")[ttp://ubuntuforums.org/showthread.php?t=1969961]("http://ubuntuforums.org/showthread.php?t=1969961")

Entering:```
  echo $DESKTOP_SESSION
```Shows "gnome classic".

Since April the only change has been that originally the Launcher Icons were 48 pixels in the 2d Launcher mode and could not be reduced. In the course of various updates that has altered and I can now reduce them to 32 pixels al la 3d launcher.

So I will be interested to see if you get any more response than I did.

Chao!,** bogan.**

Hopefully we can get this fixed **bogan**! My system was fine up until maybe 5 days, a week ago.
All 3 Ubuntu I have installed got new kernels today and so I have been in all 3.
I have been in Quantal 12.10 a lot and hadn't paid much attention until lately when I realized this was not right.
Thanks to any one that can sort this out! :)

---

### Post by bogan on 2012-08-11
Hi!, **Cavsfan**,

Have you tried to see if the Gnome Classic Menu headings are there, but under the Global menu Title/Headings.

How about Icons in the left side of the Topbar? do they show?

Inactivating the Global menu or altering the Theme, or topbar transparency can make them visible, but not, of course, accessible.

Personally, because of this, I tend to use Gnome Classic(no effects) and had rather forgotten how annoying I found this to start with.

I also checked out my other 12.04 installation on the same Desktop and its Gnome Classic is just the same with the Unity style Launcher side bar & no visible menu headings.

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-08-11
> **bogan said:**
> Hi!, **Cavsfan**,

Have you tried to see if the Gnome Classic Menu headings are there, but under the Global menu Title/Headings.

How about Icons in the left side of the Topbar? do they show?

Inactivating the Global menu or altering the Theme, or topbar transparency can make them visible, but not, of course, accessible.

Personally, because of this, I tend to use Gnome Classic(no effects) and had rather forgotten how annoying I found this to start with.

I also checked out my other 12.04 installation on the same Desktop and its Gnome Classic is just the same with the Unity style Launcher side bar & no visible menu headings.

Chao!, **bogan.**

The only way I can get to the applications menu is through Cairo Dock. As you can see from the picture above, 
the top left of the panel there is nothing and the icons are visible on the right top panel.

I have been using Gnome Classic for quite a while without any issues. I haven't recently changed any themes or anything. I have only gotten in long enough to get updates.

I have spent most of my time in Quantal 12.10 and have a perfectly good working Gnome Classic there.
The left of the top panel in Quantal  show Applications and Places OK and there is no Unity panel.

So, I guess if I didn't have Cairo Dock installed, I would have an unworkable system. No access to anything other than that which is available in the Unity panel.

I like Gnome Classic with effects and since this is the LTS I am hoping that this can be fixed.
If I wanted to see that Unity panel I would just login that way.
Thanks bogan!

---

### Post by bogan on 2012-08-11
Hi!, **Cavsfan**,

For the same reason that you use the Cairo Dock, with Gnome Classic to access the menus, I have installed the ClassicMenu Indicator, as you can see in the attached screenshot.

For the purposes of illustration - it is non-functional - I used Ubuntu Tweak to change the GTK Theme from 'Clearwaita' to 'Low Contrast'.

As a result you can see the Icons I set in the Topbar with Gnome Classic(no effects), though they are not accessible; also the Gnome menu Headings ;Applications' & 'Places' are visible, though over-written by the Global Menu active window title.

You can see it is Gnome Classic from the Terminal window, and the bottom panel; whilst the "App" of "Applications" & and the "aces" of "Places", are also readable.

I am Posting this as it seems to me that the problem is not with Gnome Classic, which is functioning as it should, but with the Global Menu function and Dash, which should not be active at all.

Edit: Incidently, there is no 'Unity' Icon in 'System Settings', so I cannot try turning it off that way; perhaps, if you have that Icon you could try de-activating it.  "man unity" does not offer any way to do so in a terminal.
Chao, **bogan.**

---

### Post by Cavsfan on 2012-08-11
bogan, would you believe I just had to login into Precise in Unity (Ubuntu 2nd login option from the bottom) and then back on in Gnome Classic and
the Unity panel is gone and Applications and Places are selectable at the top left!
Problem solved.
I know it takes a while when you select another login option. I have only selected 2 the whole time I have had Precise installed:
Ubuntu (with Unity) and Gnome Classic (with effects).

I have firefox-globalmenu installed.

It must have been a glitch. I hope you get your problem sorted out.
However, there are still a few things I notice: I cannot Alt+Tab between windows and Emerald is not the windows decorator.
It is probable just some setting in CCSM or Cairo Dock. Those 2 can make your system appear to be in trouble when all it is is a setting.
I'll play around and see if I can fix it or find out what is messed up.
Thanks!

---

### Post by bogan on 2012-08-11
Hi!, **Cavsfan**,

I just realised that the Unity Icon I missed in System Settings, was in CCSM, under 'Desktop'.

Untick the 'Ubuntu Unity Plugin' and Hey Presto, the Dash and Launcher disappear, and the Menu headings are revealed and active, as are the Icons I added to the Topbar.

However, the Global Menu has gone as well and windows have no menu bars, and I have not yet found how to activate them. Any Ideas??

Edit: I just read your Post #11.  Switching Login back and forth between the various options never affected the Global Menu problem with Gnome Classic for me. I wonder if Unity will still be there when I login to Ubuntu !!.

Chao!,** bogan.**

---

### Post by Cavsfan on 2012-08-11
I also did this to get the File, Edit, etc. back on the top of all the menus at the suggestion of CharlesA:

**Disable the Global Menu in Ubuntu 12.04 (Precise Pangolin)**

[http://ubuntuforums.org/showpost.php?p=12099470&postcount=97](http://ubuntuforums.org/showpost.php?p=12099470&postcount=97)

---

### Post by Cavsfan on 2012-08-11
> **bogan said:**
> Hi!, **Cavsfan**,

I just realised that the Unity Icon I missed in System Settings, was in CCSM, under 'Desktop'.

Untick the 'Ubuntu Unity Plugin' and Hey Presto, the Dash and Launcher disappear, and the Menu headings are revealed and active, as are the Icons I added to the Topbar.

However, the Global Menu has gone as well and windows have no menu bars, and I have not yet found how to activate them. Any Ideas??

Chao!,** bogan.**

I did have the Unity Plugin checked in CCSM and unchecking it did not fix it.
I will look at my settings in CCSM and Cario Dock because wobble windows is off and other things.
Probably just some settings got turned off.

---

### Post by bogan on 2012-08-11
Hi!, **Cavsfan,**

Well, looks as though, even if the symptoms are the same, the causes of our problems are different.

Logging out of Gnome Classic to Ubuntu/Unity gave me a heart stopping 45 seconds of blank black screen followed by another 40 secs of Desktop background on logging back to Gnome classic. 

However, it restored the Window Menu bars, so I did not need to use your link, Thanks for the thought.

Strangely, In Ubuntu/Unity CCSM the Unity Plugin had no 'tick' option, so I suppose it is always active when logged in that way.

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-08-11
Sure enough the CCSM settings were all set back to default. I mean everything.
I think everything is back to normal now.

One thing I could not figure out was my conky on my right side was always "on top" of all other windows even when started via Alt+F2.
I also have a 20 second delay at startup for this.

I did find this here [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)
Added it and this fixed it.
**own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager**

Still some things are strange. I'll give it a while before I resolve this thread.

I hope you get your situation resolved **bogan**!

---

### Post by Cavsfan on 2012-08-11
> **bogan said:**
> Hi!, **Cavsfan,**

Well, looks as though, even if the symptoms are the same, the causes of our problems are different.

Logging out of Gnome Classic to Ubuntu/Unity gave me a heart stopping 45 seconds of blank black screen followed by another 40 secs of Desktop background on logging back to Gnome classic. 

However, it restored the Window Menu bars, so I did not need to use your link, Thanks for the thought.

Strangely, In Ubuntu/Unity CCSM the Unity Plugin had no 'tick' option, so I suppose it is always active when logged in that way.
You might look into that.

Chao!, **bogan.**

It seems every time you switch between login options, it takes a long time to do so.
So, I am used to that.
CCSM can cause so many problems that appear to be system related when they are just tweaks that change.

---

### Post by cmcanulty on 2012-08-11
I have the opposite problem. I like and use classic no effects but want to try Unity and XFCE and when I log into unity  I see only my classic panels, no dash.

---

### Post by sienile on 2012-08-11
> **cmcanulty said:**
> I have the opposite problem. I like and use classic no effects but want to try Unity and XFCE and when I log into unity  I see only my classic panels, no dash.

I would suggest starting your own thread. People who have had your problem are going to be more likely to find your post if the thread title matches the problem... not the opposite problem.

I have no idea what could be causing that myself. I'm just searching through the forum for some place for me to productively use my 50 posts to be able to have a signature.

P.S.: I still hate that 50 post rule.

---

### Post by Cavsfan on 2012-08-12
Everything seems back to normal with the following exceptions on the top right panel:
1) no volume icon
2) no internet status icon
3) no evolution email icon
4) no gear icon for logout, shutdown, suspend, etc.
5) 2 time displays instead of the usual 1

---

### Post by Cavsfan on 2012-08-12
Well, I have tried a bazzillion things and cannot get it back the way it was.
I even logged in with Unity and there was no Unity panel until I enabled the Unity plugin in CCSM.
Compiz breaks on almost every login. It has been resetting it's self to default too even back to 2 windows.
After I had it all setup with the rotating cube, etc.

I tried purging gnome-session-fallback and gnome-panel, rebooting, reinstalling them and still the top right icons are gone.
It's probably going to take a fresh install of 12.04.1 which comes out on the 23rd.

---

### Post by Cavsfan on 2012-08-20
> **cmcanulty said:**
> I have the opposite problem. I like and use classic no effects but want to try Unity and XFCE and when I log into unity  I see only my classic panels, no dash.

That is most probably just the Unity plugin not being checked in CCSM causing that.

---

### Post by Cavsfan on 2012-08-26
Solved this today with a clean install of 12.04.1

---

