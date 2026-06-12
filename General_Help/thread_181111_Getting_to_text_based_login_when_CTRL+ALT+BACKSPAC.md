---
title: "Getting to text based login when CTRL+ALT+BACKSPACE"
date: 2006-05-23
forum: General Help
---

### Post by ToneDispenser on 2006-05-23
Hi there,

I have a little trouble with xorg or Gnome.
When I hit CTRL+ALT+BACKSPACE I get to
the text-based login no. 1

When I hit Alt+F7 I get a black screen with a cursor blinking
in the top left corner of my screen.

"ps -A" tells me that gdm is still running.
No errors are being reported in /var/log/Xorg.0.log
or /var/log/gdm/\:0.log

I want gdm and X to restart when hitting CTRL+ALT+BACJSPACE,
since I connect my TV sometimes and would like to get to TwinView
fast...

Thanks for any hints/tips!
(2 monts without booting the windows partition so far ;))

---

### Post by hw-tph on 2006-05-23
You don't restart GDM by pressing Ctrl+Alt+Bksp - you kill the X server. To gracefully restart it from a terminal type **sudo /etc/init.d/gdm restart**.

You could use an alias if you type this often, like this:
```
alias resx='sudo /etc/init.d/gdm restart
```
Put it in your ~/.bashrc and the command **rex** will prompt you for your password and then restart gdm.


Håkan

---

### Post by pitkali on 2006-05-23
Do you just want to restart your X server? Because then you could edit /etc/gdm/gdm.conf and set the variable AlwaysRestartServer to true, so just logging out of Gnome would restart server gracefully (gdm displaying then the login screen).

---

