---
title: "&quot;Try running XORG with the latest VESA drivers&quot;"
date: 2009-11-07
forum: General Help
---

### Post by Vistro on 2009-11-07
What the hell does that mean?

I am having issues installing WoW on 9.10, but it installed okay on 9.04. I am using the latest version of WINE. 

The particular problem is actually Blizzard being a pain in the ***. In order to accept an EULA, one must scroll it down to the bottom. Only then does the "Accept" button become activated, and clickable. I scrolled all the way down, but the button is still greyed out. WoWWiki says to 

"Try running XORG with the latest VESA drivers"

What does that mean, and how do I do it?

thanks!

---

### Post by Tea4all on 2009-11-07
What video card are you using?

---

### Post by Vistro on 2009-11-07
ATI Radeon something. It's running on a four year old Dell laptop.

---

### Post by tetris11 on 2009-11-15
You should find out what Desktop you are using first by logging out, and checking what session you are using (gnome (gdm) or kde (kdm) usually)

Log back in.
Open up a terminal: Applications->Accesories->Terminal

type:
sudo bash                                  (Requests super use)
[enter your password]                      (grants super use)
nano /etc/X11/xorg.conf                    (this brings up xorg configuration)

scroll down to where it says:
Section "Device"   and add/change the line that says:
Driver "whatever",  to  Driver "VESA"              
(REMEMBER what 'whatever' was before you changed it. You might need to change it back)

Then press:
Ctrl+O                          (save?)
[Enter]                         (yes, save)
Ctrl+x                          (exit xorg.conf)

Now you need to restart gnome or kde or whatever you use:
[Remember that you can go back to GUI by pressing Ctrl+Alt+F7)
Press Ctrl+Alt+F1  to go into tty1.
Login with your username, password
type:
/etc/init.d/gdm stop                        (stops gnome)
/etc/init.d/kdm stop                        (stops kde)

Check that GUI is blank (i.e. Ctrl+Alt+F7 is blank)
Go back to tty1 (Ctrl+Alt+F1)

type in only one of these commands (you dont want to have multiple sessions running at the same time!):

/etc/init.d/gdm start                  (starts gnome) OR
/etc/init.d/kdm start                  (starts kde)

And that's it, you are now running on the VESA driver.

Btw, sorry if any of this was condescending. Im a bit of a noob myself and I find it frustrating when people offer help without telling you what they are doing.

Hope that helped!

---

