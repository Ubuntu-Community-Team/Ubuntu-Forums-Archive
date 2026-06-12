---
title: "Cairo Dock Plugins Not Working (Ubuntu 12.04)"
date: 2012-05-27
forum: General Help
---

### Post by cbanakis on 2012-05-27
I just did a clean install of Ubuntu 12.04 32bit.

The first thing I did was install all available updates.

Next I installed Cairo.

For some reason, none of the plugins/add-ons seem to be working correctly.

The weather add-on wont search to find my location, and displays no icon.

I only have 2 themes available for Cairo.  (Last time I installed, there were several more)

If I try to add an applet from the Cairo website via "Drag this link onto your dock" I get an error "Sorry, this module couldn't be added"

I have tried with and without open gl

I have tried purging Cairo from my system, and reinstalling.

Even tried wiping the hard drive, and starting from scratch.

I have 12.04 installed with Cairo running on my other computer, and everything worked perfectly on the first attempt.

All I have done for the last 7 hours, is try to get this to work, and I have no idea what the problem could be.

Any ideas?

Thank you very much for your time, and wisdom.

---

### Post by derklempner on 2012-05-28
```
sudo apt-get install cairo-dock-plug-ins
```

---

### Post by cbanakis on 2012-05-28
> **derklempner said:**
> ```
sudo apt-get install cairo-dock-plug-ins
```

Tried that, looks like everything was already installed, its just that nothing is working.

Also, every single applet/launcher I have on the dock only has 1 icon to choose from.

there should be like 10 trash can icons, but there is only the 1.

this whole situation I am in makes absolutely no sense.

---

### Post by cbanakis on 2012-05-28
It seems like the problem is that Cairo doesn't seem to have access to the internet, in some weird sorta way?

---

### Post by cbanakis on 2012-05-28
OK, I figured out that the problem is 100% related to a setting in my router.

I bypassed my router, plugging my computer directly into my modem, and the problem no longer exists.

Does anyone have any idea where I should begin with the router settings?

---

### Post by cbanakis on 2012-07-02
I'm just keeping the other router till I have a need for dual wan's again.

Guess I'll have to figure out the exact cause then.

---

