---
title: "Enabling the terminal bell"
date: 2012-04-11
forum: General Help
---

### Post by Fafnir089 on 2012-04-11
Hi all!
 I've installed Lucid Lynx on a Laptop for testing purposes.

1. No beep in XFCE terminal windows with: CTRL+G or echo -e "\a" or pressing TAB
2. It works on TTY1 (CTRL-ALT+F1)
3. module pcspkr is blacklisted (no change in behaviour when the module is loaded, so I leave it blacklisted)
4. /etcinputrc: # set bell style none (is commented out)
5. apt-get install beep : OK, is working
6. Alsa Mixer Element "Beep" is on and the fader is open
7. In XFCE Settings Manager under "Appearance/ Settings" I've enabled two sound related checkboxes. I have a German layout. I cannot tell how they are correctly named in English. Maybe something like "Enable event sounds" and "Enable acoustic feedback".
8. MiscBell=TRUE in ~/.config/Terminal/terminalrc
9. in /etc/pulse/default.pa I've enabled
     load-module module-x11-bell sample=bell-windowing-system

I've spend some time to find a solution but no success. If you`re using Linux for your Desktop work then you may find the console beep is a plague. But I`m using the echo -e "\a" in several shell scripts that run on servers. It would add much comfort to editing when I would be able to test those shell scripts in a X11 environment like XFCE.
Can someone help please? (Is it a bug?)
Best regards,
Fafnir089
:p

---

### Post by nothingspecial on 2012-04-11
Question moved out of ancient thread to one of it's own.

---

### Post by Fafnir089 on 2012-04-12
Hi all,
found time to investigate. This is probably the same issue:
[https://bugzilla.redhat.com/show_bug.cgi?id=607393](https://bugzilla.redhat.com/show_bug.cgi?id=607393)
Maybe a workaround through pulseaudio is possible. Did not test that yet. What bothers me is that 
Xubuntu Lucid Lynx has no system sounds on board. Could someone tell me a package which delivers some bell and beep sounds in *.wav format?
By the way: the path to the xfce4-terminal "Advanced topics" documentation is
/usr/share/doc/xfce4-terminal/html/C/advanced.html

---

