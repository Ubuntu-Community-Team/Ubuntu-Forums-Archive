---
title: "Google Chrome - buttons on right?"
date: 2011-11-06
forum: General Help
---

### Post by werewolves on 2011-11-06
I am using Gnome Shell in 11.10, and one major annoyance that I found is that all of the close buttons are on the right, except in Google Chrome.  Is there a way to force them to the right?

Thanks

PS: I suppose if there is not a way to move the Chrome buttons, I could live with moving the other buttons to the left.  I don't really care what side they are on, as long as it's consistent.

---

### Post by crossedout on 2011-11-06
Easiest way I found to move the buttons to the right side:

[LIST=1]
[*]Open Preferences in Chrome/Chromium
[*]Click 'Personal Stuff' (left-hand side)
[*]Under 'Appearence' select 'Use system title bar and borders'.
[/LIST]

Hope that helps,
-Xout

---

### Post by werewolves on 2011-11-07
Thank you, that does put the button on the right, unfortunately at the expense of adding the standard Metacity window decorations (thus adding some wasted space).  I was hoping to set the buttons to the right without losing vertical space.

This will work for now unless anyone has any other ideas.

---

### Post by carlbastos on 2011-11-10
I have the same problem, and since I am on a netbook, I cannot afford to sacrifice that space the window decoration uses. :(

---

### Post by carlbastos on 2011-11-14
Hey comrades,

I recently found that Chrome/Chromium still uses metacity configuration to define where its buttons are placed even when you are using Gnome Shell.

I tried to make some changes in the gnome configuration database directly using gconf-editor to get the buttons rearranged, however every time I did it the settings were all rolled back once I re-logged. Due to this problem, I used [Ubuntu Tweak]("http://ubuntu-tweak.com/") instead and it worked just fine.

I solved the problem by doing the following:

[LIST=1]
[*]Logged out of my Gnome Shell Session;
[*]Logged in using "GNOME Classic (no effects)" (but I think Unity 2d works the same way);
[*]Ran Ubuntu Tweak (see link above) and changed the buttons order under "Window Manager Settings" to "Right";
[*]Logged out of GNOME Classic and logged in Gnome Shell again;
[*]Voilá - My Chrome now has its buttons placed in the right side;
[/LIST]

Screenshots:

[ [img]http://2imgs.com/2i/t/49736b4192.jpg[/img] ](http://2imgs.com/49736b4192)

[ [img]http://2imgs.com/2i/t/58627a5083.jpg[/img] ](http://2imgs.com/58627a5083)


---

I hope that helps!

---

### Post by werewolves on 2011-11-14
Thanks so much!

---

### Post by Tamale on 2011-11-20
this worked for me as well, many thanks!

---

### Post by jorcarras on 2012-04-10
worked perfectly 4me 2 ... thanks

---

### Post by alco75 on 2012-05-11
[this]("http://askubuntu.com/questions/78288/how-can-i-move-chromes-buttons-to-the-right-in-gnome3s-shell") worked for me in Precise with Gnome Shell

```
gconftool-2 --set /apps/metacity/general/button_layout --type string ":close"
```

---

