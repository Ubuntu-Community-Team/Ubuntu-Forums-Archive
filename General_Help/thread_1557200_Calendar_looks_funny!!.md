---
title: "Calendar looks funny!!"
date: 2010-08-20
forum: General Help
---

### Post by s0rc3r3r on 2010-08-20
I think this is the first tme I am giving attention to Ubuntu Calendar and was quiet surprised to see 31 (repeated),32,33,34,35,36 shown in the calendar
Well!! seems like a bug to me.

I am attaching a screen shot in .jpg format for you to see it.

is there a fix for that?
I hope its does not have critical sub issues!

can anyone please provide some input regarding the same?

---

### Post by Tamlynmac on 2010-08-20
That represents the week of the year. As in 52 weeks in a year. For example, today (Fri Aug 20, 2010) is in the 33rd week of the year 2010.

Good Luck and I hope this helps.

---

### Post by ankspo71 on 2010-08-20
Hi,
I'm not using Gnome, but I think you are referring to the week numbers. 

I think it's possible to turn it off.

[http://people.gnome.org/~bmsmith/gconf-docs/C/clock-applet.html](http://people.gnome.org/~bmsmith/gconf-docs/C/clock-applet.html)
> /schemas/apps/clock_applet/prefs/show_week_numbers 

Press Alt+F2 and type gconf-editor to run the Gnome Configuration Editor.

When the Gnome configuration editor opens, search for clock_applet, then see if there is an option to turn off the week numbers. (I'm not finding any help on Google about this)
Hope this helps.

---

### Post by s0rc3r3r on 2010-08-20
> **ankspo71 said:**
> Hi,
I'm not using Gnome, but I think you are referring to the week numbers. 

I think it's possible to turn it off.

[http://people.gnome.org/~bmsmith/gconf-docs/C/clock-applet.html]("http://people.gnome.org/%7Ebmsmith/gconf-docs/C/clock-applet.html")


Press Alt+F2 and type gconf-editor to run the Gnome Configuration Editor.

When the Gnome configuration editor opens, search for clock_applet, then see if there is an option to turn off the week numbers. (I'm not finding any help on Google about this)
Hope this helps.

Thank you people for clearing that.
I was using the Windows Operating system.So I was surprised to see those numbers in the familiar Tool.
That's pretty nice that Ubuntu has such an option in the Calendar.
I used to screw around with the UBuntu Settings..thought that those numbers were side effect.
Anyway! I am learning new things everyday from here.Simple and Complicated
Thanks guys!!!

---

