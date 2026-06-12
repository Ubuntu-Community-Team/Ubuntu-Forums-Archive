---
title: "New windows appear behind existing ones using Unity"
date: 2012-01-18
forum: General Help
---

### Post by Joel Duckworth on 2012-01-18
Hi everyone, I did a bit of searching on this and couldn't turn anything up. Is it just me or when you open a new application from the Launcher in unity the new windows will appear behind the last active window on the desktop? Clicking the Launcher icon again brings it to the front, but really? When I launch an application I usually want it on top right away...:confused:

---

### Post by Paddy Landau on 2012-01-19
That's not right. What version of Ubuntu are you using? Do you single-click or double-click the launcher icon? My guess is that you've made some kind of change to Compiz that has this unintended effect.

---

### Post by bogan on 2012-01-19
> **Joel Duckworth said:**
> Hi everyone, I did a bit of searching on this and couldn't turn anything up. Is it just me or when you open a new application from the Launcher in unity the new windows will appear behind the last active window on the desktop? Clicking the Launcher icon again brings it to the front, but really? When I launch an application I usually want it on top right away...:confused:
Hi! **Joel**,
I have noticed this happening, especially when Firefox is running with a near full screen display, an I drag it to the right so the Launchers show, and I Single-Click on Home folder or gedit - I then get a 'Wobbly' Icon.

However I just tried it to check, and  it is not happening that way now. 
At the moment I am logged into 'Ubuntu' in 11.10, but usually I log into Gnome Classic. 

I will log out and switch to the latter and edit this if things are different.
[COLOR=Blue]Edit: Things got a bit complex so I have made a new Post.
Briefly it only happened in Gnome classic when opening the Home folder.[/COLOR]
Chao!, bogan

---

### Post by bogan on 2012-01-19
Hi!, **Joel & Paddy**,

After fairly extensive tries I was unable, in 11.10, logged into Ubuntu[Unity],to reproduce this effect of App Windows opening behind the Current focused Window. **Edit**: *Though I could logged into Ubnuntu 2D.*

Logged into Gnome Classic with, and without, Ubuntu 2d Launcher active, the effect was fairly, though not entirely, predictable.

First: it was far more likely to occur if there was no gap, exposing the Desktop, between the focused Window and the Launchpad .**Edi**t: *This was an illusion caused by dragging the top window to access the one behind.*

Second: I was unable to get it to occur when opening anything other than the FileManager> Home Folder. Gedit always opened in front.

Third: The effect was the same whether the Launchers were exposed or hidden, and Super><3 was used to open the Folder, or it was opened from Applications>Accessories>Files or Places>Home Folder.

Fourth: It did not seem to make any difference whether the existing window was actually focused, or if the Mouse was clicked with its cursor on the Desktop. What did have an effect was whether the Window had just been moved or not; opening a second or third time without moving it and the Home Window opened in front.

Fifth: I tried using Firefox, Gedit, Software Manager, and LibreOffice Windows as the existing Window. **Edit**: *Later, see other Posts, also with Terminal WIndows*.
 The effect occurred with all of them, but was more consistent with the Gedit Window as the Home Window nearly always lined up its left edge with that of Gedit, where ever it was. Whereas, with the other Windows it varied in its placing. **Edit**: *It also did this with a Terminal Window*.

Sixth: When there was no gap between Window and Launcher, the Home Window often opened behind the Launcher, which did not hide until the Home Window was clicked on to make it focused. **Edit**: *This was incorrect, Windows often open behind the Launcher and it stays until the Mouse Cursor is moved away. The Home Window did this even when opening in front of the existing Window.*

Edit: As a matter of interest, it does not happen in 10.04.  **Edit 20/01/12** *Edit notes added after repeating tests on a second 11.10-14  computer*.

Chao!, bogan.

---

### Post by Paddy Landau on 2012-01-19
That's interesting. You could raise a bug report but, as Gnome Classic is to be discontinued in 12.04, the developers are unlikely to do much about it.

Joel -- are you using Gnome Classic?

---

### Post by Joel Duckworth on 2012-01-19
Thanks for the help, I'm running stock 11.10 32bit and just logging into the default interface (Unity right?) I didn't think you could log into classic without installing something extra? I've got an oldish Intel laptop with an Nvidia card (Quadro NVS 110M/GeForce Go 7300)

Well I think you might be onto something with opening the home folder. I usually have Chromium open on the screen but not maximised or stretched right to the edge. Most times I press the home folder it opens behind Chromium... not every time though

If I open Terminal from the Launcher and then the home folder, it opens behind the terminal window every time... Even if terminal is maximised...

Actually... with a bit more playing around, I think it might only be happening when there is a terminal window open...

Hmmmm

UPDATE: it's also happening with Tomboy notes and Skype (opening behind Chromium), without Terminal open... but it doesn't happen all the time... weird

---

### Post by Joel Duckworth on 2012-01-19
also, I'm just single clicking and I haven't made any changes to compiz

---

### Post by Joel Duckworth on 2012-01-19
Bogan, can you try logging into the Unity interface, opening terminal and then clicking the home folder from the Launcher?

Does it open behind the terminal window every time you do it?

---

### Post by bogan on 2012-01-20
Hi!, **Joel & Paddy,**
Joel Posted:> Bogan, can you try logging into the Unity interface, opening terminal and then clicking the home folder from the Launcher?Short answer1: Yes! I have, and it is the same as a gedit Window.
> Does it open behind the terminal window every time you do it?Short answer2: No! Not in a "Ubuntu" Login, but [COLOR=Red]_sometimes_[/COLOR] in a "Ubuntu 2D" or Gnome Classic login, whether there is a Terminal Window open or not.

Longer answer: I had not actually tried with a Terminal Window previously, but opening the Home folder with a Terminal Window, behaves exactly the same as it does with a Gedit Window. ie. When the later is moved, the Home Window tracks it, and opens behind but horizontally lined up with it.

I will edit my previous Post to match what I have found since, after trying out the same things on my other -WinVista - m/c, which also has 11.10-14 installed, like this Win7 m/c, but does not have Gnome3 installed, it is an 'Update' installation, whereas this one is a clean LiveUSB install, and does behave differently in some ways
 As far as this Window Behind effect is concerned, it behaved in all respects the same way.
 [ The only exception being the behavior of the LaunchPad, probably because it is set to a different 'Fade & Hide' mode.]

The " _sometimes_ " is essentially that this effect only seems to occur when the existing Window has been moved - dragged - immediately before opening the Home Window; not always then, but perhaps 90% certain.

As far as the Bug Report issue is concerned,  for me this is a curiosity and a minor inconvenience, clearly not intended, but not in the Bug class.

If you, Joel, are in doubt as to which set-up you are using, the Login Screen will tell you, and you can select from what is available - it does not surprise me as it took me some weeks with 11.04 & 11.10 before I understood the differences and capabilities of each and their variations.

Alternatively, run: ps ax | grep unity; if you are running Ubuntu 2D you will get something like: ```
ps ax | grep unity
 4279 ?        Sl     0:01[COLOR=Red] unity-[/COLOR]2d-launcher
 4280 ?        Sl     0:00 [COLOR=Red]unity[/COLOR]-2d-panel
 4347 ?        Sl     0:00 /usr/lib/[COLOR=Red]unity[/COLOR]/[COLOR=Red]unity[/COLOR]-panel-service
 4509 pts/0    S+     0:00 grep --color=auto [COLOR=Red]unity[/COLOR]
```If you are running Ubuntu[Unity] you will get something like:```
 ps ax | grep unity
 4804 ?        S      0:00 /usr/bin/[COLOR=Red]unity[/COLOR]-window-decorator
 4807 ?        Sl     0:00 /usr/lib/[COLOR=Red]unity[/COLOR]/[COLOR=Red]unity[/COLOR]-panel-service
 4872 ?        Sl     0:00 /usr/lib/[COLOR=Red]unity[/COLOR]-lens-applications/unity-applications-daemon
 4874 ?        Sl     0:00 /usr/lib/[COLOR=Red]unity[/COLOR]-lens-files/[COLOR=Red]unity[/COLOR]-files-daemon
 4876 ?        Sl     0:00 /usr/lib/[COLOR=Red]unity[/COLOR]-lens-music/[COLOR=Red]unity[/COLOR]-music-daemon
 4920 ?        Sl     0:00 /usr/lib/[COLOR=Red]unity[/COLOR]-lens-music/[COLOR=Red]unity[/COLOR]-musicstore-daemon
 5006 pts/0    S+     0:00 grep --color=auto [COLOR=Red]unity[/COLOR]
```Chao!, **bogan**

---

### Post by bogan on 2012-01-20
Hi!, **Joel**.

You Posted:>  UPDATE: it's also happening with Tomboy notes and Skype (opening behind  Chromium), without Terminal open... but it doesn't happen all the  time... weirdI do not have Skype, but I just tried out TomBoy Notes and it behaves in the same way as the File Manager, except that it does not track the Active Window as it is moved.

Another thing I have noticed - it happened again with Tomboy just now -  is that, directly after a reboot, but not always after logging out and  in again, even if the existing Window has been moved, the first time the  new Window is opened, it does so in its default location and size, **and** in front..  
Closing it, moving the existing Window and re-opening it, it shows behind, and in some cases, a different size.

It would be interesting to know if this is common, just unremarked.

From what I have found, it seems conclusively an error in the procedure which 'remembers' the location and size in which a Window is closed, so that the next time it is re-opened or unminimized, it should do so the same as before.

BTW:  It does** not** occur when logged into Gnome.  ie Gnome3, not gnome Classic.

Chao!, **bogan**.

---

### Post by homersbrain14 on 2013-04-28
I was having this issue.  Here is what fixed it for me.

1) Install compizconfig-settings-manager

2) Press Alt-F2 and type ccsm and press enter

3) Find and click the "General Options" button

4) Click the Focus and raise behaviour tab

5) Make sure the "Auto-Raise" is checked.  Also not a bad idea to change the Focus Protection to off

After that, all worked great.  Hope this helps.

---

