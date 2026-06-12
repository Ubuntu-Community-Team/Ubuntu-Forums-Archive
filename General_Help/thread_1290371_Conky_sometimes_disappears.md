---
title: "Conky sometimes disappears"
date: 2009-10-13
forum: General Help
---

### Post by DeMus on 2009-10-13
I have a, if you don't mind me saying so myself, nice conky on my desktop. Sometimes, when I close a program, or just click on the button on the extremely left side of the bottom panel to bring the desktop upfront, the conky info is gone.
When I then open System monitor, I still see conky running. I can not end it, I have to kill it to get rid of it.
Then, when I re-start conky, the info returns.
It's not caused by running one program, it happens randomly.

What could be the reason for the conky to disappear from the screen?

I use:
Jaunty 9.04 64 bits, completely updated
Kernel 2.6.30
nVidia driver 190.36
AWN*

I have not:
Compiz

*: should AWN be running btw?

---

### Post by DeMus on 2009-10-14
Nobody? Am I the only one experiencing these problems?
Am I that unique?
Hard to believe.

Come on please, give me some clues where to look, what to do.

---

### Post by stinkeye on 2009-10-14
> **DeMus said:**
> Nobody? Am I the only one experiencing these problems?
Am I that unique?
Hard to believe.

Come on please, give me some clues where to look, what to do.
Posting on this thread with your conky config will get you a response.
[_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=983") BEWARE THIS THREAD IS ADDICTIVE.

It may be as simple as *own_window_type*.

Try substituting this in your conky config above "TEXT"```
own_window yes
own_window_type normal
own_window_transparent YES
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

From man conky
```
own_window_type
              if own_window is yes, you may specify type normal, desktop,  dock,  panel
              or  override (default: normal).  Desktop windows are special windows that
              have no window decorations; are always visible on your  desktop;  do  not
              appear  in  your  pager or taskbar; and are sticky across all workspaces.
              Panel windows reserve space along a desktop edge, just  like  panels  and
              taskbars, preventing maximized windows from overlapping them. The edge is
              chosen based on the alignment option. Override windows are not under  the
              control of the window manager. Hints are ignored. This type of window can
              be useful for certain situations.
```
Panel and dock may only be available from version 1.7.1 up.
Conky version.
```
conky -v
```

---

### Post by DeMus on 2009-10-14
Thanks for your answer and explanation.
I changed the line own_window_type from override to normal, but this doesn't help at all. The moment I click the Show desktop button in the lower panel my conky is gone.
I have version 1.6 btw. It is in the repos. Where can I get the latest version?

---

### Post by stinkeye on 2009-10-14
> **DeMus said:**
> Thanks for your answer and explanation.
I changed the line own_window_type from override to normal, but this doesn't help at all. The moment I click the Show desktop button in the lower panel my conky is gone.
I have version 1.6 btw. It is in the repos. Where can I get the latest version?
If you use ```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
in your code as well it shouldn't be minimized when you show the desktop.
The "skip taskbar" option should make it be overlooked by the show desktop command.
If you have the 4 setings I posted earlier in your config file everything should work fine.
Just make sure there isn't another occurrence of those settings in your config, thus changing the options.

There is a .deb file available here:[_[COLOR="DarkRed"]conky .deb 1.7.2[/COLOR]_]("https://launchpad.net/~norsetto/+archive/ppa/+packages")
For conky with all enabled features grab the conky-all package.
There is nothing wrong with the version you are using though.
They have just added more features such as the ability for conky to draw images and a few minor bug fixes.

---

### Post by stinkeye on 2009-10-15
You may also just need to delay the starting of conky to allow the window manager time to load.
See this thread [[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=867076[/COLOR]]("http://ubuntuforums.org/showthread.php?t=867076") in STEP 2 - Setting up conky to autostart on boot.

---

### Post by DeMus on 2009-10-15
> **stinkeye said:**
> If you use ```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
in your code as well it shouldn't be minimized when you show the desktop.
The "skip taskbar" option should make it be overlooked by the show desktop command.
If you have the 4 setings I posted earlier in your config file everything should work fine.
Just make sure there isn't another occurrence of those settings in your config, thus changing the options.

There is a .deb file available here:[_[COLOR="DarkRed"]conky .deb 1.7.2[/COLOR]_]("https://launchpad.net/~norsetto/+archive/ppa/+packages")
For conky with all enabled features grab the conky-all package.
There is nothing wrong with the version you are using though.
They have just added more features such as the ability for conky to draw images and a few minor bug fixes.

Well, I have the text as you wrote (the 4 settings) but still when I come back to my desktop the conky sometimes has disappeared. 
I do have the start-up delay and that is working fine, conky starts when the desktop has completed, no problem there. It's just when I minimize other windows and return to my desktop it sometimes is gone.

---

### Post by MaxIBoy on 2009-10-15
Do you have either

[LIST]
[*]Metacity compisite effects, or
[*]Kwin composite effects?
[/LIST]
If so, try disabling them and see if that fixes your problem. (And fer chrissake clean up your desktop, it ruins the otherwise beautiful theme.)

---

### Post by DeMus on 2009-10-15
> **MaxIBoy said:**
> Do you have either

[LIST]
[*]Metacity compisite effects, or
[*]Kwin composite effects?
[/LIST]
If so, try disabling them and see if that fixes your problem. (And fer chrissake clean up your desktop, it ruins the otherwise beautiful theme.)

I do have both AWN and metacity running. I stopped the metacity process and after that the AWN. Bad idea. Now the computer came to a halt. Nothing in the foreground worked anymore, processes in the background still ran. I couldn't click anything anymore and had to hard-reboot.
Do I need AWN, do I need metacity, do I need both? What do they do exactly?

---

### Post by stinkeye on 2009-10-15
You need metacity (default window manager for ubuntu) running unless you have another window manager installed
ie compiz 
I just did a bit of experimenting with metacity on my computer, and I need to set```
own_window_type override
```
for conky not to be minimized when I show the desktop.
So it seems metacity doesn't use
own_window_hints
the same way as compiz does.

---

### Post by DeMus on 2009-10-15
> **stinkeye said:**
> You need metacity (default window manager for ubuntu) running unless you have another window manager installed
ie compiz 
I just did a bit of experimenting with metacity on my computer, and I need to set```
own_window_type override
```
for conky not to be minimized when I show the desktop.
So it seems metacity doesn't use
own_window_hints
the same way as compiz does.

Well, whatever I do, whatever I write in the conkyrc file, it just doesn't help. Almost everytime I return to my desktop the conky is gone. I'll attach my file so maybe somebody can see if there is something "illegal" in there.

---

### Post by stinkeye on 2009-10-15
> **DeMus said:**
> Well, whatever I do, whatever I write in the conkyrc file, it just doesn't help. Almost everytime I return to my desktop the conky is gone. I'll attach my file so maybe somebody can see if there is something "illegal" in there.
[COLOR="DarkRed"]Edit[/COLOR]: Just checking -Do you restart conky after making changes to the config file.
I can run your conky on my computer using the metacity window manager 
and conky behaves normally.
What's confusing me is you said you were running AWN dock which requires a compositing window manager to run,
and by default the metacity compositing feature is not enabled.
Plus the fact that if I run your conky under metacity with compositing turned on
it draws shadows around the border which cant be turned off.
[ATTACH]132009[/ATTACH]
But in your screenshot there is no shadows to your conky.

To tell what window manager you are using install wmctrl
```
sudo apt-get install wmctrl
```
then open a terminal and type:
```
wmctrl -m
```
When I am running metacity I get this
```
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```
If you are running metacity to find out if the compositing feature is enabled open configuration editor
```
gconf-editor
```
and goto /apps/metacity/general
and look for compositing_manager.

---

### Post by DeMus on 2009-10-15
Stinkeye,
When running wmctrl -m I get the same answer as you did:

Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

In the gconf-editor the compositing manager is **_not_** enabled.
Should it be?

---

### Post by stinkeye on 2009-10-15
> **DeMus said:**
> Stinkeye,
When running wmctrl -m I get the same answer as you did:

Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

In the gconf-editor the compositing manager is **_not_** enabled.
Should it be?
It should be to run AWN but doesn't need to be for conky.
The things that differ on your system are
64bit,,,,,,,,,,,,,,,,,,,,,32bit
AWN .......................dont run
nVidia driver 190.36,,,,,,,nVidia driver 185.18 
So I'm all out of answers.
If it's really annoying you, maybe install compiz and fusion-icon 
which enables you to easily switch between window managers
[ATTACH]132015[/ATTACH]

---

### Post by DeMus on 2009-10-15
> **stinkeye said:**
> It should be to run AWN but doesn't need to be for conky.
The things that differ on your system are
64bit,,,,,,,,,,,,,,,,,,,,,32bit
AWN .......................dont run
nVidia driver 190.36,,,,,,,nVidia driver 185.18 
So I'm all out of answers.
If it's really annoying you, maybe install compiz and fusion-icon 
which enables you to easily switch between window managers
[ATTACH]132015[/ATTACH]

Well, I'm not fond of Compiz. It resembles too much like Vista with all the graphical "bullsh*t". I don't need a spinning desktop, or windows which faint away, or wobble when I move them. When I close a window it has to be closed: period. Not disappear in slow-motion.
I did set the compositing manager in gconf-editor and until now Conky did not disappear again. No, just checked, it's still there.
So maybe, we did find the answer.
Thanks for all your help. Really appreciate it.


Edit: it's 13 hours later now and still my conky did not disappear yet. I get more confident we did find the solution.
Thanks again, mate.

---

### Post by stinkeye on 2009-10-16
> **DeMus said:**
> Well, I'm not fond of Compiz. It resembles too much like Vista with all the graphical "bullsh*t". I don't need a spinning desktop, or windows which faint away, or wobble when I move them. When I close a window it has to be closed: period. Not disappear in slow-motion.
I did set the compositing manager in gconf-editor and until now Conky did not disappear again. No, just checked, it's still there.
So maybe, we did find the answer.
Thanks for all your help. Really appreciate it.


Edit: it's 13 hours later now and still my conky did not disappear yet. I get more confident we did find the solution.
Thanks again, mate.
No problem. Glad to help.
p.s. I love all the compiz whizbang fluff.

---

### Post by SpeedyGonsales on 2012-06-29
Old topic, but can't find better for sharing my solution for this problem:

I copied from somewhere my .conkyrc and with

> own_window_type override

after I clicked first time on desktop conky window vanished. Then I tried

> own_window_type desktop

but got same behaviour. What was irritating - after I edited .conkyrc and changed "desktop" for "override" or vice versa - conky would appear and stay. Until restart. As it would be kinda stupid to write script which would start some 3 minutes after desktop start which would just change desktop for override or vice versa I gave up for a while.

Then one day I tried > own_window_type normal

And it worked! (it needed hints for not showing on desktop pager etc), but problem is finally solved.
You have three possible parameters for own_window_type variable, you need to try all three and one will work, first you try with **normal**! It can save you a lot of time and frustration. :lolflag:

---

