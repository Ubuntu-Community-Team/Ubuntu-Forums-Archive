---
title: "Boots only to background"
date: 2011-01-19
forum: General Help
---

### Post by Brianpcooney on 2011-01-19
A couple weeks ago i installed Ubuntu with Gnome on my Dell inspiron 9400, on a fresh new(empty) hard drive. Went without a hitch and has worked great for a couple weeks.
A couple nights ago, i opened the update manager and saw that there were a few recommended updates, i browsed through them, none looked spooky or anything so i installed them all.  After rebooting, my computer now does nothing at all. I get to the log in, i type in my password and then after that, all that's there is my background picture. No status bars, no wifi connections. I can right click and get a menu, but there's nothing there of any help, just background settings.
I'm an ubuntu newbie for sure. i'm trying to figure it out as i go along, finding advice in forums and stuff. but i havent seen this problem anywhere.
I installed from a live iso. i'm not sure if i can put it back in and somehow undo whatever happened. I'm at a complete impasse with this.
Any help is MUCH appreciated

---

### Post by lithopsian on 2011-01-19
Sounds like your desktop startup is borked.

Right click and menu (Openbox?) suggests that the desktop itself is loading find, but the autostart.sh is not, so no panel, no applets, no conky (?).

Nothing on the menu?  Maybe not Openbox?  Maybe your home directory is corrupted?  Try booting to the command line (or starting a terminal is you can, maybe alt-f2?).  Then check your partitions.  If you boot often enough, it will happen automatically, or you could force it.

---

### Post by Brianpcooney on 2011-01-20
ok, i've got no openbox or anything like that. alt f2 doesn't do anything.
I have a blank cd in so i have an icon on the desktop where i can access the file manager.  but again, i'm a brand new user, coming from windows, so it's not much good to me as i'm still learning file extensions and basic stuff like that.
If i reboot from my live ISO, can i reinstall back to the original configuration without losing everything i've done with it for the last two weeks?

---

### Post by Brianpcooney on 2011-01-20
ok, i have it running and apparently everything works. i just can't access anything because i have no status bar or menu bar and i can't seem to get them back because i can't open up any control panel like items because they're all in the menu. been scrolling through help program tryng to figure out how to open something that will help me. none of the key commands seem to work. the problem is much simpler than i originally thought. but i still can't figure out how to fix it

---

