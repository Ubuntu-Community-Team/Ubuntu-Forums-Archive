---
title: "Themes reverted to flat GTK after a system crash, can not change it back"
date: 2009-07-01
forum: General Help
---

### Post by boteeka on 2009-07-01
Yesterday I had a power outage and my Jaunty box was turned off. After the power came back the Gnome theme has been reverted to the default GTK look (no theme). From that point on I can not change the theme from the Appearance window.

I already reinstalled the themes and theme engines, but with no luck.

Can anybody suggest any solutions?

---

### Post by thespirit3 on 2009-07-01
What happens when you try to change a theme?  Does it let you - but then fail to actually make the change?

If this happened to me I'd make a backup of .gnome .gnome2 .gconf and .gconfd in my home directory, move these elsewhere (or remove them - if you have a copy) then log out/in and hopefully they'll all get recreated with the correct contents and permissions. 


Steve

---

### Post by boteeka on 2009-07-01
>> What happens when you try to change a theme?  Does it let you - but then fail to actually make the change?

Yes, that's what is happening. As a matter of fact the colors do apply (on windows and the panels), and the Appearance window even gets themed, but nothing else.

I also followed your advice and deleted those directories, logged out and then back, but I still can't change the theme.

---

### Post by Spooky23 on 2009-07-31
I have exactly the same problem and it applies to all users, even newly created ones. Have you found a solution, yet ? I was able to switch the window appearance beack to the human theme using gtk-theme-switch2, but the icons are still wrong, also for GUI programs run as root using sudo the theme remains the gtk2-flat theme.

---

### Post by metaldark on 2009-08-03
I have the exact same problem.  Some system settings file must have gotten damaged?

---

### Post by hellz99 on 2009-08-04
I'm having the same problem, except I'm pretty sure I didn't have a system crash.  I posted in another thread already here: [http://ubuntuforums.org/showthread.php?t=1231195]("http://ubuntuforums.org/showthread.php?t=1231195")

See if you have the same error entries in your auth.log as I do.

---

