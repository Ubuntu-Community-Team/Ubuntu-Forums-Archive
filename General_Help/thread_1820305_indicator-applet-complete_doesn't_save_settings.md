---
title: "indicator-applet-complete doesn't save settings"
date: 2011-08-07
forum: General Help
---

### Post by kedmond on 2011-08-07
In the indicator-applet-complete, I want the date and day to be displayed with the time.  I open the Time & Date Settings, tick off the appropriate boxes, and nothing changes.  The same is true for the Bluetooth icon.  I can't remove the bluetooth icon from the indicator applet.

It seems like a general problem with the indicator applet in that it doesn't save my settings.  I've seen a few bug reports regarding this, but I haven't seen any solutions.  Please help!:confused:

---

### Post by SalHelder on 2011-08-07
You don't use Bluetooth and it still shows up there, right? If so go to

gnome-system-monitor

and kill the respective process and then go to

gnome-session-properties

And remove/uncheck the respective entry.

---

### Post by kedmond on 2011-08-07
> **SalHelder said:**
> You don't use Bluetooth and it still shows up there, right? If so go to

gnome-system-monitor

and kill the respective process and then go to

gnome-session-properties

And remove/uncheck the respective entry.

SalHelder, thanks for that help.  I never knew about that.  So why doesn't the bluetooth preferences do that for me?  It used to work before a recent update.

Now, how do I fix the time & date bug?  These indicator applets have a lot of bugs it looks like.

---

### Post by kedmond on 2011-08-07
I just realized that it's not remembering my weather settings either.  When I login, I have to reconfigure the settings of the Weather Indicator each time.  There's something preventing the Indicator Applets from saving or altering their settings.

---

### Post by SalHelder on 2011-08-07
I'm not sure about indicator-applet, since I haven't used that at all, I just got rid off it when it came installed. But try this:

1. Remove the indicator-applet-complete from the panel, and add the normal clock, that should solve the weather and day problem.

2. Now you'll probably need to install indicator-applet-session and others (check in Synaptic).

3. Add the indicator applets that you want, (do not add the complete one tough).

I guess it might work.

---

### Post by kedmond on 2011-08-07
> **SalHelder said:**
> I'm not sure about indicator-applet, since I haven't used that at all, I just got rid off it when it came installed. But try this:

1. Remove the indicator-applet-complete from the panel, and add the normal clock, that should solve the weather and day problem.

2. Now you'll probably need to install indicator-applet-session and others (check in Synaptic).

3. Add the indicator applets that you want, (do not add the complete one tough).

I guess it might work.


You're awesome.  Thanks so much.  :D

---

