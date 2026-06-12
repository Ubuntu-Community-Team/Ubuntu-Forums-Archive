---
title: "Unity panel always displayed on top of fullscreen windows"
date: 2011-09-23
forum: General Help
---

### Post by quequotion on 2011-09-23
Annoyingly, when any kind of application is in full-screen, the text and icons on the panel are always visible (appmenu, indicators, the clock etc).

Even more annoyingly, the mouse regards them as *under* the full-screen window (*where they should be*), so the indicator icons and application menus don't respond to clicks.

Is there any way to stop the panel from being displayed on top of everything?

I don't want to hide the panel, just have it properly covered when a full-screen window opens.

Is there any setting for this in ccsm, gconf, or dconf?

---

### Post by scarleo on 2011-09-23
What apps are you using that doesn't hide the panel? I haven't found any app with that behaviour, all my apps hides the panel when in fullscreen.

---

### Post by raja.genupula on 2011-09-23
Hey i have seen issue like you got. some times this type of issues needs capture of problem . so please attach a screen shot and by the way follow this 

[http://ubuntuforums.org/showthread.php?t=1654141](http://ubuntuforums.org/showthread.php?t=1654141)

All the best

---

### Post by quequotion on 2011-09-25
> **scarleo said:**
> What apps are you using that doesn't hide the panel?

It is not a problem with the applications.

The panel is displayed on top of every full-screen application of every kind.

Please understand that I do not mean the **launcher** on the left side.

I am talking about the **panel** across the top of the screen.


> **raja.genupula said:**
> ...and by the way follow this...

Thank you for the link, unfortunately this is not my problem. My problem has to do with full-screen applications.

I'm attaching two screenshots.

fullscreen.panel.1.png = a video in Totem.
fullscreen.panel.2.png = a game in wine.

---

### Post by fwsober on 2011-12-03
I'm also having this problem.

I am using Citrix Receiver to remote access another machine, and it tries to use the full screen but the Unity panel still appears at the top. I guess it's as a result of this that I still have a scrollbar on the RHS and the mouse is mis-placing all of my clicks within the screen.

I should mention I'm using a fresh install of 11.10.

Full screen is working fine with Firefox when I hit F11. With the citrix client F11 is just going through to the remote session though.

---

### Post by redeemer on 2012-01-12
My solution was:

If you have Compiz enabled (as in Unity by default):

```

sudo apt-get install compizconfig-settings-manager

```

Then, in Control Center: Personal / CompizConfig Settings Manager
check Utility / Workarounds / Legacy Fullscreen Support.

---

### Post by quequotion on 2012-02-12
[quote=redeemer]Then, in Control Center: Personal / CompizConfig Settings Manager
check Utility / Workarounds / Legacy Fullscreen Support. [/quote]

This is not a solution to my problem.

The problem is not how windows are rendered in full-screen.

Unity's panel is ALWAYS visible under ALL circumstances and with ANY settings.

Furthermore, when an application is in full-screen, the panel cannot be clicked. It is visible, but not usable.

I theorize that X11 correctly layers input so the full-screen window is "on top" and receives clicks, but something forces the panel to be *displayed* on top.

In Gnome 2 panels could be configured to "auto-hide" and scroll off the screen until moused over.

The Unity launcher (left edge) can be configured this way.

The Unity panel (top edge) cannot.

There are no settings, no functions, no features *at all* to hide this panel.

One of the design goals of Unity was to open more screen real-estate for users.
The panel is definitely detracting from that.

I'm surprised that no one else has posted about this.
It isn't just me.
Everyone using Unity should be experiencing this.
Maybe I'm the only one bothered by it?

---

### Post by sleepyhollows on 2012-02-12
THeres no settings anywhere in unity. No right click -> hide on icons, no drag to move... I dont get it. I can't find the settings for anything.

 But i'm sure it will be ironed out..

Your issue sounds pretty drastic and I would suggest unique. I doubt the release would have gone out with a ghost panel stuck over the top of full windows. If I am understanding correctly.

---

### Post by grahammechanical on 2012-02-12
In full screen mode the windows are moving under the panel. That is what is happening and it should not happen.

There is no intention to make the top panel disappear when a window is maximised. Remember, it is the intention with unity for the top panel to be the place for the max, min & close buttons of a window as well as for app indicators.

I am using 12.04 development release and maximised windows stay below the top panel but up against it.

we have the ability to bounce a window against the top panel and when we let go of the mouse button the window maximizes. Then when we move the mouse over the top panel the pointer should change to a hand icon so that we can grab the top of the maximized window and pull it down at which point the window snaps back to its original size. My point is that the maximized window should not be under the top panel. That is the problem and not the one of the top panel not disappearing.

I do not know how you stop this from happening but my guess is that it is to do with a setting in CCSM. I cannot check this out as I am not using 11.10 but 12.04 and there are changes to CCSM in 12.04.

Regards.

P.S. It occurs to me that your thread title is a little misleading. This is not a problem with maximized windows. Is it? It is a problem with playing video in full screen mode. Is it not?

---

### Post by bogan on 2012-02-12
Hi! **quequotion**,
You posted:>  I'm surprised that no one else has posted about this.
It isn't just me.
Everyone using Unity should be experiencing this.
Maybe I'm the only one bothered by it?Not so! I am running 11.10 and full screen Firefox Window extends to, but not over or under, the top Bar. Exactly as **grahammechanica**l describes for 12.04

Other apps,  including for instance LibreOffice and gedit, when clicked to to full screen extend to literally full screen, so they appear to be 'under' the title bar.

However, when the Mouse cursor is on the top bar the Window title moves to the right,  or the Global menu starts after the buttons, revealing the three control buttons, and they are effective.

However, contrary to what you describe, the Icons on the right all work normally.

The Mouse cursor changes to a hand but you cannot drag a fullscreen window anyway, you have to reduce it with the size button first.
**grahammechanica**l, Posted : > P.S. It occurs to me that your thread title is a little misleading. This  is not a problem with maximized windows. Is it? It is a problem with  playing video in full screen mode. Is it not?      On the evidence of the above the answer is No! - unless I unknowingly have the same fault that **quequotion** has.

What you, { QQ } describe, appears to be the failure to detect the mouse cursor is on the top bar.

Edit: I have just logged out & in to check that both Unity and Gnome Classic in 11.10 behave the same way. It is limited to an Ubuntu log-in, in Gnome Classic, it does not occur and **grahammechanica**l's description applies.

Chao!, **bogan**.

---

### Post by bogan on 2012-02-12
Hi!** all**.
I posted, P #10:>  Edit: I have just logged out & in to check that both Unity and Gnome  Classic in 11.10 behave the same way. It is limited to an Ubuntu  log-in, in Gnome Classic, it does not occur and **grahammechanica**l's description applies.As a further check I logged-in to Ubuntu 2d, and Unity 2D does the same FullScreen trick of hiding the top line behind the title bar.
BTW File Manager Windows also behave in the same way, when Clicked to FullScreen.

 With Gnome Classic, the top bar is a 'normal' Gnome Panel, that can be edited or removed with the Alt+Right-Click drop-down menu, or easily have Icons added, which the Unity top bar can not.

Perhaps this is to do with the Global Menu, which Gnome Classic does not have.

Personally I am not bothered by this, as my Mouse works as I would expect.

Chao!, **bogan**.

---

### Post by quequotion on 2012-02-13
> **grahammechanical said:**
> It occurs to me that your thread title is a little misleading. This is not a problem with maximized windows. Is it? It is a problem with playing video in full screen mode. Is it not?

The thread title is the best I could do.
I was expecting communcation difficulty when I started the thread.

It is not a problem with maximized windows.
It is not a problem with the windows.
It is not a problem with watching videos.

It is a problem with the panel along the top edge of the screen, which should not (in my opinion) be visible while an application is in full-screen. This is affecting applications of all kinds: media players, games, web browsers, etc...

Furthermore, if the panel is going to be visible anyway, it should at least be usable but it is not.
While the panel can be seen at all times, when displayed on top of a full-screen window it cannot be clicked.

I know this confusing.

By full-screen I do not mean "maximized".
Maxmized windows are still windows and have a titlebar with close, minimize, and restore buttons.

Full-screen means occupying 100% of screen space.

With Unity, there is always a panel at the top, even when an applicatio should be completely covering the screen.

> **sleepyhollows said:**
> THeres no settings anywhere in unity. No right click -> hide on icons, no drag to move... I dont get it. I can't find the settings for anything.Because they are in Compiz. You need to install compizconfig-settings-manager (ccsm). There are only a few configurable items.> But i'm sure it will be ironed out..Never lose that faith.> Your issue sounds pretty drastic and I would suggest unique. I doubt the release would have gone out with a ghost panel stuck over the top of full windows. If I am understanding correctly.

It isn't unique. Everyone using unity should be experiencing this.

The release indeed went out "with a ghost panel stuck over the top of full[-screen] windows". I've seen this in three differet installs of Ubuntu on two differen computers.

---

### Post by efflandt on 2012-02-13
It sounds like possibly a specific video card, chip or driver issue.  Things like full screen flash video should really go full screen.  But for some reason something is not layering properly and your inactive top bar remains visible.

What video card or chip do you have, and which driver.

---

### Post by quequotion on 2012-02-13
> **efflandt said:**
> It sounds like possibly a specific video card, chip or driver issue.  Things like full screen flash video should really go full screen.  But for some reason something is not layering properly and your inactive top bar remains visible.

What video card or chip do you have, and which driver.

I honestly don't think so.

Can you provide a screenshot of anything in full-screen (not maximized) with no panel at the top? (I should **not** be able to see the application name or menu nor the indicator icons, the clock, or the user and system menus)

Desktop: nVidia GT 220, using the proprietary drivers.

Laptop: Intel 315M (or something like that)

I have tried several versions of the nvidia driver and always had this issue.

I have tried the nouveu driver as well and had the same issue in addition to general horribleness.

*UPDATE*
[Found another thread about this issue.](http://ubuntuforums.org/showthread.php?t=1790241) It looks like there were the same communication problems and ultimately it just came to an end.... in July 2011.

---

### Post by quequotion on 2012-02-13
> **bogan said:**
> Hi!** all**.
I posted, P #10:As a further check I logged-in to Ubuntu 2d, and Unity 2D does the same FullScreen trick of hiding the top line behind the title bar.
BTW File Manager Windows also behave in the same way, when Clicked to FullScreen.

 With Gnome Classic, the top bar is a 'normal' Gnome Panel, that can be edited or removed with the Alt+Right-Click drop-down menu, or easily have Icons added, which the Unity top bar can not.

Perhaps this is to do with the Global Menu, which Gnome Classic does not have.

Personally I am not bothered by this, as my Mouse works as I would expect.

Chao!, **bogan**.


Sounds like you've observed the behavior I'm talking about.
It's not caused by the global menu.
The behavior is the same even without global menu (appmenu) installed.

The reason this bothers me is not completely asthetic.

I don't want the application title and menu, as well as the indicator icons, the clock, and the user and system menus on top of my games, movies, audio visualizers, image editor, etc when the applications are in full-screen and should occupy 100% of the screen space without obstruction.

---

### Post by quequotion on 2012-02-13
> **grahammechanical said:**
> In full screen mode the windows are moving under the panel.It certainly looks like that.

> There is no intention to make the top panel disappear when a window is maximised. I already mentioned this, but I mean "full-screen" and not "maximised"; the two terms are not interchangable.

The rest of your post describes the behavior of maximising/unmaximising windows in compiz which has apparently not changed.

I am having a problem with full-screen applications, not maximized applications.

---

### Post by baillou2 on 2012-02-13
I think I have more or less, the same issue. Here's my original post about it (no one ever answered):

For the past couple of weeks I've had this bug. When I maximize a window from being minimized it goes all the way up into the panel. To fix it I only have to grab the panel and drag down and the window pops back where it should be just under the panel. But it's really annoying. 

Here's a picture. If you'll notice the top of the maximized nautilus window goes up and behind my semi-transparent panel.

Does anyone have any info on this and a means of fixing it? I can't seem to find anything.

Thanks in advance.

---

### Post by quequotion on 2012-02-14
> **baillou2 said:**
> I think I have more or less, the same issue. Here's my original post about it (no one ever answered):

For the past couple of weeks I've had this bug. When I maximize a window from being minimized it goes all the way up into the panel. To fix it I only have to grab the panel and drag down and the window pops back where it should be just under the panel. But it's really annoying. 

Here's a picture. If you'll notice the top of the maximized nautilus window goes up and behind my semi-transparent panel.

Does anyone have any info on this and a means of fixing it? I can't seem to find anything.

Thanks in advance.

Your screenshot definetly *looks* like the same issue, but the circumstances are different.

You are experiencing a bug in **maximisation** behavior.

In your case, the window size is increasing after being re-maximised; ignoring the the panel which should also be serving as the titlebar and upper limit for the maximised window.

Is this happening with all applications or just certain applications?



I started this thread because of a problem with **full-screen**.

The properties of a full-screen application and a maximized window are different.

A maximised window should have:
[LIST=1]
[*]A title bar
[*]A window frame
[*]Close, Minimize, and Restore buttons
[/LIST]

In Unity, the panel provides those along with the indicator icons, clock, and user and system menus.

A full-screen application:
[LIST=1]
[*]Occupies 100% of screen space with content
[/LIST]

There should be nothing else on the screen at all.

My problem is the the panel is always visible. So your problem and mine look the same, and may even be related, but are not exactly the same bug.

---

### Post by bogan on 2012-02-16
Hi!, quequotion,

 My previous Posts in this thread were a little confused as I had not  appreciated the full significance of you distinguishing between  maximised and fullscreen windows.
 
Now I do, and I am a bit surprised that no-one seems to have responded to your Post: >   Can you provide a screenshot of anything in full-screen (not  maximized) with no panel at the top? (I should not be able to see the  application name or menu nor the indicator icons, the clock, or the user  and system menus).  I would have responded before this, but had not a clue how to attach multiple Thumbnails. I have now found away to do so, but the results are even more confusing.

Running 11.10 logged in to Ubuntu { Unity } 
First, the only program I have found that behaves roughly as you describe is Gimp. FullScreened [ F11 ] it occupies the whole screen but the top panel Icons are on top of it **and active.** I have not tried to get a screenshot.

Second, an empty Gedit screen  Clicked to Full-Screen { F11 } is totally white, with no borders or  Panels, and no Icons showing; not much point in Posting a screenshot of  nothing. 

So the file in the 1st image has three lines of text, though only line 3  is visible, until the cursor is placed, not just on the top text line,  but touching the extreme top of the screen.
The first image is of a Gedit file FullScreened { F11 } with the cursor  pushed up to the top edge of the screen, causing the Gedit Tool Bar to  come down over the top two lines of the text.
.....................................<< Click on the space below this, there is a Thumbnail there!
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212777&thumb=1&d=1329406520[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=212777&d=1329406520") The actual Screen image visible is limited by the thin line over the Gedit Toolbar.

The second image is FireFox FullScreened { F11 } with the cursor held  below the top bar, the dark surround of the Ubuntu Forum screen occupies  the Top Bar and no panel Icons are visible. The top five lines have  gone. 
However the two FF buttons are also in that Bar, the **[COLOR=Red]|F|[/COLOR] **on the left giving access to FF's own menus, and the three size buttons on the right are also active.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212778&thumb=1&d=1329406520[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=212778&d=1329406520") The actual visible image is limited by the dark surround on the forum display.

The third image is FireFox FullScreened { F11 } with the cursor pushed  up to the top edge of the screen, causing the two FF Tool Bars to come  down but not over the top two lines of the display: instead the latter  scrolls down to make room for them. The FF buttons stay in the same  position independent of the scrolling.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212779&thumb=1&d=1329406520[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=212779&d=1329406520") The trouble is that,  apart from the first which accurately shows what is visible on the  screen, but shows in addition, lines and the panel which belong to the Nautilus display of the Screenshot, these screen shots bare no resemblance at all to what is actually visible.

Neither the Left side LauncherPanel nor the top Panel and top three  lines are visible. whereas the screenshots show things which are not   Fullscreen displays at all, and Image 2 & 3 seem identical, which is  a travesty. 

Chao!, bogan.  Puzzled beyond belief. I clearly need a different way of getting a true screen shot.

---

### Post by quequotion on 2012-02-16
> **bogan said:**
> Hi!, quequotion,

 My previous Posts in this thread were a little confused as I had not  appreciated the full significance of you distinguishing between  maximised and fullscreen windows.
 
Now I do, and I am a bit surprised that no-one seems to have responded to your Post  As am I, somewhat. I am also not entirely shocked that there are no screenshots without the Unity panel as it is always visible under all circumstances in every installation of Ubuntu (until someone proves me wrong).

> ...Gimp. FullScreened [ F11 ] it occupies the whole screen but the top panel Icons are on top of it **and active**.  I verified this. Like everything else, the panel is visible on top of Gimp's fullscreen window; *unlike* everything else, the icons and menus on the panel still respond to clicks.

> Neither the Left side LauncherPanel nor the top Panel and top three  lines are visible. I think you mean the screenshot of gedit, which looks like the *correct* full-screen behavior. Gedit's slide down menu *should* cover a few lines when the cursor hits the top of the screen to pull it down and neither the launcher nor the panel should be visible.

**How did you get that screenshot?** I need to know in exact detail.

> Chao!, bogan.  Puzzled beyond belief. I clearly need a different way of getting a true screen shot.

Yes, unfortunately your screenshots of firefox show neither full-screen nor anything to corroborate your statements.

How did you take these screenshots?

---

### Post by quequotion on 2012-02-16
Here are two more screenshots of the problem.

This is now in Precise.

Both screenshots are of Firefox (11.0~b2+build1-0ubuntu1).

Both screenshots clearly show the Unity panel across the top.

See the window title, the indicator icons, the clock, the user menu and the system menu?
*None of them shoud be there;* furthermore, none of these menus or icons respond to clicks.

The first screenshot is simply firefox in full screen.

The second screenshot shows what happens when the mouse touches the top of the screen while firefox is in full-screen: the tab bar and navigation bars drop down.

You may notice that the background of the panel is different in each screenshot.
I have set it, in ccsm, to 100% opacity, which somewhat alleviates my frustration (its content is always visble, but at least its background is clear).

The first screenshot shows the brown border of the Ubuntu Forum's page behind the panel, so the panel appears brown.

The second screenshot shows the gray background of the the tab bar behind the panel, so the panel appears gray.

These screenshots were taken by pressing [PrtScr].
By default, Ubuntu uses gnome-screenshot for [PrtScr].
The screenshots represent exactly what is displayed on my screen, except they are down-sized for the forum limitations.

---

### Post by bogan on 2012-02-16
Hi! **quequotion**,

This is frustrating, I just spent four hours trying to answer your queries and just as I got somewhere and had a Fullscreen of FireFox with top panel icons over it, that worked, - I had a drop-down menu displayed - when I tried to get a Screenshot, a Window opened saying that a script had failed to respond and did I want to wait?

Then everything froze and when I rebooted FireFox was all corrupt.

However I have managed to get one Screenshot that is more or less what is visible, though don't ask me what I did differently. or how I got the screen with the Icons on top. I can not repeat either predictably.
Another curiosity is that the Gedit shot was only 46KB whereas the other two were 420+Kb originally.

You Posted:>  [QUOTE] Neither the Left side LauncherPanel nor the top Panel and top three  lines are visible.                                  I think you mean the screenshot of gedit, which looks like the *correct* full-screen behavior. Gedit's slide down menu *should*  cover a few lines when the cursor hits the top of the screen to pull it  down and neither the launcher nor the panel should be visible.[/QUOTE]No, I was referring to the FireFox image whose visible display is bounded by the dark surround of the Ubuntu Forum display and the scroll bar on the right side. I will insert the one shot I have of this here.It also shows the fullscreen extended under the launchPad as well as the top Panel
[ATTACH]212800[/ATTACH]
> **How did you get that screenshot?** I need to know in exact detail.I have concluded - although it does not explain everything, that the delay setting in Screenshot has not been working properly and was taking the image before the F11 key took effect.

What I did was this: I ran Screenshot from the Dash and locked its Launcher in the Unity LaunchPad, set to 'Grab the whole desktop', a delay of 3 secs, and 'include pointer'; the 'include the window border' option was ticked but ghosted. 
I then set up FireFox in non-maximized form, with the LaunchPad accessible, opened Screenshot, Clicked on 'Take Screenshot', pressed F11, moved the cursor to where I wanted it to be, and waited.
Then I saved the result and cropped the two FF shots in Gimp.
 
I have taken several more screenshots with 'Grab current window' selected, but most do not seem to differ greatly  from the others. In the one I am attaching the small FireFox buttons  on its menu line can just be seen through the semi-transparent toolbar dark bar, whereas on screen they are on the same level as the bar and are not moved when other lines scroll down.Edit: as clearly seen in this second screenshot, though partly obscured by the X button of the display.
[ATTACH]212801[/ATTACH]

Chao!, **bogan**.

---

### Post by quequotion on 2012-02-17
> **bogan said:**
> Hi! **quequotion**,

This is frustrating, I just spent four hours trying to answer your queries and just as I got somewhere and had a Fullscreen of FireFox with top panel icons over it, that worked, - I had a drop-down menu displayed - when I tried to get a Screenshot, a Window opened saying that a script had failed to respond and did I want to wait? Wow. No idea about the script crash... I think the forums may be going through some tinkering as there was a post about upgrading. Sorry your Firefox installation was corrupted.

> No, I was referring to the FireFox image whose visible display is bounded by the dark surround of the Ubuntu Forum display and the scroll bar on the right side. I will insert the one shot I have of this here.It also shows the fullscreen extended under the launchPad as well as the top Panel Please be careful with your vocabulary. You mean to say that it shows the fullscreen window extended under the **launcher** as well as the top **panel**.

"Launchpad" is Ubuntu/Canonical's development platform and support website.

You are spending WAY too much effort to get screenshots.

The main problem with your screenshots is the complicated method by which you are taking them.

Just press the **[PrtScr]** ("print screen") key.
It's at the top of your keyboard near the **[Pause/Break]** **[Insert]** and **[Del]** keys.

**gnome-screenshot** should appear with a dialogue asking where to save the file; if not then the file has been saved to the default location: **~/Pictures/** with a name like "*Screenshot at 2012-02-18 02:03:45.png*"

Of course, you will have to resize for the forum (1024x768 max).

"Grab current window" screenshots are no use for this thread.
Only screenshots of the entire screen, like your screenshot of firefox above, can display the behavior I'm talking about.

Anyway, ***you are experiencing the same bug I am***, as proven by your screenshot of firefox.

There **should not be** either the launcher or the panel visible in that shot. 

This is the bug I have been talking about.

You have a full-screen window with stuff appearing on top of it.

***That is NOT the correct behavior.***

---

### Post by bogan on 2012-02-17
Hi! **quequotion**,
You Posted: 
> "Grab current window" screenshots are no use for this thread.
Only screenshots of the entire screen, like your screenshot of firefox above, can display the behavior I'm talking about. I am attaching a screenshot taken as you suggested with PrtScrn, and therefore a fullscreen shot. However, it is identical with the last one I took as 'Grab current Window' with Screenshot. After all, if the Window is indeed a Fullscreen one, the two should be identical; though I fully understand your reason for wanting it to be of the Screen as a whole.
[ATTACH]212866[/ATTACH]
I am fairly sure that I know now what provokes the extension under the Top bar or 'panel', though I am unable to initiate it at will.

When I Maximize a Window, by whatever means, and it extends visibly under the top bar, pressing F11 will produce the Fullscreen display similarly extended, but in most cases the Icons are active; not as you get them, inaccessible.

If the Maximised Window only just reaches the bottom of the Top bar, or the top rows do not show even with a fully transparent Bar, then F11 will produce the 'correct' behavior with no Icons, though there may be Titles or menu headings, depending on the program - no two seem to behave in exactly the same way.

The only 'program' that I have found that predictably behaves as you describe with the 'Panel' Icons not working is a standard Terminal. In Fullscreen mode the Prompt is in the Top bar position and the cursor is unable to activate the Icons, and the only way to get out of it is to press F11 again. In fact the reason that the Mouse is unable to actvate the Icons is probably because its cursor has changed to a text cursor and is not an arrow head cursor, when it changes back the Icons are active again.

As far as my vocabulary is concerned one of the things I find very frustrating and confusing about Linux is the habit of using several different names for the same things. I know that LaunchPad is used for the bug report DB, but it seems to me to be a much more appropriate term for a collection of Launchers, as well as being more descriptive than Dock, ToolBar, Panel, SideBar, Menu, QuickList, or any of the other terms I have come across in the Forums, used to name this not much loved feature. Perhaps if the Launchers themselves were called what they are: 'Icons', the confusion would not occur. But I gather that Icon is a four letter word in Linux.

Chao!, **bogan**.

---

### Post by quequotion on 2012-02-18
> **bogan said:**
> When I Maximize a Window, by whatever means, and it extends visibly under the top bar, pressing F11 will produce the Fullscreen display similarly extended, but in most cases the Icons are active; not as you get them, inaccessible.

If the Maximised Window only just reaches the bottom of the Top bar, or the top rows do not show even with a fully transparent Bar, then F11 will produce the 'correct' behavior with no Icons, though there may be Titles or menu headings, depending on the program - no two seem to behave in exactly the same way.This is interesting. At least it shows there are some conditions for this misbehavior, and variations of it. I'm still not sure if it hints at a cause...

How's your desktop setup?
Are you using Unity (3d) as packaged (no special settings or configurations) or do you have some customized settings anywhere?

Mine is fairly customized, using CCSM as well as special options in /etc/X11/xorg.conf and the proprietary nvidia drivers.
Default settings don't change the results in my case.

> The only 'program' that I have found that predictably behaves as you describe with the 'Panel' Icons not working is a standard Terminal. In Fullscreen mode the Prompt is in the Top bar position and the cursor is unable to activate the Icons, and the only way to get out of it is to press F11 again. In fact the reason that the Mouse is unable to actvate the Icons is probably because its cursor has changed to a text cursor and is not an arrow head cursor, when it changes back the Icons are active again. Yes, that is the misbehavior.
The mouse is not the cause, but shows the symptoms.
The mouse changes to a text cursor because it *should*.
The mouse is interacting with the terminal window.
If the panel were correctly *under* the terminal and not visible, this would make sense.

> As far as my vocabulary is concerned one of the things I find very frustrating and confusing about Linux is the habit of using several different names for the same things. I know that LaunchPad is used for the bug report DB, but it seems to me to be a much more appropriate term for a collection of Launchers, as well as being more descriptive than Dock, ToolBar, Panel, SideBar, Menu, QuickList, or any of the other terms I have come across in the Forums, used to name this not much loved feature. Perhaps if the Launchers themselves were called what they are: 'Icons', the confusion would not occur. But I gather that Icon is a four letter word in Linux.I appreciate and share your frustration.
Unfortunately this problem is neither limited to linux nor those particular terms.
Words like "icon", "panel", "menu", etc., are becoming rather flexible and overlap more and more.
How do we define these as what they "are" when they combine aspects of several concepts?
We have some new terms with Unity: indicator, lens, scope, etc. which attempt to define the new interface concepts.

For example, here are some descriptions of Unity:

-*A user interface based on the desktop metaphor with some innovative design concepts, such as "indicators" which combine aspects of the classic notification-area icon with a miniature application and "lenses" have aspects of both menus, folders, search engines*.

-*A desktop management plugin for compiz that provides a vertical launcher on the right edge of the screen and a horizontal panel across the top of the screen*.

-*Ubuntu's dock and panel desktop*.

-*Canonical's compiz-based desktop paradigm which integrates menus, icons, searching and some interactive applications into two panels*. 

And so on and so forth ad infinitum.

---

### Post by bogan on 2012-02-18
Hi!, **quequotion**,

You Posted:>  How's your desktop setup?
Are you using Unity (3d) as packaged (no special settings or configurations) or do you have some customized settings anywhere?Apart from where I have detailed changes, for the purposes of your Thread I have been using the 3D Ubuntu (Unity) log-in. I have used CCSM, but mainly to check that all the Unity Plug-ins were installed.

As far as I know it is bog standard, other than that Gnome 3 is installed but not used.
I have also used MyUnity to reduce the Launcher size to the minimum and set the transparency/opacity.

I assume that other changes I have made when logged-in to Gnome Classic are not relevant, as the Top Bar behavior we are concerned with does not occur then.
BTW: in Classic it is possible to Grab & Drag a Window right up to the top of the screen, occupying the Top Bar space, but F11 still gives the 'correct' result.
Using 2D Unity produced the same results as 3D.

My Video card in this Win7 m/c is an Nvidia GT520 1GB, and uses the NVIDIA x86-290.10  proprietary driver.

At this moment I am using my other Desktop computer, which has a similar set-up, except 11.10 is an updated installation, it does not have Gnome3, and it runs WinXP;  whereas the first one has a clean install of 11.10 and runs Win7.
 In both cases the Ubuntu installations are on separate external Sata3/USB Hdds,

So far - its only an hour or so, and I have been updating everything - I have not been able to reproduce
the' incorrect' behaviour; but I attach a PrtScr image of interest with a Terminal Window F11'd to Fullscreenh. 
[ATTACH]212912[/ATTACH]
NB the cursor at the moment before I took the shot was a Text cursor.** not **an arrowhead as shown. and it shows the only interaction with the Top Bar, which  was, when clicked over it, to display the Terminal Menu headings; though neither they, nor the icons were active, merely visible through the transparent Terminal Window. 

Chao!,** bogan.**

---

### Post by quequotion on 2012-02-19
> **bogan said:**
> BTW: in Classic it is possible to Grab & Drag a Window right up to the top of the screen, occupying the Top Bar space, but F11 still gives the 'correct' result.
That's interesting... I took a moment to check things out in Unity 2D, but I haven't installed the gnome-fallback ("Classic") or Gnome Shell sessions.
> Using 2D Unity produced the same results as 3D.
Not for me. I was able to get correct full-screen in Unity 2D.
I don't know why, but windows properly full-screen over the Unity 2D panel so it is not visible.

By the way, another vocabulary problem...
"Gnome 3" is often used interchangably with "Gnome Shell".
In fact "Gnome Shell" is only the desktop interface component of "Gnome 3" and the title of it's default desktop session.
"Gnome 3" also includes several other components, particularly the gtk3 toolkit and a bundle of software derived from it, like the file browser nautilus.
"Classic", "Ubuntu Classic", "Gnome Classic" and "gnome-fallback" all refer to a desktop session comprised of a Gnome 2 look-alike desktop interface built from gtk3 components.

Ubuntu 11.10 has Gnome 3 and uses all of it's components except the shell by default, unless you installed Kubuntu or Xubuntu.

> So far - its only an hour or so, and I have been updating everything - I have not been able to reproduce
the' incorrect' behaviour; but I attach a PrtScr image of interest with a Terminal Window F11'd to Fullscreenh. I see. Your set up isn't much different than mine. I wonder why our desktops behave differently.

How about your nvidia settings? Anything special? Overclocking?

> NB the cursor at the moment before I took the shot was a Text cursor.** not **an arrowhead as shown. Yeah, it probably changed because gnome-screenshot took focus, even though it wasn't visible yet.
Notice the terminal cursor has become an outlined rectangle, not a filled one.

---

### Post by bogan on 2012-02-19
Hi!, **quequotion**,

You Posted: > Ubuntu 11.10 has Gnome 3 and uses all of it's components except the shell by default, unless you installed Kubuntu or Xubuntu.I am not sure this is right, at least it does not tie in with what I have got: Log-in options, { apart from Gnome (No Effects) & User defined } include: 

1: 11.10 -16 on USB: Ubuntu. Ubuntu 2D
2: 11.10-16 + Gnome3: Gnome, Gnome Classic, Ubuntu, Ubuntu 2D.
3: 11.10-16 + gnome-fallback: Gnome Classic, Ubuntu, Ubuntu 2D.
{'Gnome' in item 2 is what I assume to be Gnome-Shell, ie it is totally different from any of the others.}
> [QUOTE]Using 2D Unity produced the same results as 3D.Not for me. I was able to get correct full-screen in Unity 2D.
I don't know why, but windows properly full-screen over the Unity 2D panel so it is not visible.[/QUOTE]I have begun to think this whole mystery is just that Panels set to Auto-hide when a Window touches their space, do so with either a 'normal' or a Maximised Window, but not with a FullScreen Window.

I know that that is not always so, ie with gedit they stay hidden, or at least  they stay beneath the Window and hence are not visible  - except for a transparent Window - nor active.

The 'incorrect' behavior is when - for whatever reason - the Window is displayed under the Panel, even when it has the Focus. ( or am I over-simplifying things.? )

The question I have is another vocablary issue: Panels are said to  'hide', when in fact they scroll aside or up/down, when a Window  encroaches or the Mouse Cursor triggers the effect. This is very noticeable with  FireFox, because it scrolls several toolbars off the screen.

In other words, it is not a question of:> :windows properly full-screen over the ..... panel so it is not visible.The Panels should not be there but off the screen.> How about your nvidia settings? Anything special? Overclocking?I am using the proprietary 290.10 driver and the only setting I have altered is to set the resolution to 1280x1024x24 which is the lower resolution of my monitors - used singly.  No overclocking or multiplexing, CLI or whatever.

Also I am using the Default Desktop Manager, not one of the other various alternatives, and nothing has been Tweaked. The Installation on the USB is totally virgin and I just finished wiping it and updating a re-installation. It behaves the same as the other two Hdd installs although it does not have any extra Gnome apps added.

Chao!, **bogan.**

---

### Post by quequotion on 2012-02-28
> **bogan said:**
> I am not sure this is right I am.
Check the ".session" files in /usr/share/gnome-session/sessions/

Ubuntu = gnome-session with Unity (3D) and Compiz
Ubuntu 2D = gnome-session with Unity 2D and Metacity
Gnome = gnome-session with Gnome Shell and Metacity
Gnome Classic = gnome-session with (shoddy) Gnome3 imitation of Gnome2 Panels and Metacity

Canonical did not innovate a whole new desktop; they just re-branded Gnome.
Nearly all of ubuntu's default software is GTK.

> I have begun to think this whole mystery is just that Panels set to Auto-hide when a Window touches their space, do so with either a 'normal' or a Maximised Window, but not with a FullScreen Window.As I have said, *there are no settings to make this panel auto-hide*. It should be layered under the windows as it was in your recent screenshots of firefox, gnome-terminal, and the older shot of gedit.


> I know that that is not always so, ie with gedit they stay hidden, or at least they stay beneath the Window and hence are not visible  - except for a transparent Window - nor active.That is how the panel should behave.
I cannot reproduce this with any applications in Unity (3D).
I really wish I could, but I can't.

> The 'incorrect' behavior is when - for whatever reason - the Window is displayed under the Panel, even when it has the Focus.Yes and no. I would define it this way:

The incorrect behavior is when the panel is displayed over a full-screen window that has focus.

There are only two circumstances for which any object (panel, window, menu, notification, etc) should take focus and be displayed over a full-screen window:

1. User action has created a new object or raised an existing one.
2. A process requring immediate attention has created a new object or raised an existing one.

In both cases, the object should dissappear when returning focus to the full-screen window.
There are no circumstances in which an object should be displayed over a full-screen window *without* taking focus.

> The question I have is another vocablary issue: Panels are said to  'hide', when in fact they scroll aside or up/down, when a Window  encroaches or the Mouse Cursor triggers the effect. This is very noticeable with  FireFox, because it scrolls several toolbars off the screen. Yes, "hide" is also a vague term.
To be precise we should say that objects either "scroll off" the screen (hiding) or "stay under" another object (layering).

> In other words, it is not a question of:The Panels should not be there but off the screen. That is an acceptable solution.
Actually I hope to have the layering problem fixed, but a scroll away setting for the panel would make me just as happy.

---

### Post by bogan on 2012-02-28
Hi!,** quequotion,**

Thanks for your detailed elucidation.

We seem to be in general agreement, even if our displays sometimes seem to react differently.

I am still very surprised that no-one else has entered a contribution to this thread.

Chao!, **bogan.**

---

### Post by quequotion on 2012-03-02
Yeah... between the two of us we have plenty of information here but no solutions...

---

### Post by chicken159 on 2012-03-08
Anyone reported a bug on this? I have the same thing - every fullscreen application appears behind the top panel though behaves as if it is behind it...

ALSO, with the launcher in its 12.04 default behaviour of never hide, the Launcher does the same and appears on top whilst being unusable.

I have seen bug reports relating to this behaviour on a multi-monitor setup, but was beginning to wonder if this is not so much a bug as REALLY annoying design?

---

### Post by chicken159 on 2012-03-08
Bit of an update...

I seem to have fixed this by randomly crashing about in ccsm...

I was using Cube, so in the interests of getting to a 'normal' setup I switched to desktop Wall...with the usual conflicts and disabling then re-enabling Unity. I did have Gnome Compatibility active, which seemed to cause conflicts with Unity at some point so I have disabled it.

The always-on-top Unity behaviour disappeared when using Desktop Wall...so I figured what the hell and re-enabled Cube. Success! I now have fullscreen applications, Cube, and no Unity appearing on top...

Slight warning - I did the same thing on a second machine and it didn't work - but since I had exported the profile from ccsm t Ubuntu One I just imported it into the new machine and have got rid of this bug in both machines.

---

### Post by Nerdy314159265 on 2012-03-12
Is this along the same lines as your problem? For me everything seems to work except Firefox fullscreen, especially with Youtube fullscreen. This is a screenshot of a Youtube video fullscreened.

[http://dl.dropbox.com/u/4240139/Screenshot%20from%202012-03-12%2012%3A50%3A13.png](http://dl.dropbox.com/u/4240139/Screenshot%20from%202012-03-12%2012%3A50%3A13.png)

The only thing is I wasn't even seeing part of the Youtube panels except for the progress bar behind the top and bottom gnome panels.

P.S. I'm using gnome classic, and Ubuntu 12.04

---

### Post by quequotion on 2012-03-13
> **chicken159 said:**
> I had exported the profile from ccsm t Ubuntu One I just imported it into the new machine and have got rid of this bug in both machines.

You may be on to something here.

Perhaps this is some undocumented setting / feature that's been left enabled by old profile data. Technically that isn't possible, since I saw the same bug on different machines and even in fresh installs, but then again anything's possible.

Can you zip and upload your compiz profile? I'd love to compare it to mine.

> **Nerdy314159265 said:**
> Is this along the same lines as your problem? For me everything seems to work except Firefox fullscreen, especially with Youtube fullscreen. This is a screenshot of a Youtube video fullscreened.

[http://dl.dropbox.com/u/4240139/Screenshot%20from%202012-03-12%2012%3A50%3A13.png](http://dl.dropbox.com/u/4240139/Screenshot%20from%202012-03-12%2012%3A50%3A13.png)

The only thing is I wasn't even seeing part of the Youtube panels except for the progress bar behind the top and bottom gnome panels.

P.S. I'm using gnome classic, and Ubuntu 12.04

Yes and no.
I see the panel showing (partially) over your full-screen application, but you have some additional graphical corruption near the top and bottom of the screen.
This could be two bugs.

---

### Post by quequotion on 2012-03-13
[Here's an interesting blog post.](http://somethingididnotknow.wordpress.com/2012/02/09/set-fullscreen-windows-to-go-over-gnome-shells-and-unitys-top-bar-with-python-and-glade/)

According to this, it could be an undocumented design flaw.

Apparently windows in full-screen must have their window type changed to "Popup" to get over the panel in gtk3 (both gnome-shell and unity are gtk3).

Why then should not windows that are full-screen automatically be designated "Popup" or better yet why not allow the full-screen function to simply make things full-screen?

Also, bug reports:
[This one was expired](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/792690). Probably ignored because the description was unclear.
[They say this is a multimonitor-only, and therefore different, bug](https://bugs.launchpad.net/unity/+bug/734908). I believe they are related bugs, if not the same bug.

---

### Post by chicken159 on 2012-03-15
Here's my ccsm profile...in case it helps! I suspect it has some leftover settings lying around from several iterations of update and trying things out (and it does exhibit the ongoing annoying previous-workspace-flash bug - hence the name).

Also - note that on the original machine it was just the process of going from cube > wall > cube which seemed to clear the problem (which is probably easier - if a bit scary what with it disabling unity in the process).

Be interesting to know what changed to sort this out...

---

### Post by quequotion on 2012-03-16
> **chicken159 said:**
> Here's my ccsm profile...in case it helps! I suspect it has some leftover settings lying around from several iterations of update and trying things out (and it does exhibit the ongoing annoying previous-workspace-flash bug - hence the name).

Also - note that on the original machine it was just the process of going from cube > wall > cube which seemed to clear the problem (which is probably easier - if a bit scary what with it disabling unity in the process).

Be interesting to know what changed to sort this out...

Thanks!
I'll take a look at this tonight.

In the mean time, maybe you've already heard, some progress is being made on the windows flashing on the wrong workspace issue:

It's not a fix, but it will do for now. Check out [this thread](http://ubuntuforums.org/showthread.php?t=1938942) and my [small revision](http://ubuntuforums.org/showthread.php?p=11768939#post11768939).

---

### Post by chicken159 on 2012-03-16
Yeah thanks - I'd seen that - I think I've just got used to the flashing such that it doesn't annoy me enough and will wait and see what happens with a durable fix, which just shows that the rotating cube is about usability and productivity, not just looking cool ;) (On the other hand...I was using transparancy to see where everything was on my desktops before...but I'm liking my new pangolin wallpaper so much that its turned off except on rotate now...and thats just about looking good!)

---

### Post by Nerdy314159265 on 2012-03-19
> **quequotion said:**
> 
I see the panel showing (partially) over your full-screen application, but you have some additional graphical corruption near the top and bottom of the screen.
This could be two bugs.

I forgot to mention, those graphical corruptions were only in the screenshot. Just looking at the screen it didn't show up like that at all. I had the panels covering the Youtube window without any other glitches at all, they were simply overlaid.

---

### Post by quequotion on 2012-03-20
> **chicken159 said:**
> Also - note that on the original machine it was just the process of going from cube > wall > cube which seemed to clear the problem (which is probably easier - if a bit scary what with it disabling unity in the process).

Can you post the profile from the original machine?

I tried your suggestion.

Interestingly, full-screen worked properly with the desktop wall.

Also, I wasn't required to reload unity while switching from cube to wall.

Unfortunately compiz crashed when I attempted to change back to the cube.

I was forced to log out and log in again and found that panels were still visible on top of full-screen windows.

---

### Post by chicken159 on 2012-03-20
> **quequotion said:**
> Can you post the profile from the original machine?


Sorry - I've been swapping profiles around between machines so much I don't actually know where they came from any more...suspect I should be more methodical. I've got a fresh install on my Dell Mini 10v that I'll set up from scratch and see if that works with fullscreen and cube then post the profile if it works.

The profile posted seems to get fullscreen working on my other machines though.

---

### Post by alfsagen on 2012-03-21
.

---

### Post by alfsagen on 2012-03-21
> **grahammechanical said:**
> In full screen mode the windows are moving under the panel. That is what is happening and it should not happen.

There is no intention to make the top panel disappear when a window is maximised. Remember, it is the intention with unity for the top panel to be the place for the max, min & close buttons of a window as well as for app indicators.

I am using 12.04 development release and maximised windows stay below the top panel but up against it.

we have the ability to bounce a window against the top panel and when we let go of the mouse button the window maximizes. Then when we move the mouse over the top panel the pointer should change to a hand icon so that we can grab the top of the maximized window and pull it down at which point the window snaps back to its original size. My point is that the maximized window should not be under the top panel. That is the problem and not the one of the top panel not disappearing.

I do not know how you stop this from happening but my guess is that it is to do with a setting in CCSM. I cannot check this out as I am not using 11.10 but 12.04 and there are changes to CCSM in 12.04.

Regards.

P.S. It occurs to me that your thread title is a little misleading. This is not a problem with maximized windows. Is it? It is a problem with playing video in full screen mode. Is it not?


You are discussing *maximised* windows, not *full screen*.
These are 2 different things.

Simple example: Open Firefox, then press F11 --> Firefox goes into  *full screen* mode (which is more than maximised), and it should cover  the Unity status bar at the top of the screen.

---

### Post by eazymomo on 2012-03-24
Hi, i am experiencing the same issue.  

Top panel remaining visible when Fullscreen-ing (not maximising) any application - most noticeably with video (VLC/totem) as this is where i use fullscreen the most - but have checked it with Chromium (F11) and Gimp with the same behaviour being apparent.

I cannot be 100% sure but i think when i initially installed (before messing with CCSM and crashing unity a couple of times, or messing around with desktop themes) i watched some videos in fullscreen and the problem wasn't there - but it is a new computer with fresh windows7 and 11.10 so i might have been using vlc under win7.

This is an issue for me as i use Gimp and VLC a lot for my work. also i am currently without any other means of watching video/TV other than my laptop and i'm just a stickler for fullscreen viewing.

I find that it is hard to change settings in CCSM without unity going 'mental'/resetting or even crashing and having to log in and find interesting ways to run the terminal etc....  i have enabled the desktop cube and saw on an earlier post that i might want to try the wall but whenever i try to enable wall or disable cube it just crashes unity.

From what i have seen here there are others with the problem and it is not just a result of my gung-ho settings-amashing attitude as usual.  I find it to be a really strange oversight to make fullscreen windows/apps only overlay this panel if they are of the type 'pop-up' (not that i fully understand what this means) but surely unity should have been developed to utilise whatever coding/designation was already in use with popular applications - so that the user experienced the same functionality as previously in gnome shell/ubuntu or with other operating systems.

anyway longterm n00b here who keeps ending up behind the curve with ubuntu with each new install.

---

### Post by eazymomo on 2012-03-25
hey there - not confuse the issue - purposefully anyway - but just experienced the maximising issue as well... bloody annoying.  I think i am going to do a fresh install, but i might not.

If i do i will let you know how i get on.  will be a couple of days till i do IF i do - in the mean time if anyone here wants any info from me i will be only to happy to oblige.

cheers, Iain

---

### Post by Gasmart on 2012-03-27
Hi, I also have this problem...  the Unity status bar is over my tabs in firefox.

---

### Post by Nerdy314159265 on 2012-04-09
Has anyone made any progress in figuring this out. I attempted to use CCSM to set a window rule that it would always fullscreened. What ended up happening is that it would flick fullscreen, then the bars would come back, like CCSM was working but the bars tried to overrule it.

---

### Post by josephellengar on 2012-05-05
I'm going to revive this thread, if nobody minds. I have the same problem when watching YouTube or VLC videos, for example, and do have Desktop Wall and Legacy Fullscreen Support enabled, and neither have helped. Has anybody come up with a better solution?

---

### Post by msuug on 2012-05-05
> **josephellengar said:**
> I'm going to revive this thread, if nobody minds. I have the same problem when watching YouTube or VLC videos, for example, and do have Desktop Wall and Legacy Fullscreen Support enabled, and neither have helped. Has anybody come up with a better solution?

I also have exactly the same problem with every application. Considering in terms of screen size value, I thought the launcher was put on the left to increase the vertical screen space. However on coming from 10.04 to 12.04, about a cm has been knocked off the top, whereas in 10.04 the panel was set to autohide.
Additionally it makes it look (at least to me) like a fragmented desktop and interferes severely with several applications which have panels in the same area. see screenshot for example

---

### Post by josephellengar on 2012-05-06
bump

---

### Post by foogoo on 2012-05-07
I now have this problem as well since upgrading to 12.04 using the Gnome desktop. When using VLC or Virtualbox (these are the only applications I've tried) fullscreen, both the top and bottom panels will come up after about 30 seconds. Clicking on the application will make them disappear, only to have them come back momentarily.

Any help? It's very annoying.

---

### Post by Avaritia on 2012-05-08
I can confirm this as well, I have tried 5 different programs in WINE and 2 native games since I upgraded to Ubuntu 12.04, in all of them the bar appears at the top in fullscreen mode and the mouse 'leaves' the game window.

The unity menu also appears at the side in fullscreen programs as well if I dont tell it to hide.

Did the Ubuntu devs not stop and think for a second "Hang on guys, how come Ubuntu is the only distro, out of hundreds that is stiill using compiz?" 

Compiz has never worked with fullscreen programs properly, thats why some distros have removed it from there repositories altogether.

Ubuntu should warn people that even native games do not run well with compiz, not doing so is misleading.

---

### Post by jerome1232 on 2012-05-08
Wow op, you simply assume way to much. Just because you experience an issue doesn't make it a universal issue.

In my screenshot, I have two monitors, which is is why you see a small desktop to the left of my primary display.

---

### Post by bachinchi on 2012-05-10
I have this issue when using Wine, I'm attaching a screenshot showing it.

This can be fixed unticking the 'Allow window manager to control the windows' in Wine options. But doing that also brings another issue, I couldn't close the Wine App for some odd reason.

---

### Post by tg_nightnight on 2012-05-17
I had/have the same problem: my game was showing up as a alpha-trasparency on top of the unity desktop.

The following is not really a solution, per say, but rather a method that allowed me to play my game: **I used xephyr**. 
This may or may not work for you and you might want to fudge with the settings, but this is what I did:
```
sudo apt-get install xserver-xephyr
```(Note: before executing the following line, remember that **one way to exit xephyr fullscreen** in ubuntu 12.04 unity is to type **ctrl-alt-del**)
Run xephyr in fullscreen mode:
```
Xephyr :1 -ac -br -fullscreen -reset -extension Composite
```then, concurrently in another terminal, run:
```
DISPLAY=:1 /path/to/your/game
```

---

### Post by frankbooth on 2012-05-20
> **bachinchi said:**
> 
This can be fixed unticking the 'Allow window manager to control the windows' in Wine options. But doing that also brings another issue, I couldn't close the Wine App for some odd reason.


I unticked the following:
[LIST]
[*]Allow the window manager to decore the windows
[*]Allow the window manager to control the windows
[/LIST]

This worked out perfectly for me without causing new issues, thanks for the tip.

---

### Post by josephellengar on 2012-05-20
Well none of that solves the problem for native applications. I'm still looking for that solution if anybody has it.

---

### Post by quequotion on 2012-05-22
> **jerome1232 said:**
> Wow op, you simply assume way to much. Just because you experience an issue doesn't make it a universal issue.

In my screenshot, I have two monitors, which is is why you see a small desktop to the left of my primary display.

I don't think so. I honestly don't.

Your screenshot does nothing to prove or disprove my point.

I am *not* using two monitors and your screenshot shows the panel displayed on top of other windows in at least one of your desktops.

Could you provide a screenshot of an application in full-screen (*not maximized*), on a **single** monitor system, with absolutely no trace of the unity panel across the top of the screen?

The main problem with this issue is that only a handful of people seem able to grasp what the problem is.

By the way, my name is not "op". It's quequotion. This isn't 4chan.

---

### Post by quequotion on 2012-05-22
> **josephellengar said:**
> Well none of that solves the problem for native applications. I'm still looking for that solution if anybody has it.

Good news / Bad news

Bad news first:
As of yet only a dozen or so people have realised what's wrong.

Perhaps switching between Unity+Wall and Unity+Cube will get one or the other to work.
Personally I dont have any more use for Unity 2.5D than Unity 2D and this apparently doesn't work for everybody.

Good news:
One of the more progressive & active compiz developers seems to have taken an interest in my [bug report](https://bugs.launchpad.net/unity/+bug/931460)!

---

### Post by jawahar on 2012-05-24
quequotion,

It does appear most people are missing the distinction between fullscreen and mazimized windows. 

Other forums have also mentioned that this is a known bug. The following is similar to your report but is unassigned and is assigned a low priority.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/977438](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/977438)

While waiting for a fix however, one of the workarounds in the following forum might help. Disabling the "Place Windows" functionality from the Compiz Settings Manager worked for me.
[http://askubuntu.com/questions/126447/fullscreen-gnome-classic-ubuntu-12-04](http://askubuntu.com/questions/126447/fullscreen-gnome-classic-ubuntu-12-04)

---

### Post by jerome1232 on 2012-05-24
> **quequotion said:**
> I don't think so. I honestly don't.

Your screenshot does nothing to prove or disprove my point.

I am *not* using two monitors and your screenshot shows the panel displayed on top of other windows in at least one of your desktops.

Could you provide a screenshot of an application in full-screen (*not maximized*), on a **single** monitor system, with absolutely no trace of the unity panel across the top of the screen?

The main problem with this issue is that only a handful of people seem able to grasp what the problem is.

By the way, my name is not "op". It's quequotion. This isn't 4chan.

A) No it doesn't, no window is full screened on that second monitor thus the panel is, as expected, displayed.

B) My main point is this is not a "feature" of Unity, it's a bug a few people seem to be experiencing, likely related to compiz.

---

### Post by josephellengar on 2012-05-24
Just turn off place windows in CCSM. Fixed this and other bugs for me.

---

### Post by quequotion on 2012-05-25
> **jerome1232 said:**
> A) No it doesn't, no window is full screened on that second monitor thus the panel is, as expected, displayed.

So the purpose of the screenshot as relevant to this thread was..?

> B) My main point is this is not a "feature" of Unity, it's a bug a few people seem to be experiencing, likely related to compiz.

I was very concerned that it might be a feature, but it's more likely an oversight.

The bug is occuring regularly with Unity+Cube desktops and occasionally in Unity+Wall desktops. It is not quite as ubiquitious as I originally thought, but only because Unity+Cube is not the default desktop.

A certain change in gkt3 may require window managers to reinterpret deprecated full-screening methods until sofware becomes "standards" compliant; therefore this may be related to a known bug in Gnome desktops.

Until very recently, the cube has been excluded from development in compiz while compiz development progressed very slowly throughout the 12.04 deveopment cycle in many fragmented bzr branches with a thousand bugs left in limbo.

Luckily, rumours of it's death were completely absurd; development has picked up for 12.10.

Altogether I'd become rather frustrated with this issue since it seemed like hardly anyone understood it, the bug reports are low-priority, and the support for the Cube seemed likely to be deprecated.

Sorry if I took some of that frustration out on this thread.

---

### Post by quequotion on 2012-05-25
> **josephellengar said:**
> Just turn off place windows in CCSM. Fixed this and other bugs for me.

Do you use a Unity desktop or a Gnome desktop?

This didn't work for me, but I am using Unity+Cube.

The symptoms in Gnome sound very similar and are probably related.

---

### Post by quequotion on 2012-05-25
More good news!

The multimonitor bug report I mentioned before has become the master bug report for this issue, which is now recognized as a more general issue and has high priority:

[Bug #734908: Unity is visible on top of fullscreen apps](https://bugs.launchpad.net/unity/+bug/734908)

I love the smell of progress in the morning.

---

### Post by josephellengar on 2012-05-25
> **quequotion said:**
> Do you use a Unity desktop or a Gnome desktop?

This didn't work for me, but I am using Unity+Cube.

The symptoms in Gnome sound very similar and are probably related.

Gnome classic.

---

### Post by jerome1232 on 2012-05-25
> **quequotion said:**
> So the purpose of the screenshot as relevant to this thread was..?


If you can't figure out why a screenshot showing a full screened application with no panel over it is relevant to this thread... Particularly when you requested such a screenshot be provided.

Unity has not been playing well with other compiz plugins since the get go, getting those bugs squashed is important, perhaps someday soon I can use a sphere with 3d windows again :D

---

### Post by quequotion on 2012-05-26
> **jerome1232 said:**
> If you can't figure out why a screenshot showing a full screened application with no panel over it is relevant to this thread... Particularly when you requested such a screenshot be provided. but you just said there weren't any full screened windows in the screen shot?

Any way, dual monitor desktops and single monitor desktops have different designs.
It wouldn't make sense to have the panel streched across all monitors or have individual panels on each monitor.
I assume that there's only one panel on one monitor and the other monitor doesn't have a panel to be getting in the way of full screen.

That is why I found your screenshot to be irrelevant in the first place.

Then you agreed with me.... or so I thought?

> Unity has not been playing well with other compiz plugins since the get go, getting those bugs squashed is important, perhaps someday soon I can use a sphere with 3d windows again :D This day is getting closer. Work is getting done on the cube again and an SRU is in the works for Precise. Quantal should have the best compiz experience since before all this Unity nonsense.

---

### Post by Rave2Rave on 2012-06-16
as already mentioned:

this bug (i was also affected) comes up due to a wrong compiz-config, or better, a compiz-config, that doesn't really work correctly with unity/gnome at the moment.

my solution:

disable the "put windows" plugin (german: "fenster platzieren")
just to be on the safe side, i disabled every plugin, i don't really need and
which literally cries out for bringing up that bug, like
desktop wall and cube.

...so happy i could solve that annoying bug!...for me^^

---

### Post by quequotion on 2012-06-18
> **Rave2Rave said:**
> as already mentioned:

this bug (i was also affected) comes up due to a wrong compiz-config, or better, a compiz-config, that doesn't really work correctly with unity/gnome at the moment.

my solution:

disable the "put windows" plugin (german: "fenster platzieren")
just to be on the safe side, i disabled every plugin, i don't really need and
which literally cries out for bringing up that bug, like
desktop wall and cube.

...so happy i could solve that annoying bug!...for me^^

I've never used the "put windows" plugin, but I still have this bug.

Compiz misconfiguration may indeed be a possiblity, as solutions such as "enable/disable plugin x" or "disable and then reenable plugin y" and vice-versa seem to work on a case-by-case basis.

I haven't had any more luck with a clean install than reconfiguring a used one however...

--edit--

> just to be on the safe side, i disabled every plugin, i don't really need and which literally cries out for bringing up that bug, like desktop wall and cube.

Wait, are you saying you diabled *both* wall *and* cube as well? No wonder you don't have the bug!

---

### Post by Alexislavie on 2012-06-18
Try this :
sudo add-apt-repository **ppa:lavie-alexis/compiz-precise+placepluginfixed**           
sudo apt-get update
sudo apt-get upgrade

Disconnect from your session and reconnect to see the changes, it worked for me under gnome classic.

---

### Post by quequotion on 2012-06-20
> **Alexislavie said:**
> Try this :
sudo add-apt-repository **ppa:lavie-alexis/compiz-precise+placepluginfixed**           
sudo apt-get update
sudo apt-get upgrade

Disconnect from your session and reconnect to see the changes, it worked for me under gnome classic.

No effect for Unity/Cube :(

---

### Post by RottNKorpse on 2012-06-26
I seemed to have found the solution...at least it is working for me for over a week with no occurrence of the top panel being on top anymore.

What I did was installed "compiz-plugins-extra" package from the software centre and that seemed to have solved it completely.

[https://apps.ubuntu.com/cat/applications/compiz-plugins-extra/](https://apps.ubuntu.com/cat/applications/compiz-plugins-extra/)

Give it a try and let me know if this fixed it or not.

---

### Post by quequotion on 2012-06-30
> **RottNKorpse said:**
> Give it a try and let me know if this fixed it or not.

I've almost always had plugins-extra installed, but haven't noticed any difference with or without it.

---

### Post by haresear on 2012-06-30
> **RottNKorpse said:**
> I seemed to have found the solution...at least it is working for me for over a week with no occurrence of the top panel being on top anymore.

What I did was installed "compiz-plugins-extra" package from the software centre and that seemed to have solved it completely.

[https://apps.ubuntu.com/cat/applications/compiz-plugins-extra/](https://apps.ubuntu.com/cat/applications/compiz-plugins-extra/)

Give it a try and let me know if this fixed it or not.

I tried this, but it didn't work for me.

---

### Post by quequotion on 2012-06-30
***It's a rendering bug in Unity.***

Following the [bug report](https://bugs.launchpad.net/unity/+bug/734908), it would seem this is pretty much taken care of in bzr.

This [merge log](https://code.launchpad.net/~vanvugt/unity/regionalDamage/+merge/109809) shows the work that's been done this month.

Now we wait for testing and for packages to get rolled out.

I'm going to try compiling unity and nux from bzr for now.

**edit**
There are also daily builds available in the bleeding-edge [Unity Staging PPA](https://launchpad.net/~unity-team/+archive/staging/).
Unfortunately the merge has not yet been approved, so the changes haven't made it in yet.

If it works, I will be delighted to mark this thread solved.

Crossing fingers!

---

### Post by Ubun2to on 2012-06-30
Simple solution.
1. Install MyUnity.
2. Open MyUnity.
3. Change behavior from "Fixed" to "Hidden."
I figured it out myself.
Anyway, in 11.10, the default action was to hide, and in 12.04, the default action is to stay on top (which is what I like, personally).
You can also sorta hide the date/time bar at the top by doing this:
1. Open MyUnity.
2. Go to the Panel tab.
3. Set Transparency to 100%.
4. Make sure "Transparency maximized toggle" is turned off.
I also figured that out myself.

---

### Post by quequotion on 2012-07-08
> **Ubun2to said:**
> Simple solution.
1. Install MyUnity.
2. Open MyUnity.
3. Change behavior from "Fixed" to "Hidden."
I figured it out myself.This will hide the unity ***launcher***.
This can also be achieved with ccsm.


This thread is about what you call the "date time bar".> You can also sorta hide the date/time bar at the top by doing this:
1. Open MyUnity.
2. Go to the Panel tab.
3. Set Transparency to 100%.
4. Make sure "Transparency maximized toggle" is turned off.
I also figured that out myself.Unfortunately this is all that can be done about the unity ***panel*** for the moment.
This can also be done in ccsm.

We've already discussed most of your ideas earlier in this thread (posts #7 and #21), though not in the context of a solution.
Unfortunately, the issue has been plagued with communication problems, misunderstandings, and misconceptions.

Luckily, [the problem has been identified]("https://bugs.launchpad.net/unity/+bug/734908") and a fix is already in the bzr.

---

### Post by quequotion on 2012-07-12
Good news / Bad news

There is a fix released... for quantal (12.10)

Not *yet* for precise.

I don't recommend installing the quantal packages in precise; it didn't go well for me.

I ran into a new bug, which is apparently not happening in quantal, wherein all of unity blinks on and off constantly.

Work continues, and precise will get a backported release eventually.

---

### Post by beccatoria on 2012-07-25
Not sure if this is useful, but mark me as another person experiencing this glitch under Gnome Classic + Compiz that got it fixed by turning of "place window".  I know that's not helping with Unity + Compiz, but I figure it's data for those of us with Classic?  

Hope a fix is released for you soon, OP!

---

### Post by quequotion on 2012-07-28
> **beccatoria said:**
> Hope a fix is released for you soon, OP!

Please, call me quequotion, or QQ or que or whatever, but "OP" just doesn't feel right outside of 4chan.

I'm hoping the issue will be worked out soon; but it seems the problem is difficult to resolve.

Supposedly, a fix has been released for Quantal and will be backported to Precise eventually.

Ambitious as I am, I took it upon myself to install Quantal's Unity and Compiz in Precise.

At first, this did not go well as the proposed fix resulted in another, even more frustrating glitch.
Fortunately, the new glitch was tracked down and stamped out rather quickly.
Unfortunately, at no time did I ever see any  improvement in Unity's behavior.

The panel is still displayed on top of all full-screen applications in Unity 6.0.

Whether that is because I have installed Unity 6.0 in Precise, or because the bug is not fixed, remains to be seen.

---

### Post by ahgblopes on 2012-08-03
> **josephellengar said:**
> Just turn off place windows in CCSM. Fixed this and other bugs for me.
I'm running Unity on GENTOO, and it works for me!!! also,  various bugs were corrected with this!!! thank you very much!!!

---

### Post by quequotion on 2012-08-03
Another round of screenshots.

All of these screenshots show one thing:

Unity's panel is always visible.

It doesn't seem to matter what is going on, whether there's a full-screen app, a screensaver, or when the desktop cube is in mid-rotation.

In any test case I can test, when using unity with the desktop cube, the panel is always visible.

I've also attached these to [a new bug report]("https://bugs.launchpad.net/unity/+bug/1025535").

Interest in the issue seems to have waned.

---

### Post by ksanger on 2012-08-03
Found you wrong today.  Logged into my computer to find Firefox occupying the whole screen with no file menu bar nor system items.  Hit F11 to get a file menu and close firefox.  Then found no unity icons nor system icons just a background.  Luckily rebooting gave me unity icons and system items back but it would be nice to know how and whey they disappeared and how to get them back.

---

### Post by quequotion on 2012-08-04
> **ksanger said:**
> Found you wrong today.  Logged into my computer to find Firefox occupying the whole screen with no file menu bar nor system items.  Hit F11 to get a file menu and close firefox.  Then found no unity icons nor system icons just a background.  Luckily rebooting gave me unity icons and system items back but it would be nice to know how and whey they disappeared and how to get them back.

That's interesting.

Sounds like unity crashed; this happens to me from time to time as well.
Usually I have that kind of problem after changing settings in CCSM, but it's happened at boot in the past.

Normally, when you have firefox in full-screen (F11), are the menubar, system icons, etc visible? Don't they get in the way of the search and address boxes?

Do you use unity with a Desktop Wall or a Desktop Cube?

Desktop Wall seems to be fixed, but Desktop Cube has a deeper problem I think.

---

### Post by ksanger on 2012-08-04
Tried Firefox in full screen mode, F11.  Menu bar and system icons do not show up.  Neither do the Unity quick launch icons.  Hitting F11 again brought them back.  (This time).

I have no idea what desktop wall or desktop cube is.  I assume I have a wall.  I just installed the normal distro from a copy burned to cd.

I have been logged in for well over 1 week.  Note I've never left my systems on like this before.  I used to power down after every use.   Is it normal to have to reboot Ubuntu occasionally like Windows?

---

### Post by firekage on 2012-08-15
I will add few words myself. I have two instances of Ubuntu:

-the one is from upgraded 11.10 to 12.04
-the second one is a clean installation of 12.04

I have the same bug/problem with visible Unity panel with full-screen apps ( i don't write about maximized apps but full-screen apps) with upgraded 11.10 to 12.04 but on a fresh install with 12.04 i don't have this bug and it has not occured yet. I have 3d Unity, i have cube enabled with 3d "effects" (like water rain, deformations and so on).

Still don't know why on upgraded version it occurs while on clean install it doesen't not. As a matter of fact in my case this is true rather for using players like movie players because when i have full-screened firefox than it is under the panel but i can use panel while when i have full-screened movie players, and im watching something than panel is visible, not usuable, i can't click at anything on it.

---

### Post by quequotion on 2012-08-15
> **ksanger said:**
> I have no idea what desktop wall or desktop cube is.  I assume I have a wall.  I just installed the normal distro from a copy burned to cd. You assume correctly. The wall is default.

Unrelated/Unimportant background information:
The cube *used to be* the quintessential component of compiz, until Canonical got their hands on it and stripped it of all but the most mundane features.
The cube renders multiple desktops as sides of a three-dimensional shape, so you can have windows open on each side and rotate around to see them (or see them all at once if your cube is transparent, while being able to focus on the side in front of you).
The wall renders multiple desktops as one big flat surface, so you can have windows scattered all over it and slide around to see them; it is a generally inferior and less interesting design, but supposedly easier to understand and it gets lots of points from hardcore anti-eyecandy people.

>  Is it normal to have to reboot Ubuntu occasionally like Windows?That's a good question.

Theoretically no, since it is GNU/Linux and should never have to fully reboot unless you've updated the kernel. There are a lot of ways to get around having to reboot in GNU/Linux, which is one reason network administrators like it (reboots cost time, and therefore money). If you know the tricks you only have to reboot very rarely.

However, in practice, Ubuntu gets rebooted almost as much as windows. Partly this is because some windows refugees are trying to use Ubuntu just like they used windows, and partly because all the intricate tricks to avoid having to fully reboot are well... intricate, mostly involving terminal commands and fixing text configuration files using as the super-user which is risky if you make a mistake.

Here's an example:
One day your desktop just stops; freezes.
Maybe you can still move the mouse, maybe you can't.

Options:

1. Open another tty: ```
[ctrl]+[alt]+[f1~6]
```The screen will be black  except for some text asking you to login. This is the same username and  password you usually log in with. Note that you will not be able to see your password as you type it, not even as asterisks.

Once logged in, you can check if some process is using too much cpu with:```
top
``` *Q*uit top by pressing [q].

Terminate a misbehaving process with: ```
killall processname
```There are other, more intricate, ways to kill a process if *killall* doesn't work.

Return to your, hopefully unfrozen, desktop at tty7:```
[ctrl]+[alt]+[f7]
```2. That didn't work. Opening a tty worked, but the bad process won't die or the desktop wasn't there at tty7. 
Go back to another tty1~6. You will still be logged in at the one you used before.

You can restart the entire desktop session without having to reboot:```
sudo /etc/init.d/lightdm restart
```This will close all windows and take you back to the usual graphical login screen. You might lose some data if you hadn't saved before the freeze, but this should get you back on your feet faster than a reboot.

3. That didn't work; maybe none of the ttys will open. This is not good, but not necessarily the worst case scenario.
There are two last-ditch key combinations.

The key combination to restart X (the GUI) is disabled by default, but its:```
[ctrl]+[alt]+[backspace]
```This has some quirky results, but if you really don't want to reboot it may help.

The "magic keys" ```
[alt]+[SysRq]+[r],[e],[i],[s],[u],[b]
```Hold [alt]+[SysRq] and press each letter once, slowly, in sequence. This will reboot your system, but it's a soft reboot. The system should shutdown smoothly. This also gives applications a chance to write to disk before being killed, unmounts drives, etc. and is much less risky than hitting the switch.

4. That didn't work; maybe the kernel is locked up, and that's bad, and now you have to hit the switch.

5. Actually, there are probably a dozen other ways to get out of a frozen desktop without rebooting, but they are too intricate for me.

This post is completely off topic, but it looks like it's unlikely that I will ever see full-screen windows in Ubuntu with the Compiz Cube that aren't obstructed by the unity panel.

---

### Post by quequotion on 2012-08-15
> **firekage said:**
> As a matter of fact in my case this is true rather for using players like movie players because when i have full-screened firefox than it is under the panel but i can use panel while when i have full-screened movie players, and im watching something than panel is visible, not usuable, i can't click at anything on it.

This sentence is difficult to understand, but I think you mean:

"*As a matter of fact, in my case this is true rather for using players--like movie players--because when i have full-screened firefox then it is  under the panel, but i can still use the panel; while when i have full-screened  movie players and i'm watching something, then the panel is visible but not usable--i can't click at anything on it*."

How did you full-screen firefox? Did you press [F11]?

Sounds like you have the same issue as me on your upgraded installation.

I also had this issue after upgrading my previous computer to 12.04 and again after starting over on a new computer with a fresh install of 12.04.

I wonder why yours didn't develop the problem with a fresh install.

Are the compiz configurations of your two computers different at all?

Can you post them?

--how to do that:
1. In ccsm, click "Preferences"
2. On the "Profile & Backend" panel, under "Profile" there are some buttons.
3. Click "Export" and save the file somewhere.
I recommend** upgraded.txt **and **freshinstall.txt **for filenames.
4. Attach those txt files to a reply here

---

### Post by Ubun2to on 2012-08-16
> **quequotion said:**
> That's a good question.

Theoretically no, since it is GNU/Linux and should never have to fully reboot unless you've updated the kernel. There are a lot of ways to get around having to reboot in GNU/Linux, which is one reason network administrators like it (reboots cost time, and therefore money). If you know the tricks you only have to reboot very rarely.

However, in practice, Ubuntu gets rebooted almost as much as windows. Partly this is because some windows refugees are trying to use Ubuntu just like they used windows, and partly because all the intricate tricks to avoid having to fully reboot are well... intricate, mostly involving terminal commands and fixing text configuration files using as the super-user which is risky if you make a mistake.

I prefer to shut my network down every night, as I lost $300 worth of networking equipment due to a lightning strike, and I don't plan on losing it again. I was offline for about a week.

---

### Post by firekage on 2012-08-16
> **quequotion said:**
> This sentence is difficult to understand, but I think you mean:

"*As a matter of fact, in my case this is true rather for using players--like movie players--because when i have full-screened firefox then it is  under the panel, but i can still use the panel; while when i have full-screened  movie players and i'm watching something, then the panel is visible but not usable--i can't click at anything on it*."


Yes, that's right. I was in hurry and didn't see that it was hard to read and understand. Sorry.


> How did you full-screen firefox? Did you press [F11]?

I did it again and you're right. As soon as i full-screened firefox by F11 than Unity panel is not usuable, not clickable but visible. So, in other words, it happens with all apps on full-screen.

> Sounds like you have the same issue as me on your upgraded installation.

Yes, but only on one machine.

> I also had this issue after upgrading my previous computer to 12.04 and again after starting over on a new computer with a fresh install of 12.04.

I wonder why yours didn't develop the problem with a fresh install.

There is only one difference:

-11.10>12.04 uses gdm
-12.04 on fresh install uses lightdm

> Are the compiz configurations of your two computers different at all?


I will check it again.

> 
Can you post them?

--how to do that:
1. In ccsm, click "Preferences"
2. On the "Profile & Backend" panel, under "Profile" there are some buttons.
3. Click "Export" and save the file somewhere.
I recommend** upgraded.txt **and **freshinstall.txt **for filenames.
4. Attach those txt files to a reply here

I will do this but in my case with exporting and importing profiles in ccsm happens something bad - while i click on import than everything freezez, ican move window but it looks like Ubuntu/Unity/gui doesen't respond and i have to kill X. With importing the same thing happens.

---

### Post by quequotion on 2012-08-18
Good news / Bad news

Good news:
I tracked down the cause on my computer.
Whenver I have the cube enabled and transparent, Unity will be stuck on top of everything.
If the cube is set to 100% opacity, things work as expected.

Bad news:
This may only work for me, as it seems several different configurations of compiz bring out the error. Also, I don't want to go without a transparent cube.

Good news:
The developers recognize and continue to work on the problem.
I've been talking to people on IRC who were very supportive.

Bad news:
It looks like we're down to edge cases with unspecified causes, which are rather difficult bugs to fix.

---

### Post by quequotion on 2012-08-18
> **firekage said:**
> I will do this but in my case with exporting and importing profiles in ccsm happens something bad - while i click on import than everything freezez, ican move window but it looks like Ubuntu/Unity/gui doesen't respond and i have to kill X. With importing the same thing happens.

That's strange. You shouldn't have to click "import" for anything, just "export".
It shouldn't damage your configuration, but then compiz and ccsm are a little unpredictable.

---

### Post by firekage on 2012-08-22
> **quequotion said:**
> 
Are the compiz configurations of your two computers different at all?


I checked it again. Few words at the end of quotation.

> 
Can you post them?

--how to do that:
1. In ccsm, click "Preferences"
2. On the "Profile & Backend" panel, under "Profile" there are some buttons.
3. Click "Export" and save the file somewhere.
I recommend** upgraded.txt **and **freshinstall.txt **for filenames.
4. Attach those txt files to a reply here

I did it but because of what i have to say at the end of this quotations there is no need for it.


> **quequotion said:**
> Good news / Bad news

Good news:
I tracked down the cause on my computer.
Whenver I have the cube enabled and transparent, Unity will be stuck on top of everything.
If the cube is set to 100% opacity, things work as expected.

Bad news:
This may only work for me, as it seems several different configurations of compiz bring out the error. Also, I don't want to go without a transparent cube.

Good news:
The developers recognize and continue to work on the problem.
I've been talking to people on IRC who were very supportive.

Bad news:
It looks like we're down to edge cases with unspecified causes, which are rather difficult bugs to fix.

I have to agree with you in 100%. I checked it again and what you said is true for me too. If i set cube to 100% opacity then panel at the top disappears when apps are fullscreened, but if i have, for an example, 95% opacity than panel at the bottom is still present when apps are fullscreened.

I was wrong earlier, had time and checked it - you're right. It is true for ma also on 12.04 fresh installation, and with upgrades too.

---

### Post by ray field on 2012-09-02
> **quequotion said:**
> Good news / Bad news

Good news:
I tracked down the cause on my computer.
Whenver I have the cube enabled and transparent, Unity will be stuck on top of everything.
If the cube is set to 100% opacity, things work as expected.

Bad news:
This may only work for me, as it seems several different configurations of compiz bring out the error. Also, I don't want to go without a transparent cube.

Good news:
The developers recognize and continue to work on the problem.
I've been talking to people on IRC who were very supportive.

Bad news:
It looks like we're down to edge cases with unspecified causes, which are rather difficult bugs to fix.

thankful I came across this thread -- turning off the cube transparency fixed the panel showing up fullscreen (for me it was most annoying in dosemu, and playing video). as a side benefit, compiz seems to use much less CPU.

is there a sense this only affects systems with Nvidia cards?

is compiz the way of the future? since I'm just an enduser I am just grateful for what I get -- compiz gives me a lot, but the persistence of bugs like this one and the "flashing previous desktop" one just make me wonder if there is uncertainty about whether to just ditch compiz in favor of something else.

---

### Post by firekage on 2012-09-02
In my opinion, in fact, whatever you choose, it won't be without issues, problems, bugs.  I have KDE on Slackware - had many problems with it...

---

### Post by quequotion on 2012-09-05
> **firekage said:**
> I have to agree with you in 100%. I checked it again and what you said is true for me too. If i set cube to 100% opacity then panel at the top disappears when apps are fullscreened, but if i have, for an example, 95% opacity than panel at the bottom is still present when apps are fullscreened.> **ray field said:**
> thankful I came across this thread -- turning off the cube transparency fixed the panel showing up fullscreen Three people with the same problem and the same workaround?
That has to be the most consistency since the beginning of this thread.

> is there a sense this only affects systems with Nvidia cards? Good question. I don't think so, but I'm no expert.
The bug reports so far haven't connected to a certain driver or card; one developer explicitly said the rendering problem is not relevant to the driver.
However, one can never be completely certain when faced with unpredictable behavior.

Properly answering your question requires (at least) the following tests:
Run compiz with the nvidia card and the nouveau drivers.
Run compiz with the nvidia card and the proprietary drivers.
Run compiz with a different GPU in the same machine.

Developers and users alike tend to distrust the proprietary drivers, but I find seven out of ten times this is based on hearsay, two out of ten on misconfiguration, and one out of ten on an actual bug (which Nvidia will eventually get around to fixing).
In this case I doubt it's connected with the card or the drivers since it hadn't come up yet and the issue seems tied to compiz's configuration.

> is compiz the way of the future? since I'm just an enduser I am just grateful for what I get -- compiz gives me a lot, but the persistence of bugs like this one and the "flashing previous desktop" one just make me wonder if there is uncertainty about whether to just ditch compiz in favor of something else.The "flashing previous desktop" bug really has been fixed, although that fix is not officially available for Precise.
One of the developers set up a temporary PPA for Precise [here]("https://launchpad.net/%7Evanvugt/+archive/compiz-preproposed"),  but this version of compiz, 0.9.7.8-0ubuntu1, is "out of date"  (0.9.7.8-0ubuntu1.4 is current for Precise), so installing requires an override.
The fix is not included in newer versions of compiz until  0.9.8 (available for Quantal).
Someday, there will be an SRU for Precise that will include this fix and others...
In the mean time, I have installed compiz from Quantal on my system.

I certainly hope that compiz is the future, because it has a lot of potential, but I'm very worried about the direction it's taking since Canonical has (in effect) taken over.
"The plan" as it were, is that future versions of Ubuntu will use Wayland and Compiz for rendering and composting, for which purpose all X11 dependencies of Compiz will be bound to a separate plugin for use on other, non-wayland, platforms. Wayland's official inclusion in Ubuntu continues to be postponed.
  
During the compiz 0.8.x era, there were some innovative plugins like headtracking, affine, stackswitch, window rotation, compiz screensaver, etc... all of which are pretty much forgotten now. Those and more are still available from the mostly abandoned git repository (development is entirely in launchpad bzr now), but it's not likely that they are compatible with recent compiz. 
Compiz 0.9.x is much lighter and more stable, but the Unity integration clashes with other desktops, the default configuration is rather unimpressive, and it lacks support for all the extras that made compiz "cool". In addition, since the compiz development community has all but shut  down (wiki, website, and forums are all ghost towns now) several other  platforms have (falsely) declared it dead and dropped it from their  distributions.
In my opinion, compiz, and the community that make it awesome, deserve better.

---

### Post by bogan on 2012-09-06
Hi!, **quequotion**,  Congratulations! 

You will shortly make your century.

When you started this thread, you and I seemed to be the only ones who had this problem, and you had difficulty in finding anyone who would even recognize what you were talking about.

You don't seem to have **that** problem any longer, even if the original one still gives trouble. 

 Chao!, **bogan**.

---

### Post by quequotion on 2012-09-07
> **bogan said:**
> When you started this thread, you and I seemed to be the only ones who had this problem, and you had difficulty in finding anyone who would even recognize what you were talking about. It seems like much longer ago than it actually was. Much progress has been made since we properly defined the issue. Thank you for your help and support.

Now that we've established some consistent behavior, I feel there's a stronger possibility that this bug will be fixed.

---

### Post by firekage on 2012-09-08
> **quequotion said:**
> 
The "flashing previous desktop" bug really has been fixed, although that fix is not officially available for Precise.
One of the developers set up a temporary PPA for Precise [here]("https://launchpad.net/%7Evanvugt/+archive/compiz-preproposed"),  but this version of compiz, 0.9.7.8-0ubuntu1, is "out of date"  (0.9.7.8-0ubuntu1.4 is current for Precise), so installing requires an override.
The fix is not included in newer versions of compiz until  0.9.8 (available for Quantal).
Someday, there will be an SRU for Precise that will include this fix and others...
In the mean time, **I have installed compiz from Quantal on my system.**


Could you explain, in detail, how to install it by overriding it?

---

### Post by ray field on 2012-09-08
> **firekage said:**
> Could you explain, in detail, how to install it by overriding it?

this thread covers the bug & the stopgap fix:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430)

post #149 is I think how I implemented it.

however, several weeks after I installed the fix, one of my Compiz upgrades snuck through, apparently, and wrecked my Compiz configuration. it may have been my error, except I don't remember doing anything wrong or risky. 

as a result, I am one of those (impatiently) waiting for the resolution of the bug -- I guess somewhere in the launchpad thread there's a good explanation of why the fix has landed in Quantal but not Precise, but I don't understand that, either.

---

### Post by Mycen on 2012-09-09
> **quequotion said:**
> Good news / Bad news

Good news:
I tracked down the cause on my computer.
Whenver I have the cube enabled and transparent, Unity will be stuck on top of everything.
If the cube is set to 100% opacity, things work as expected.

Bad news:
This may only work for me, as it seems several different configurations of compiz bring out the error. Also, I don't want to go without a transparent cube.

Good news:
The developers recognize and continue to work on the problem.
I've been talking to people on IRC who were very supportive.

Bad news:
It looks like we're down to edge cases with unspecified causes, which are rather difficult bugs to fix.

Heyhey, Thanks for noting this, I had just been fudding around with my compiz settings in 12.04 to get the coolest desktop experience ever, and fullscreen apps started behaving as you described. The transparency during rotation was fine, but opacity when not rotating had to be 100. Too bad, I liked seeing my other desktops...

---

### Post by quequotion on 2012-09-09
> **Mycen said:**
> Heyhey, Thanks for noting this, I had just been fudding around with my compiz settings in 12.04 to get the coolest desktop experience ever, and fullscreen apps started behaving as you described. The transparency during rotation was fine, but opacity when not rotating had to be 100. Too bad, I liked seeing my other desktops... Could you join [this bug report ]("https://bugs.launchpad.net/unity/+bug/1025535")as well? If we can get the number of people affected up higher, the report might get more attention and urgency.

If anyone else comes across the same problem, leave a comment here and join the bug report also. Comment on the bug report if you have some more information.

If you don't have a launchpad account, you'll need to make one (or maybe you can use your forum login?), log in, and then click, in the report, on the yellow (!) next to "This bug affects # people. Does this bug affect you?" then click "(O) Yes, it affects me."

---

### Post by quequotion on 2012-09-09
> **firekage said:**
> Could you explain, in detail, how to install it by overriding it?It's not something I'd recommend, particularly if you ever have to go back to the default version since downgrading is much more difficult.

If you want to try, you'll either need to add Quantal's repositories or download the packages manually. I went with manually because I don't want to install other stuff from Quantal yet.

The list of packages to download is pretty long, particularly a few obscure dependencies will come up.

I've individually downloaded and installed the following packages:```
bamfdaemon_0.3.0-0ubuntu1_amd64.deb
compiz_0.9.8.0-0ubuntu1_all.deb
compizconfig-backend-gconf_0.9.8.0-0ubuntu1_all.deb
compizconfig-settings-manager_0.9.8.0-0ubuntu1_all.deb
compiz-core_0.9.8.0-0ubuntu1_amd64.deb
compiz-gnome_0.9.8.0-0ubuntu1_amd64.deb
compiz-plugins_0.9.8.0-0ubuntu1_amd64.deb
compiz-plugins-default_0.9.8.0-0ubuntu1_amd64.deb
compiz-plugins-extra_0.9.8.0-0ubuntu1_all.deb
compiz-plugins-main_0.9.8.0-0ubuntu1_all.deb
compiz-plugins-main-default_0.9.8.0-0ubuntu1_all.deb
libbamf0_0.3.0-0ubuntu1_amd64.deb
libbamf3-0_0.3.0-0ubuntu1_amd64.deb
libcompizconfig0_0.9.8.0-0ubuntu1_amd64.deb
libdecoration0_0.9.8.0-0ubuntu1_amd64.deb
libglew1.8_1.8.0-1ubuntu2_amd64.deb
libglewmx1.8_1.8.0-1ubuntu2_amd64.deb
libmetacity-private0a_2.34.5-0ubuntu1_amd64.deb
libnux-3.0-0_3.4.0-0ubuntu3_amd64.deb
libnux-3.0-common_3.4.0-0ubuntu3_all.deb
libpci3_3.1.9-5ubuntu2_amd64.deb
libunity-core-6.0-5_6.4.0-0ubuntu4_amd64.deb
libunity-protocol-private0_5.96.0-0ubuntu1_amd64.deb
libunity-webapps0_2.0.1-0ubuntu1_amd64.deb
metacity_2.34.5-0ubuntu1_amd64.deb
metacity-common_2.34.5-0ubuntu1_all.deb
nux-tools_3.4.0-0ubuntu3_amd64.deb
pciutils_3.1.9-5ubuntu2_amd64.deb
python-compizconfig_0.9.8.0-0ubuntu1_amd64.deb
sgml-base_1.26+nmu3ubuntu1_all.deb
unity-2d_6.4.0-0ubuntu4_all.deb
unity_6.4.0-0ubuntu4_amd64.deb
unity-autopilot_6.4.0-0ubuntu4_all.deb
unity-common_6.4.0-0ubuntu4_all.deb
unity-lens-applications_6.4.0-0ubuntu1_amd64.deb
unity-lens-files_6.4.0-0ubuntu2_amd64.deb
unity-lens-music_6.6.0-0ubuntu1_amd64.deb
unity-lens-video_0.3.9-0ubuntu1_all.deb
unity-services_6.4.0-0ubuntu4_amd64.deb
unity-webapps-service_2.0.1-0ubuntu1_amd64.deb
```Also important to note, the latest version of compiz in Quantal has been severly lobotomized to preserve interoperability with in GLES for ARM. It will probably be back in shape soon enough, but the current version looks a little WIP.

---

### Post by Mycen on 2012-09-10
> **quequotion said:**
> Could you join [this bug report ]("https://bugs.launchpad.net/unity/+bug/1025535")as well? If we can get the number of people affected up higher, the report might get more attention and urgency.


Done! :D

---

### Post by dondamyani on 2012-09-15
> **quequotion said:**
> Could you join [this bug report ]("https://bugs.launchpad.net/unity/+bug/1025535")as well? If we can get the number of people affected up higher, the report might get more attention and urgency.

If anyone else comes across the same problem, leave a comment here and join the bug report also. Comment on the bug report if you have some more information.


Done!

---

### Post by quequotion on 2012-09-25
About two weeks ago Unity 5.16.0 was released to fix this issue.

Unfortunately it does not fix [bug 1025535]("https://bugs.launchpad.net/unity/+bug/1025535"), where unity appears on top of everything when the cube is enabled and transparent.

This bug also continues to affect Unity 6.6.0 in Quantal.
[]("https://bugs.launchpad.net/unity/+bug/1025535")

---

### Post by ray field on 2012-09-26
I hope it's not me or my hardware, but the last week or so, Compiz has become extremely unstable. Within 3-10 hours of a reboot, almost inevitably I'll come up against:

1) a frozen desktop, or one that is completely corrupted;
2) a desktop that will refuse to return from the screensaver, requiring a hard reboot, which is always fun;
3) a "broken cube," as it were -- a desktop which refuses to spin to reveal any other desktops. In the past, when Compiz crashed in this fashion, it was considerate enough to arrange all open windows from other desktops on the remaining one, but the most recent version of Compiz do not do this.

I understand this isn't the best place to post this -- however 1) when I look at the lengthy list of Compiz bugs on Launchpad, I don't really see anything germane because 2) I don't really know where to look to find.  In fact, [the few] times when the crash reporter pops up to ask me if I'd like to report the bug, it asks me something impenetrable or irrelevant. 

So -- I guess one reason I'm posting here is I don't find another Compiz thread, and the discussion here has been intelligent and well-informed. 

1) Where should I look to find the bug to report?
2) Is there any particular feature I should try disabling to stabilize things?
3) As I mentioned earlier, I had trouble with the the older version of Compiz, so am unwilling to use the back version. I really have grown quite fond of Unity, but while an occasional crash is acceptable, inevitable ones really aren't. Should I just go to Gnome 3?

---

### Post by ray field on 2012-09-30
> **ray field said:**
> I hope it's not me or my hardware, but the last week or so, Compiz has become extremely unstable. 

just for the archives: I seem to have maybe resolved this by installing nvidia-current (I had 239.something I think). I actually would have been happy to go with Nouveau -- I don't do much hardcore gaming, which I assume is the most compelling reason to use the proprietary driver -- except the fullscreen dosemu was terrible.

---

### Post by Ubun2to on 2012-10-01
> **ray field said:**
> I hope it's not me or my hardware, but the last week or so, Compiz has become extremely unstable. Within 3-10 hours of a reboot, almost inevitably I'll come up against:

1) a frozen desktop, or one that is completely corrupted;
2) a desktop that will refuse to return from the screensaver, requiring a hard reboot, which is always fun;
3) a "broken cube," as it were -- a desktop which refuses to spin to reveal any other desktops. In the past, when Compiz crashed in this fashion, it was considerate enough to arrange all open windows from other desktops on the remaining one, but the most recent version of Compiz do not do this.

I understand this isn't the best place to post this -- however 1) when I look at the lengthy list of Compiz bugs on Launchpad, I don't really see anything germane because 2) I don't really know where to look to find.  In fact, [the few] times when the crash reporter pops up to ask me if I'd like to report the bug, it asks me something impenetrable or irrelevant. 

So -- I guess one reason I'm posting here is I don't find another Compiz thread, and the discussion here has been intelligent and well-informed. 

1) Where should I look to find the bug to report?
2) Is there any particular feature I should try disabling to stabilize things?
3) As I mentioned earlier, I had trouble with the the older version of Compiz, so am unwilling to use the back version. I really have grown quite fond of Unity, but while an occasional crash is acceptable, inevitable ones really aren't. Should I just go to Gnome 3?

According to isantop in [this thread]("http://ubuntuforums.org/showthread.php?t=2061578"), using things such as the Compiz Cube will make Unity mess up due to it not being made to use it.

---

### Post by firekage on 2012-10-01
> **Ubun2to said:**
> According to isantop in [this thread]("http://ubuntuforums.org/showthread.php?t=2061578"), using things such as the Compiz Cube will make Unity mess up due to it not being made to use it.

I have no problems using compiz with cube and desktop effect - only the one from this topic.

---

### Post by quequotion on 2012-10-09
> **ray field said:**
> 1) a frozen desktop, or one that is completely corrupted;
2) a desktop that will refuse to return from the screensaver, requiring a hard reboot, which is always fun;
3) a "broken cube," as it were -- a desktop which refuses to spin to reveal any other desktops. In the past, when Compiz crashed in this fashion, it was considerate enough to arrange all open windows from other desktops on the remaining one, but the most recent version of Compiz do not do this. Take a look back, on page 9, at [this post]("http://ubuntuforums.org/showpost.php?p=12174438&postcount=89") for some tips on getting out of a frozen or broken desktop. > 1) Where should I look to find the bug to report?
2) Is there any particular feature I should try disabling to stabilize things?
3) As I mentioned earlier, I had trouble with the the older version of Compiz, so am unwilling to use the back version. I really have grown quite fond of Unity, but while an occasional crash is acceptable, inevitable ones really aren't. Should I just go to Gnome 3?Are you using the latest compiz from Quantal?
I backed off a few versions after seeing the mess it's in right now. A whole new development phase has begun, porting compiz to OpenGL|ES for ARM devices. Some of the features are neat and it's super light on resources, but lots of plugins were lobotomized and some of the new features are creating indescribably buggy behavior.

1. I spend a lot of time on google. Think of seven different ways to say what you think is wrong and search them all; think of ways to make your searches more effective; you might find a report--if not make a new report. If you are using a bleeding-edge version however, it is likely that the issue has not been reported--not to say it is unknown. You might be able to talk to developers via IRC, on freednode at #compiz-dev or #ubuntu-unity, keeping in mind that they are busy coders and volunteers with mysterious schedules.

2. If you are using the new compiz, of particular importance are the new options in OpenGL: "**Framebuffer Object**", "**Vertex Buffer Object**" and " **Always use Buffer Swapping**". Dependingon your graphics card and drivers these can either really hurt or really help you (they are alll intended to improve performance, but are not yet stable or complete). I found "*Vertex Buffer Object*" is causing some strangeness, like a hall-of-mirrors effect and other times a shattered cube effect, but is also necessary for some other things.

3. Essentially, we are all using Gnome 3, or GTK3 with most of the Gnome Suite in Ubuntu. The only thing you are "missing out" on is the Gnome-Shell desktop. It isn't compatible with compiz, doesn't vertically sync, and is even more touch-panel oriented than Unity... The Mint Linux "Cinnamon" desktop looks promising if you want to go "back to basics" and I'm putting some thought into it myself.

I appreciate your enthusiasm. Particularly because I've also run into so many other problems in relation to this one, I'm happy to help. There is a subforum for the discussion of Desktop Environments you  might want to look through.

After an *interesting* week with the new GL|ES compiz, I backed down to 0.9.8+bzr3319-0ubuntu1, which was the best release of compiz since unity came out. This version doesn't have some of the new performance enhancements, but all bugs affecting me except for this thread's topic are fixed, the "extra" plugins are rolled in, and it even comes with "stackswitch"--my favorite "[Alt]+[[Tab]" alternative.

> **Ubun2to said:**
> According to isantop in [this thread]("http://ubuntuforums.org/showthread.php?t=2061578"), using things such as the Compiz Cube will make Unity mess up due to it not being made to use it.Making Unity a compiz plugin that is incompatible with the cube would be a fallacy of unimaginable magnitude.... *which actually happened* but the design was revised after a flood of negative press threatened to kill unity in its crib. Unity* should be *fully compatible with the cube at this point, and I can't seem to find any issues other than the subject of this thread.
**--------------------------------------------------------------------------------------------**

Back on topic:
Now that [s][bug 734908]("https://bugs.launchpad.net/bugs/734908")[/s] is fixed, [bug 1025535]("https://bugs.launchpad.net/unity/+bug/1025535") needs to get more attention. The development team is still keeping track, but the bug has low priority and no one is assigned to getting it fixed yet. If you have any input please log in to launchpad and contribute!

---

### Post by Ubun2to on 2012-10-09
> **quequotion said:**
> Making Unity a compiz plugin that is incompatible with the cube would be a fallacy of unimaginable magnitude.... *which actually happened* but the design was revised after a flood of negative press threatened to kill unity in its crib. Unity* should be *fully compatible with the cube at this point, and I can't seem to find any issues other than the subject of this thread.

I personally stay away from any extra Compiz plugins because of these sorts of issues. The current workspace switcher is just fine for me, after I made some adjustments to the keyboard shortcuts for easier access.

---

### Post by quequotion on 2012-10-09
> **Ubun2to said:**
> I personally stay away from any extra Compiz plugins because of these sorts of issues. The current workspace switcher is just fine for me, after I made some adjustments to the keyboard shortcuts for easier access.This is a reasonable point of view. Things are a little different for me because I have been using compiz since long before the Canonical takeover and unity, so I see the cube as the quintessential component of the compiz desktop. I understand that it was a better choice than Gnome-Shell's mutter-based desktop at the time, but it doesn't make sense to me that Canonical chose compiz to develop a 2D desktop environment and it probably never will.

In fact, I see *unity* as the obtrusive, unstable plugin that is not really compatible with compiz.

---

### Post by quequotion on 2012-10-10
I thought I'd give an example to illustrate why this issue matters to me.

I've gotten used to a certain work flow using a fully transparent cube.

I'm attaching a screenshot,  scaled down from 1680x1050 to 1024x640, which shows the basics:

On the *front* and *back* sides are reports for work; on the *left* is my work schedule in the bottom half and my salary form on the top half; on the *right* is a home video. For aesthetics, the background is a 360° equirectangular panorama.  Most important here is that *everything is visible*, but *nothing is obstructed*.

To keep organized, I usually have only one or two windows on each desktop. In this example, the left side has two windows that are arranged using the compiz "grid" plugin, the front and back have single, unaligned windows, which I might maximize later, and the right has a full-screen video. Since the cube is completely transparent, I can always see all of these things at the same time, which makes it very easy to switch back and forth between tasks.In case I lose track, *I don't have to preview all the desktops and then select the one I want or wander from desktop to desktop or even [alt]+[tab] to the window I want,* I just take a look around and rotate to it. Since each side is displayed at a different angle  and distance, nothing gets in the way of anything else visually. With the "brightness, opacity, and saturation" plugin, I can add transparency to windows case-by-case in order to watch the video while I work and roughly see the content of all windows on all desktops. Sometimes I'm just watching movies or TV, but I might also be transcribing the dialogue from a certain scene. When I'm really busy I usually forgo the TV and have a dozen windows, organized by task, across each side.

This works for me, keeps me alert and productive, and generally produces good results on time. I use the same work flow for all sorts of things ie:
Designing graphics while searching for stock photography or clipart and writing a plan for how to use them at work, reading logs and editing configuration files while reporting a bug on launchpad, playing a game while reading a walkthrough and watching a video of a tricky part, etc etc. I used the same work flow to write this post while editing the screenshot to blackout and blur sensitive information--all the while still watching the home video of a festival I participated in some years ago.

Whenever I need a break, I switch to the full-screen video, and I am mildly irritated that Unity is getting in the way of enjoying this--not to mention that it also appears over the screensaver and reveals the title of whatever window I was last using.

---

### Post by Ubun2to on 2012-10-10
> **quequotion said:**
> I thought I'd give an example to illustrate why this issue matters to me.

I've gotten used to a certain work flow using a fully transparent cube.

I'm attaching a screenshot,  scaled down from 1680x1050 to 1024x640, which shows the basics:

On the *front* and *back* sides are reports for work; on the *left* is my work schedule in the bottom half and my salary form on the top half; on the *right* is a home video. For aesthetics, the background is a 360° equirectangular panorama.  Most important here is that *everything is visible*, but *nothing is obstructed*.

To keep organized, I usually have only one or two windows on each desktop. In this example, the left side has two windows that are arranged using the compiz "grid" plugin, the front and back have single, unaligned windows, which I might maximize later, and the right has a full-screen video. Since the cube is completely transparent, I can always see all of these things at the same time, which makes it very easy to switch back and forth between tasks.In case I lose track, *I don't have to preview all the desktops and then select the one I want or wander from desktop to desktop or even [alt]+[tab] to the window I want,* I just take a look around and rotate to it. Since each side is displayed at a different angle  and distance, nothing gets in the way of anything else visually. With the "brightness, opacity, and saturation" plugin, I can add transparency to windows case-by-case in order to watch the video while I work and roughly see the content of all windows on all desktops. Sometimes I'm just watching movies or TV, but I might also be transcribing the dialogue from a certain scene. When I'm really busy I usually forgo the TV and have a dozen windows, organized by task, across each side.

This works for me, keeps me alert and productive, and generally produces good results on time. I use the same work flow for all sorts of things ie:
Designing graphics while searching for stock photography or clipart and writing a plan for how to use them at work, reading logs and editing configuration files while reporting a bug on launchpad, playing a game while reading a walkthrough and watching a video of a tricky part, etc etc. I used the same work flow to write this post while editing the screenshot to blackout and blur sensitive information--all the while still watching the home video of a festival I participated in some years ago.

Whenever I need a break, I switch to the full-screen video, and I am mildly irritated that Unity is getting in the way of enjoying this--not to mention that it also appears over the screensaver and reveals the title of whatever window I was last using.

I have no idea how you can juggle all of this. My brain is made for single tasking. When I multitask, I usually end up messing up on my typing.
This is what usually happens when I'm listening to some live streaming music (which is what I like to do-something new nearly every time) when I am typing a document:
> After considering what you want in your new custom-built machine, you should *throw my hands up in the air sometimes*, and also consider getting the nVidia GTX 660 so you can don't have to worry about upgrading it any time in the near future.
It can lead to some very awkward situations when people read what I type by accident. My train of thought is also easily brute-forced by trivial matters such as billboards on the side of the highway.
> I wonder how much longer this traffic will eat at McDonalds-wait wut?

---

### Post by quequotion on 2012-10-11
> **Ubun2to said:**
> I have no idea how you can juggle all of this. My brain is made for single tasking. When I multitask, I usually end up messing up on my typing.
This is what usually happens when I'm listening to some live streaming music (which is what I like to do-something new nearly every time) when I am typing a document:> After considering what you want in your new custom-built machine, you should *throw my hands up in the air sometimes*, and also consider getting the nVidia GTX 660 so you can don't have to worry about upgrading it any time in the near future.It can lead to some very awkward situations when people read what I type by accident. My train of thought is also easily brute-forced by trivial matters such as billboards on the side of the highway.[QUOTE]I wonder how much longer this traffic will eat at McDonalds-wait wut?[/QUOTE]Haha I see how that could be troublesome.

---

### Post by Sentello on 2013-03-14
Ubuntu 12.10 with program Dreamstream e2

[[IMG]http://s23.postimage.org/vuyhhm1gn/Screenshot_from_2013_03_14_18_29_44.jpg[/IMG]]("http://postimage.org/image/vuyhhm1gn/")

---

