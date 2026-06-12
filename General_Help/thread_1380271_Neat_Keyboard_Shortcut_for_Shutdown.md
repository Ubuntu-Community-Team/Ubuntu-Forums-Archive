---
title: "Neat Keyboard Shortcut for Shutdown"
date: 2010-01-13
forum: General Help
---

### Post by mlnoone on 2010-01-13
To get the gnome shutdown dialog directly via a keyboard shortcut, add this command to the Keyboard shortcuts (under System -> Preferences):

/usr/lib/indicator-session/gtk-logout-helper -s

Give it a suitiable name, like Shutdown, and then map it to the Keyboard combination of your choice, by clicking under the 'Shorcut' column (which will be showing "Disabled", until mapped).  I just mapped it to Windows Key + End.

Now, enjoy shutting down your system!

---

### Post by fancypiper on 2010-01-13
For tips/howtos, I think you should [Mark Your Thread as [SOLVED] ](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6).

Nice tip but why shutdown? I shutdown only when I add hardware and reboot for a new kernel.

I just press the power button on my monitor.  I let my box run all the time that I can since I have started developing my website served by my computer.

BTW, I have an alias in my .bash_aliases file for shutting down:

off='shutdown -h now'

---

