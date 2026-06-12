---
title: "Crashing Apps"
date: 2012-04-29
forum: General Help
---

### Post by gennatolls on 2012-04-29
What do you guys do when a app crashes to where the whole system become unresponsive? Occasionally this happens to me and I have to do a hard reset. Is there anything equivalent to ctrl+alt+delete like in windows where it gives you the option to open task manager? 

i.e. it takes priority over any other program (the one thats bugging the system down) and brings up the menu

Most the time when this happens Unity has also been unresponsive so I can't get a terminal up or System Monitor to end the task.

Lets hear some ideas, Thanks.

---

### Post by matt_symes on 2012-04-29
Hi

Use the magic key combination to shutdown the computer cleanly.

[http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot](http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot)

Kind regards

---

### Post by Finalfantasykid on 2012-04-29
I have a few ideas.

1.  You could set up a keyboard shortcut in the settings so load up gnome-system-monitor.  This may not work though if you are undergoing extreme cpu/memory usage.  You might be able to make it have higher priority by setting the nice value to some negative number, but I think this requires sudo access.  In which case you could have the command be something like gksu "nice -n -20 gnome-system-monitor" .  There might be a better way of this though.

2.  You could go CTRL + ALT + F1 (or F2...).  This will bring you to a tty where you can execute commands, could be a good place to run a killall command or something, especially if you have a full screen application which has locked up. (ps. to get back to the normal view, you can hit CTRL + ALT + F7 (sometimes F8?))

3.  If all else fails, you can do a CTRL + ALT + BACKSPACE to restart your X server.  This will log you out though, and you will loose any unsaved work.  I think Ubuntu disables this by default, but it can be re-enabled in the Settings > Keyboard Layout > Options > "Key Sequence To Kill X Server" (check that box)

I hope this helps.

---

### Post by gennatolls on 2012-04-29
Many thanks, I haven't heard of any of the mentioned ways. I'll have to give it a try next time something goes wrong

---

### Post by Alan.Brown on 2012-04-29
As a 'quick and nasty' solution I usually use **Alt+SysRec+B.**

See Matt-symes post above

Alan.

---

