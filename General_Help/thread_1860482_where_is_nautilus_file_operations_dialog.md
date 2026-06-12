---
title: "where is nautilus file operations dialog?"
date: 2011-10-14
forum: General Help
---

### Post by glaubersm on 2011-10-14
Hello
I use oneiric x32 with gnome-shell.
Steps to reproduce the problem
Open nautilus and copy/move some files to other place
When you see the progress window change to other aplicattion window and back to nautilus
Result: Nautilus progress window is hidden and there is no way to give it back

Can anyone confirm this problem? Any workaround?

---

### Post by ezramorris on 2011-10-14
I've seen this, using unity-2d.

I think there's two issues here. Firstly, it doesn't seem possible to alt-tab to the dialog or get to it through the launcher. It might be worth reporting a bug on Launchpad. Secondly, there isn't an icon in the panel, like there used to be, to switch to it. There's already a [bug](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/849733) on this.

Ezra.

---

### Post by glaubersm on 2011-10-14
Thanks for your reply.
I'll wait for a solution to this problem, I think this is the only option at this time.

---

### Post by Flanschbob on 2011-10-15
i just had the same problem and came up with a (dirty) workaround:

get the gnome-tweak-tool via

sudo apt-get install gnome-tweak-tool

when installed it's called advanced settings.

with that, you can activate the titlebar-button for minimizing alongside the close button. you might need to reboot or re-login to see the changes.

once you have the minimize-button you can minimze all the windows and the file operations dialog will show up. hiding all windows with ctrl+alt+d will not do the trick.

a better solution has to come, but this way is better than nothing.

---

### Post by vanadium on 2011-10-15
I do not any erroneous behaviour. Clicking the home folder button brings all nautilus windows on the foreground. Clicking a second time shows all active nautilus windows in spread mode, and one can click the progress dialog. Even using Alt+tab you could switch to it: select the nautilus icon, wait a second and the running windows appear. Use the arrow keys to select the progress window.

---

### Post by ezramorris on 2011-10-15
> **vanadium said:**
> I do not any erroneous behaviour. Clicking the home folder button brings all nautilus windows on the foreground. Clicking a second time shows all active nautilus windows in spread mode, and one can click the progress dialog. Even using Alt+tab you could switch to it: select the nautilus icon, wait a second and the running windows appear. Use the arrow keys to select the progress window.

Are you using the 3d (default) unity by any chance? For me, if I use unity 3d ("Ubuntu" option), I can see all the windows, but in unity 2d ("Ubuntu 2D" option), when I click the home folder button the second time, I only see the nautilus folder windows; the progress dialog does not show up in the spread.

---

### Post by vanadium on 2011-10-15
I should have read better, indeed. The OP is using gnome-shell (I was assuming Unity 3D), you can reproduce the issue with Unity 2D. Indeed, I am using Unity 3D, and here, it works as expected: also the progress dialog is there in the spread.

---

### Post by chrisrico on 2011-10-16
Until the usability of this is improved, using the Ctrl-Alt-Tab keyboard shortcut (accessbility switcher) will allow you to select the file operations dialog.

---

### Post by ezramorris on 2011-10-16
> **chrisrico said:**
> Until the usability of this is improved, using the Ctrl-Alt-Tab keyboard shortcut (accessbility switcher) will allow you to select the file operations dialog.

Good call! Works for me in U2d. :-)

---

### Post by glaubersm on 2011-10-16
> **Flanschbob said:**
> i just had the same problem and came up with a (dirty) workaround:

get the gnome-tweak-tool via

sudo apt-get install gnome-tweak-tool

when installed it's called advanced settings.

with that, you can activate the titlebar-button for minimizing alongside the close button. you might need to reboot or re-login to see the changes.

once you have the minimize-button you can minimze all the windows and the file operations dialog will show up. hiding all windows with ctrl+alt+d will not do the trick.

a better solution has to come, but this way is better than nothing.

It does not work for gnome-shell.

> **vanadium said:**
> I should have read better, indeed. The OP is using gnome-shell (I was assuming Unity 3D), you can reproduce the issue with Unity 2D. Indeed, I am using Unity 3D, and here, it works as expected: also the progress dialog is there in the spread.

Exactly, I use gnome-shell.

> **chrisrico said:**
> Until the usability of this is improved, using the Ctrl-Alt-Tab keyboard shortcut (accessbility switcher) will allow you to select the file operations dialog.

Also it does not work for gnome-shell.


I hope a fix to this stupid usability problem coming soon. :(

---

### Post by chrisrico on 2011-10-16
> **glaubersm said:**
> It does not work for gnome-shell.

Also it does not work for gnome-shell.


It works for me in gnome-shell. I discovered it here: [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by glaubersm on 2011-10-16
> **Flanschbob said:**
> 
once you have the minimize-button you can minimze all the windows and the file operations dialog will show up. hiding all windows with ctrl+alt+d will not do the trick.

a better solution has to come, but this way is better than nothing.

Sorry, really it works!

> **chrisrico said:**
> using the Ctrl-Alt-Tab keyboard shortcut (accessbility switcher) will allow you to select the file operations dialog.

Also it really works.

> **chrisrico said:**
> It works for me in gnome-shell. I discovered it here: [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

My english is so bad! ;)

---

### Post by bravecobra on 2011-10-16
> **chrisrico said:**
> It works for me in gnome-shell. I discovered it here: [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

Tnx. Ctrl+Alt+Tab got it back.

---

### Post by anishsane on 2012-03-18
> **chrisrico said:**
> Until the usability of this is improved, using the Ctrl-Alt-Tab keyboard shortcut (accessbility switcher) will allow you to select the file operations dialog.

Thanks... It worked for me... I was searching for this for a long time :-)


There is one more method. 

```
wmctrl -R "File Operations"
```

This would bring the window to the top. This works even if the window is on some other workspace. [FONT="Courier New"]**wmctrl -R "<window_title>"**[/FONT] is a generic method to bring any window to foreground using some (sub-)string in its title.

Disadvantage of this method is: If there is some other window, containing "File Operations" in its title, that window might come to foreground.


**[FONT="Courier New"]Ctrl-Alt-Tab[/FONT]** works better :-)

Thanks Chrisrico once again.

---

