---
title: "How to disable auto-maximize in 11.04"
date: 2011-05-01
forum: General Help
---

### Post by jwadamson on 2011-05-01
Just upgraded to 11.04 and this drives me nuts.  When an app/window is opened, if it is "sufficiently" large, it maximizes.  I use eclipse.  Eclipse is a screen-space hog, however I still need to be able to see other windows and the application bar around the edge of the eclipse window.  Unfortunatly Unity(?) is fighting me on this set up because every time i relaunch eclipse, it becomes maximized even if I, the user, have explicitly un-maximized it.

How can I disable this auto-maximize behavior.

Thanks

---

### Post by edpatterson on 2011-05-01
> **jwadamson said:**
> 
How can I disable this auto-maximize behavior.
Thanks

That seems to the the $64 question (showing my age). I am trying to have 2 spreadsheets open, each one filling 50% of the screen. As soon as I get either one of the real close to the top of the window it pops to full screen ALA Window Aero. 

A 'feature' like this should need to be turned on, not off.

It really and truly sucks.
Ed

---

### Post by JayD2 on 2011-05-01
Try looking at the settings in the CompizConfig Settings Manager (ccsm). It isn't installed by default but in the software center you can install it. The name there is Advanced Desktop Effects Settings (ccsm).

Once you have that installed open it and go to the 'window management" category. There are a variety of options to adjust. I think the one the is bothering you is the one labeled "grid'". Uncheck that box and see if that fixes things.

Note: My top taskbar has a tendency to disappear or do weird things when I uncheck that box for instance. But just logging out and logging back in fixes it. And the setting has been successfully changed.

---

### Post by mc4man on 2011-05-01
> **jwadamson said:**
> Just upgraded to 11.04 and this drives me nuts.  When an app/window is opened, if it is "sufficiently" large, it maximizes.  I use eclipse.  Eclipse is a screen-space hog, however I still need to be able to see other windows and the application bar around the edge of the eclipse window.  Unfortunatly Unity(?) is fighting me on this set up because every time i relaunch eclipse, it becomes maximized even if I, the user, have explicitly un-maximized it.

How can I disable this auto-maximize behavior.

Thanks
You can't without building from source, then it's easy though I wouldn't disable, just up the threshold.

Part of the reason it was done was it fixed some bugs (4), whether that still applies not sure if anyone has looked at. I set it to 85% here on desktop, 87.5% on laptop (would not go too much further in case bugs are still valid, though you could try and see

if inclined the file to edit is this, a define right at the top of the file
/src/PluginAdapter.cpp

> PluginAdapter * PluginAdapter::_default = 0;

#define MAXIMIZABLE (CompWindowActionMaximizeHorzMask & CompWindowActionMaximizeVertMask & CompWindowActionResizeMask)
#define COVERAGE_AREA_BEFORE_AUTOMAXIMIZE 0.75

#define MWM_HINTS_FUNCTIONS     (1L << 0)


Here's the bug I'd opened on the initial value, some recent comments, ect
(but currently not open, feel free to set to new
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/708809](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/708809)

---

### Post by Awareness on 2011-05-02
Im not even using gnome (kde), and I want to disable this auto maximize thing.

Im using dual monitor and I cant move windows from one monitor to the other because this maximize behavior...

I disabled "snapping Windows", "grid", "Resize Window" and all that seemed related to me, but the behavior continue... I can't use my dual monitor like this :/

I'd love to see unity working, but setting it as default when is obviously not ready yet, was a big failure... i am not even using gnome, wtf! :/

---

### Post by mc4man on 2011-05-02
> **Awareness said:**
> Im not even using gnome (kde), and I want to disable this auto maximize thing.

The " auto maximize" deal here is only part of the unity plugin itself, what's that got to do with kde?

---

### Post by Awareness on 2011-05-02
> **mc4man said:**
> The " auto maximize" deal here is only part of the unity plugin itself, what's that got to do with kde?

The windows does not maximize, they maximize only to half of the screen when I move them to the right edge of the screen. Ive got unity plugin disabled on compiz and all the others plugins I just told... but I still have this behavior.

Does anybody know how to disable it? Its new behavior in 11.04

---

### Post by cragwolf on 2011-05-02
> **edpatterson said:**
> That seems to the the $64 question (showing my age). I am trying to have 2 spreadsheets open, each one filling 50% of the screen.

Try Super + Alt + NumPad6 to put one of the windows to the right hand side, and Super + Alt + NumPad4 to put the other window to the left side. Not at my Ubuntu computer right now, so I don't know if those shortcuts will make the windows fill exactly 50% of the screen.

---

### Post by edpatterson on 2011-05-02
> **cragwolf said:**
> Try Super + Alt + NumPad6 to put one of the windows to the right hand side, and Super + Alt + NumPad4 to put the other window to the left side. Not at my Ubuntu computer right now, so I don't know if those shortcuts will make the windows fill exactly 50% of the screen.

I hate to sound like an idiot but what is a Super key?

I doesn't really matter. I have gone back to 10.10 for now. It was just way to frustrating.

Ed

---

### Post by cipherboy_loc on 2011-05-02
Super is the name for the key with the Windows or Mac logo. 


Cipherboy

---

### Post by edpatterson on 2011-05-02
> **cipherboy_loc said:**
> Super is the name for the key with the Windows or Mac logo. 


Thanks! 53 and still learning.

Ed

---

### Post by Berto on 2011-05-07
> **JayD2 said:**
> Try looking at the settings in the CompizConfig Settings Manager (ccsm). It isn't installed by default but in the software center you can install it. The name there is Advanced Desktop Effects Settings (ccsm).

Once you have that installed open it and go to the 'window management" category. There are a variety of options to adjust. I think the one the is bothering you is the one labeled "grid'". Uncheck that box and see if that fixes things.

Note: My top taskbar has a tendency to disappear or do weird things when I uncheck that box for instance. But just logging out and logging back in fixes it. And the setting has been successfully changed.

Thank you for ccsm.  What a horrific default.  Ubuntu team needs to change that.  If I want to maximize a window, I will hit the freaking maximize button.  If I want to put it in the corner, I expect it to go to the corner and stay there.

---

### Post by MeduZa on 2011-05-10
> **cipherboy_loc said:**
> Super is the name for the key with the Windows or Mac logo. 


Cipherboy

on my keyboard (logitech G15) is a UBUNTU LOGO key :)

---

### Post by clearym on 2011-05-18
Hi Everyone,
I just found where you can disable this (or adjust the threshold as someone mentioned earlier). In CompizConfig Settings Manager, go to "Grid" in the Window Management section. There is a tab labeled "Edges" that controls the Resize Actions and Thresholds. I used this to disable the resize actions and it's working now.

---

### Post by Ruben.cc on 2011-05-25
**Thank you very much JayD2 for advising on ccsm and clearym on how to actually use it.** This auto maximize was starting to drive me nuts. I use a 1980x1080 screen and want my browser windows to be just a "regular" 1024 wide but full height. This auto maximize (or "grid" as it seemed called) is not only terribly annoying but also not working (at least on my system). No matter which edge or corner I dragged a window to, it just maximized to full screen always, which is totally useless when browsing sites with a fixed width and messes up layouts on sites that don't have a fixed width. I really hate when programs try to "think for me" and do things by themselves. **Thanks to this great forum and knowledgeable users I was able to eliminate another little annoyance from Ubuntu (or the desktop environment to be more specific).  **

---

### Post by wildmanne39 on 2011-05-25
> **clearym said:**
> Hi Everyone,
I just found where you can disable this (or adjust the threshold as someone mentioned earlier). In CompizConfig Settings Manager, go to "Grid" in the Window Management section. There is a tab labeled "Edges" that controls the Resize Actions and Thresholds. I used this to disable the resize actions and it's working now.Thank you.:D

---

### Post by obenauer on 2011-05-25
JayD2, your directions to turn off the grid option in CCSM worked for me.  Thanks for the info!  Now my windows are behaving properly

---

### Post by stallinux on 2011-06-15
> **JayD2 said:**
> Try looking at the settings in the CompizConfig Settings Manager (ccsm). It isn't installed by default but in the software center you can install it [...].

Once you have that installed open it and go to the 'window management" category. There are a variety of options to adjust. I think the one the is bothering you is the one labeled "grid'". Uncheck that box and see if that fixes things.


This worked. Exactly as promised. Thanks.

---

### Post by insane9 on 2011-06-30
> **clearym said:**
> Hi Everyone,
I just found where you can disable this (or adjust the threshold as someone mentioned earlier). In CompizConfig Settings Manager, go to "Grid" in the Window Management section. There is a tab labeled "Edges" that controls the Resize Actions and Thresholds. I used this to disable the resize actions and it's working now.

excellent, thankyou. One of the most annoying features ever. I hated it on Win7 and i hated it on Ubuntu. 


Also, after just upgrading to Ubuntu today, i had to change it to 'Ubuntu classic' before logon. Removing the classic menu bar at the top was a horrible thing to do.

---

### Post by bjerven on 2011-07-23
Thx for the help! ccsm did the trick! Really a ugly default setting!

---

### Post by aero13972486 on 2011-07-26
Hi there
Just to flesh this one out a bit, instead of turning off the whole **grid** plugin, set the four **threshold** values to 0 from the **edge** tab. That way you can keep the numpad feature. My default is the control key though, not super, but I'm using Gnome2. Unity hasn't impressed me much. For all those that don't like Unity, instead of going back to Ubuntu 10, on the login screen for 11.04 you'll have the option to choose the interface. You can choose classic and get 11.04 with Gnome2.

Thanks for the info about the control+alt+numpad. Heckava useful I must say. You can also keep pressing control+alt+np5, np5, np5... and the window will resize smaller.
I'm so impressed with this!

---

### Post by justNiz on 2011-08-28
> **JayD2 said:**
> Try looking at the settings in the CompizConfig Settings Manager (ccsm). It isn't installed by default but in the software center you can install it. The name there is Advanced Desktop Effects Settings (ccsm).

Once you have that installed open it and go to the 'window management" category. There are a variety of options to adjust. I think the one the is bothering you is the one labeled "grid'". Uncheck that box and see if that fixes things.

Note: My top taskbar has a tendency to disappear or do weird things when I uncheck that box for instance. But just logging out and logging back in fixes it. And the setting has been successfully changed.

Wow that whole mindset is horrible.
implementing non-standard functionality and then not even having the tool installed by default so that you can turn it off. Then making the tool have an unitnuitive name like ccsm and making it such a horrible tool in that it doesn't tell you even slightly what a lot of options it can turn on and off actually do. Furthermore GRID is such a bad and unintuitive name for an option that controls auto-maximise. They couldn't have done a better job of hiding the option to turn auto-maximise off if they tried. I'm amazed anyone even found it.

Its F*cked up thinking like this that totally turns off new people trying out Linux, or even supposedly experienced users like me upgrading their older Ubuntu to newer versions.

---

### Post by Paddy Landau on 2011-10-07
Well, I have turned the four thresholds to zero and even disabled Grid altogether.

It is still maximising my "large enough" windows.

Aargh! I hate when programmers try to second-guess me.

Any help for me, please?

---

### Post by jleslie48 on 2012-03-01
the $128 question is why in god did they think this is a good idea in the first place.   It is absolutely an incredibly annoying feature.   I can't imagine anyone liking it and for that matter even requesting.

---

### Post by Paddy Landau on 2012-03-02
> **jleslie48 said:**
> the $128 question is why in god did they think this is a good idea in the first place.   It is absolutely an incredibly annoying feature.   I can't imagine anyone liking it and for that matter even requesting.
And the $256 question is how to turn it off!

I wonder if we can raise it as a bug? It still causes me problems.

---

### Post by graemev on 2012-03-11
trying to turn this damm  thing off on my desktop (just installed)I already turned it off on may laptop ... there was a simple on/off flag somewhere ... dammed if I can find it now  .... didn't involve compiz  at all

---

### Post by graemev on 2012-03-11
Damm it was this one:

/apps/metacity/general/auto_maximize_windows

That's inside: gconf-editor(1)

Already OFF on my desktop ... and maximise still happens (works fine on laptop)

---

### Post by graemev on 2012-03-11
Ahh ... added this one (was 10 set to 1) ... and now only maximises if I go "right off the top"

/apps/compizconfig-1/profiles/Default/plugins/grid/screen0/options/top_edge_action

---

### Post by Paddy Landau on 2012-03-12
> **graemev said:**
> Ahh ... added this one (was 10 set to 1) ... and now only maximises if I go "right off the top"

/apps/compizconfig-1/profiles/Default/plugins/grid/screen0/options/top_edge_action
I can find that in neither 11.04 nor 12.04 Beta. Do we have to add this item?

---

### Post by mc4man on 2012-03-12
> **Paddy Landau said:**
> I can find that in neither 11.04 nor 12.04 Beta. Do we have to add this item?
The problem with this thread is it's about 2 different things

The orig. post concerned the auto max 'feature' in 11.04 where any window that was 75% or more of the available screen was then auto maximized when opening. In 11.04 there was no way to adjust this other than changing the value in the source & rebuilding unity. (other than resizing offending windows to below 75% before closing

Then posters started referring to the grid plugin which is something different altogether.

In 11.10/12.04 there is an option to adjust the 'automaximize' value, it's in the unity plugin > experimental settings, screen shows where in 12.04, similar in 11.10

Additionally, starting in 12.04 it's been turned off for most screen sizes, I forget exactly what size, so for most the setting is moot. If affected in 11.10 or 12.04 simply raise the value.

---

### Post by Paddy Landau on 2012-03-12
> **mc4man said:**
> In 11.10/12.04 there is an option to adjust the 'automaximize' value, it's in the unity plugin > experimental settings, screen shows where in 12.04, similar in 11.10
Thank you, I found it now in 12.04. The setting in gconf is:

[FONT=Lucida Console] apps > compiz-1 > plugins > unityshell > screen0 > options > automaximize_value[/FONT]

Unfortunately, it does not work for me! Upon opening Compiz Config Settings Manager, I see that Unity Unity Plugin is turned off. Does this mean I am using 2D instead of 3D? (How can I tell?) If I'm on 2D, how can I force 3D?

Or is something else going on?

> **mc4man said:**
> Additionally, starting in 12.04 it's been turned off for most screen sizes...What setting is that? Does it mean that there is a list of applications for which the setting is ignored?

---

### Post by mc4man on 2012-03-12
> **Paddy Landau said:**
> Thank you, I found it now in 12.04. The setting in gconf is:

[FONT=Lucida Console] apps > compiz-1 > plugins > unityshell > screen0 > options > automaximize_value[/FONT]

Unfortunately, it does not work for me! Upon opening Compiz Config Settings Manager, I see that Unity Unity Plugin is turned off. Does this mean I am using 2D instead of 3D? (How can I tell?) If I'm on 2D, how can I force 3D?

Or is something else going on?

What setting is that? Does it mean that there is a list of applications for which the setting is ignored?

Here is the bug (fixed) that describes when the 'auto maximize' is disabled, making the setting irrelevant
[https://bugs.launchpad.net/ayatana-design/+bug/797808](https://bugs.launchpad.net/ayatana-design/+bug/797808)

That ^ is only for unity 3d. 


To see what your on this will show, unity 3d returns 'ubuntu', unity-2d obvious

```
echo $DESKTOP_SESSION
```

In unity-2d there is a setting to turn off auto max in metacity, see screen

As far as why you can't get unity-3d maybe a new thread, post the results of
```

/usr/lib/nux/unity_support_test -p
```

```
sudo lshw -C display
```

---

### Post by rg4w on 2012-03-12
> **Paddy Landau said:**
> Aargh! I hate when programmers try to second-guess me.
There are a number of such presumptions in the 11.10 design.  How do these happen?  Are they user-tested?

---

### Post by Paddy Landau on 2012-03-12
> **mc4man said:**
> Here is the bug (fixed) that describes when the 'auto maximize' is disabled, making the setting irrelevant
[https://bugs.launchpad.net/ayatana-design/+bug/797808](https://bugs.launchpad.net/ayatana-design/+bug/797808)
Thank you, I have voted for the bug.

> **mc4man said:**
> echo $DESKTOP_SESSION ...
Thanks for showing me those commands. I have 2D, and I don't know why. I have [posted a thread for my issue]("http://ubuntuforums.org/showthread.php?t=1939800").

> **rg4w said:**
> There are a number of such presumptions in the  11.10 design.  How do these happen?  Are they user-tested?
I really don't know, but it is irritating to the extreme.

---

### Post by LeFou on 2012-05-23
> **Paddy Landau said:**
> I really don't know, but it is irritating to the extreme.

This auto-maximize is a very useful "feature" if all you ever use your computer for is to piddle around on Facebook (NASDAQ:FB)

---

