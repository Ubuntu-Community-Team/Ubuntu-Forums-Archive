---
title: "gnome gone"
date: 2009-11-11
forum: General Help
---

### Post by elggarc on 2009-11-11
I completed an update the other day and, following a reboot, I get my desktop but none of the bars across the bottom and top of the display.

The desktop works fine.  If I open a terminal window and type firefox, the browser starts (Hurrah!)

I've discovered that the bar across the bottom is called gnome-panel.
If I open a terminal window and type "gnome-panel" I get the following error:

```
gnome-panel: error while loading shared libraries: libgnutls.so.26: cannot open shared object file: No such file or directory
```

I've downloaded and recompiled GnuTLS, but that makes no difference so I assume this error doesn't mean libgnutls isn't available.

Any ideas greatly appreciated.

---

### Post by 73ckn797 on 2009-11-11
Open Applications/Accessories/Terminal and enter the following command:

```
 gconftool-2 --recursive-unset /apps/panel
```

You will have to restart Ubuntu for the change to take effect. See how that works. It repairs panels when they get deleted or lost in some way. Will it work for this situation? It isn't too much trouble to find out.

---

### Post by elggarc on 2009-11-11
Thanks for the suggestion.

Firstly I can't use the menus as you suggest because the bar across the top is missing as well as the bottom one.

Fortunately I can open the terminal via the popup menu launched when I right-click the desktop.

I entered your suggested command.  It did not return any output at all (no success message, no error).

I rebooted and, sadly, no change.

I assume it would have errored if it needed root permissions?

---

### Post by jerrycrabb on 2009-11-23
Oh wow and oh no, I'm in the same situation. 

I just did system upgrade and now my desktop is exactly as previous poster described. 

I don't have the option to open terminal when I right click the desktop though, I think that was an add-on he must have.

-Jerry

---

### Post by t0p on 2009-11-23
Right-click on the desktop near the top of the screen and select 'New panel'.  A new panel should appear acros the top of the Desktop.

Now you can right-click on the new panel, select 'Add to panel' and you get the option to add all sorts of stuff: menus, launchers, the whole caboodle.  Set it up the way you like it.

---

### Post by jerrycrabb on 2009-11-23
> **t0p said:**
> Right-click on the desktop near the top of the screen and select 'New panel'.  A new panel should appear acros the top of the Desktop.

Now you can right-click on the new panel, select 'Add to panel' and you get the option to add all sorts of stuff: menus, launchers, the whole caboodle.  Set it up the way you like it.

I wish it were that easy.

Something is actually WRONG.

---

### Post by jerrycrabb on 2009-11-23
> **alien21010 said:**
> Hey guys,

I too was having this problem, but found that you can repair the damage done by the switch pretty easily.  If you are already to the point where nothing is displaying on the screen, either go to a fail-safe terminal (CTRL+ALT+F2), or make a new launcher on the desktop (depending on which mode you got stuck in).  In this terminal, delete all the configuration folders listed below:

.gconfd
.gconf
.gnome2
.gnome2_private
.config

You can remove them by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

It seems to be linked to the .config folder, and removing that one might solve the problem by itself. The config folders will rebuild themselves once they are removed, restoring the system to defaults.

I tried the above solution, my wallpaper went back to the karmic default but I have nothing more than a wallpaper.

---

### Post by jerrycrabb on 2009-11-26
Here's an update!

I still have the same problem :(

However, after learning that ctl + alt + f2 will take me to the failsafe prompt I have tried some stuff that might help narrow things down.


I have tried editing the xorg.conf file. This was fun because it resulted in a BLACK screen instead of a BLANK screen. subsequently I learned how to re-instate my backup xorg.conf file to get me back to my initial issue. 

I have also tried re-installing the ubuntu-desktop package and the metacity pagackage.

Hope this helps you help me, which I am grateful for!

-Jerry

---

### Post by jerrycrabb on 2009-11-26
> **73ckn797 said:**
> Open Applications/Accessories/Terminal and enter the following command:

```
 gconftool-2 --recursive-unset /apps/panel
```

You will have to restart Ubuntu for the change to take effect. See how that works. It repairs panels when they get deleted or lost in some way. Will it work for this situation? It isn't too much trouble to find out.


I didn't report back on this earlier. It did not work for my instance either.

-Jerry

---

### Post by 73ckn797 on 2009-11-27
You stated you performed an update. I assume that was not a fresh install? There have been many problems with doing an update instead of a fresh install. There have also been plenty of flawless updates but problems can occur.

---

### Post by jerrycrabb on 2009-11-27
> **73ckn797 said:**
> You stated you performed an update. I assume that was not a fresh install? There have been many problems with doing an update instead of a fresh install. There have also been plenty of flawless updates but problems can occur.


when I say "update" I may be using the wrong terminology. What I mean is the one of the periodic system updates ubuntu asks me to do from time to time. 

I have been running Karmic for some time without issue, the upgrade from Jaunty to Karmic went very smoothly.

-Thanks for the help

Jerry

---

### Post by 73ckn797 on 2009-11-27
> **jerrycrabb said:**
> when I say "update" I may be using the wrong terminology. What I mean is the one of the periodic system updates ubuntu asks me to do from time to time. 

I have been running Karmic for some time without issue, the upgrade from Jaunty to Karmic went very smoothly.

-Thanks for the help

Jerry

That answered my question. No charge for the help!  :p

---

### Post by jerrycrabb on 2009-11-27
As another update, I am posting a "blurrycam" pic of my issue:

The mouse moves around but clicks are useless.

[IMG]http://i39.photobucket.com/albums/e187/jerrycrabb/saddesktop.jpg[/IMG]

---

### Post by Bernard Hurley on 2009-11-27
I had a similar problem. It appeared to be a problem with the file .gconfd/saved_state being corrupted. Deleting it (actually I just moved it because I am a bit paranoid about thesew things!) and logging in again solved the problem. The desktop came back more or less how I expected - thee may be some differences, but I can't see what they are! I assume .gconfd/saved_state contains all the stuff in the other directories you mentioned in a binary form to allow gnome to ititialise more quickly. If you delete these other directories you will have a lot of work getting your desktop back to how you want it.

---

### Post by jerrycrabb on 2009-11-27
> **Bernard Hurley said:**
> I had a similar problem. It appeared to be a problem with the file .gconfd/saved_state being corrupted. Deleting it (actually I just moved it because I am a bit paranoid about thesew things!) and logging in again solved the problem. The desktop came back more or less how I expected - thee may be some differences, but I can't see what they are! I assume .gconfd/saved_state contains all the stuff in the other directories you mentioned in a binary form to allow gnome to ititialise more quickly. If you delete these other directories you will have a lot of work getting your desktop back to how you want it.

Thank you for your help, but this did not fix the problem.

I appreciate you trying!

-Jerry

---

### Post by jerrycrabb on 2009-11-27
*sigh*

I've backed up my data and am commencing re-installation. 

This is like admitting failure :(


-Jerry

---

### Post by 73ckn797 on 2009-11-27
> **jerrycrabb said:**
> *sigh*

I've backed up my data and am commencing re-installation. 

This is like admitting failure :(


-Jerry


Not a failure, a learning experience! Edison had several thousands tries before he got it right.

Probably not much comfort but not a failure as long as you do not give up.

---

