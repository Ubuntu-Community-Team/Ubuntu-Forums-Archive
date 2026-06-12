---
title: "Need a Remainder in Ubuntu natty"
date: 2011-07-27
forum: General Help
---

### Post by madhu542 on 2011-07-27
Hi everyone,

I want to install a package which should work like, on a given time or date, it should pop up with **remainder/alerts**.

I installed Tomboy notes and tried some thing by goggling but end up with no luck.

Any help in this would be greatly appreciated. :popcorn:

Thanks.

---

### Post by plucky on 2011-07-27
> **madhu542 said:**
> Hi everyone,

I want to install a package which should work like, on a given time or date, it should pop up with **remainder/alerts**.

I installed Tomboy notes and tried some thing by goggling but end up with no luck.

Any help in this would be greatly appreciated. :popcorn:

Thanks.

There is a Reminder Addin for Tomboy Notes.

If you open Tomboy Preferences and go to the Addins Tag,at the bottom of the window there is "Get More Addins" button which will take you [Here](http://live.gnome.org/Tomboy/PluginList).

If you download the binary file and move it to ~/.config/tomboy/addins/ directory you should be able to get Tomboy to provide reminders.

I used this a long while ago,but haven't done so lately.

Let me know if it still works.

Good Luck.

---

### Post by cybergalvez on 2011-07-27
> **madhu542 said:**
> Hi everyone,

I want to install a package which should work like, on a given time or date, it should pop up with **remainder/alerts**.

I installed Tomboy notes and tried some thing by goggling but end up with no luck.

Any help in this would be greatly appreciated. :popcorn:

Thanks.

Isn't this a function of the builtin calendar? I know that this will work with thunderbird if I leave it running (hoping that better integration in the next version will make this work better)

---

### Post by madhu542 on 2011-07-28
> **plucky said:**
> There is a Reminder Addin for Tomboy Notes.

If you open Tomboy Preferences and go to the Addins Tag,at the bottom of the window there is "Get More Addins" button which will take you [Here](http://live.gnome.org/Tomboy/PluginList).

If you download the binary file and move it to ~/.config/tomboy/addins/ directory you should be able to get Tomboy to provide reminders.

I used this a long while ago,but haven't done so lately.

Let me know if it still works.

Good Luck.

[COLOR="Red"]Thanks for the replies!
Plugin I downloaded (tomboy-reminder-0.9.2.tar.gz) and placed in the given above path and gave a sample note with time for testing purpose but it didn't worked.[/COLOR]

---

### Post by plucky on 2011-07-28
> **madhu542 said:**
> [COLOR="Red"]Thanks for the replies!
Plugin I downloaded (tomboy-reminder-0.9.2.tar.gz) and placed in the given above path and gave a sample note with time for testing purpose but it didn't worked.[/COLOR]

Just installed it on 11.04 and it worked.

1) Download the dll file and copy that to ~/.config/tomboy/addins/
1a) You might have to reboot.
2) Open Tomboy and navigate to **Edit > Preferences > Add-ins**
3) Enable the Reminder Addin.
4) Add Tomboy to the Startup Applications.
(The Tomboy icon appears in the system tray)
5) Read The Readme notes on how to launch a reminder.

Good Luck

---

