---
title: "Improper Window Decorations?"
date: 2011-05-10
forum: General Help
---

### Post by RallyDarkstrike on 2011-05-10
Hey all, just upgraded my Ubuntu VM from 10.10 to 11.04 and have managed to get Compiz working well, however, I cannot seem to change my window decoration themes under the Appearance tab?

I have a number of pre-saved themes from my 10.10 install that look fine in the Appearance menu, but when I select one of those themes the actual window decorations won't change at all - I.E. the colors won't change, the interface theme won't change, etc.

The only part of it that does work is that it asks me if I want to change the background image as usual.

Any ideas how to fix this? I know 11.04 has been getting some criticism for Ubuntu Classic not working completely right, and I seem to have unfortunately fallen into that category as I am not a fan of Unity.

Cheers for any assistance! :)

---

### Post by VCoolio on 2011-05-10
Maybe compiz is using emerald for window decorations? Set it so gtk-window-decorator. Try this:```
gtk-window-decorator --replace
``` and select another theme again. Or use emerald manager to switch emerald themes if you like those. And if this is the issue ;).

---

### Post by ghostborg on 2011-05-10
Try fusion-icon which should allow you to select your window decorator.
Can find it in Synaptic package manager. Does not load in Unity but shows up in Ubuntu classic.

---

### Post by RallyDarkstrike on 2011-05-10
> **VCoolio said:**
> Maybe compiz is using emerald for window decorations? Set it so gtk-window-decorator. Try this:```
gtk-window-decorator --replace
``` and select another theme again. Or use emerald manager to switch emerald themes if you like those. And if this is the issue ;).

Thanks Ghostborg - I am trying VCoolio's suggestion first.

I've tried that command in terminal; no luck. the decorations flicker, but when I go to select one of my themes in the Appearance menu, they still do not work properly. Not sure if this is a hint at what the problem is, but I've noticed that my scroll-bars don't look like they used to in 10.10, they are instead simply a blue rectangle with no noticeable "scrollbar" part until I mouse over them...and once moused-over, scroll arrows appear?

I'm really not sure what's going on...The colors are stuck at a light gray for the windows with the titlebar being a bluish color. I JUST noticed that the actual "Window Border: DOES change to what it is supposed to, but the window "Controls" seem to be permanently stuck on "Industrial" ?
[COLOR=DarkRed]
EDIT: Just tried opening the Emerald Manager and it tells me that it is not installed. Starting to think may have something to do with it: when I was installing the update from 11.04 to 10.10, the installer did give me a few errors. Is there any command I can enter or method I can use to simply reinstall the 10.10-11.04 update again and see if that solves anything?[/COLOR]

---

### Post by VCoolio on 2011-05-10
Open a gtk app from the terminal and check for gtk output. Just a 'zenity --info' window will do if you have it installed, or 'evince'. Maybe that gives us a hint. And maybe a screenshot? (remember forum policy, just a thumbnail, or a link to the real thing).

---

### Post by RallyDarkstrike on 2011-05-10
Alrighty, lessee....a quick type of "zenity --info" into terminal (without the quotes, of course) returns a small window that says "All updates are complete." Evince seems to open fine as well. Screenshot to follow in a moment...(gotta log out of the VM as for some reason screenshots in it don't work right but I have a workaround.)

[COLOR=Red]EDIT: Link to a screen I took of my Ubuntu VM desktop....not sure why that window on the left is so terribly transparent, I had already closed it when I took the screenshot. Anyway, the issue I am explaining is the coloring on the window decorations. As you can see from the "Appearance Preferences" window, the theme that is selected is supposed to have dark blue windows with slightly lighter titlebars, and as you can see the windows are light gray with a different shade of blue for the titlebars...not what is supposed to be displayed at all. The "Window Decorations" are the correct style, but as you can also see on the desktop panels for GNOME, the "Controls" are still stuck on the Industrial theme. That light-gray rectangle on the right side of the "Appearance Preference" window is the scrollbar I am talking about; instead of a regular scroll bar, I get that, and when I mouse over it it becomes a light shade of blue with arrows next to it and I can drag it to scroll. You can't see the Applications / System / etc. menus at the bottom, or the date/time weather because the selected theme is supposed to be using a white font for those but they are coming up as black.

[http://img263.imageshack.us/img263/1972/desktopuj.png](http://img263.imageshack.us/img263/1972/desktopuj.png)[/COLOR]

---

### Post by VCoolio on 2011-05-10
I don't know, I'd say a buggy theme, that would explain parts working and others not; didn't opening an app in the terminal result in error output there? What if you open "gnome-appearance-properties" in the terminal and try to change themes away and back to the one you want? 
And is gnome-settings-daemon running ("pgrep -l gnome-settings-daemon" will tell you)?
The transparant thing is your video card/driver not being able to keep up I think, not related to this.
Going to bed soon, hope someone else drops by to be of more assistance.

---

### Post by RallyDarkstrike on 2011-05-10
I appreciate all the help Vcoolio :)

I'm not so sure if it is a buggy theme as ALL of the 9 or so themes I had saved from 10.10 that used to work fine all do this to me now; even when I create a new theme the colors will not change, nor will the "Controls."

I haven't received any error messages when starting apps that I am aware of. Everything seems to work fine except this issue with the theming. Also, tried starting the Appearance settings using "gnome-appearance-properties" in Terminal...no dice, same issue :(

As for the "pgrep -l gnome-settings-daemon" command...tried that in Terminal and it seemingly didn't give any output at all? Not sure if that is a good or bad thing or not...I pasted it from your post, then hit enter and it just went to a new blank line with "user@machine:~$" as always :(

[COLOR=DarkRed]EDIT: Hmmm....for the heck of it, I tried typing "gnome-settings-daemon" into the Terminal to see what it would say and I did get a sort of error message in the Terminal:[/COLOR]

[COLOR=Red]user@machine:~$ gnome-settings-daemon

** (gnome-settings-daemon:3805): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:3805): WARNING **: Could not acquire name[/COLOR]

[COLOR=DarkRed]Any thoughts?[/COLOR]

---

### Post by VCoolio on 2011-05-11
well, let's check this then, last guess: install lxappearance, change themes with that, see what happens, open some gtk app when done. If it doesn't work, uninstall and remove ~/.gtkrc-2.0 and ~/.grkrc-2.0.mine to clean up.

The warnings when starting the daemon are just warning and have something to do with dbus. No deal breaker.

---

### Post by RallyDarkstrike on 2011-05-11
Alrighty, I'll give a try to that "lxapearance" thing in a few and report back with my experience.

If it doesn't work it's not too big a deal; it is only a VM that I tinker with, so I don't mind reinstalling...just that reinstalling is a pain in the butt when I've had that VM for a year and a half now. :)

[COLOR=Red]EDIT: Ok...installed lxappearance; I can change window coloring with it fine, however, the bordering of the window still will not change, not will the "Controls" still stuck on Industrial. I.E. the titlebar and the very edges/border of the windows, as in this screenshot:

Image Link: [COLOR=Blue][http://img848.imageshack.us/img848/3687/lxappearance.png](http://img848.imageshack.us/img848/3687/lxappearance.png)[/COLOR]

(Sorry that took so long, had to take a phone call!) Any other ideas?
[/COLOR]

---

### Post by RallyDarkstrike on 2011-05-15
Bit of a late reply....however I have somehow managed to get the coloring working again. As in, if I select themes in the Appearance Menu, the colors will change properly now. I still, however, cannot seem to get the "Controls" to change from anything other than Industrial, and I also still can't see scroll bars the regular way.

I've run out of ideas though, so I am just hoping whatever is causing my problems gets fixed in an update...

---

