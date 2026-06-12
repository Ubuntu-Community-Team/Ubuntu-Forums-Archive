---
title: "Did clean install of Xubuntu 11.10, but facing too many errors"
date: 2011-10-17
forum: General Help
---

### Post by MarjaE on 2011-10-17
Some of these are massive errors, some are minor, but I'm not finding any solutions:

1. Thunderbird cannot import from Evolution backups. I'm not entirely sure what to do here; the Thunderbird import functions just don't work, and the Thunderbird support pages seem to assume that Evolution is still present and working.

2. The main menu, the one at the left of Panel1, stops working, sometimes for an hour at a time. In fact, it's nonresponsive much more often than it's responsive.

3. The Alps Glidepoint. I re-installed the psmouse patch, and it now detects the Alps haywire as a touchpad + stick [there is no stick] instead of a touchpad + PS/2 mouse. But the mouse preferences for Xubuntu do not allow touchpad functions like disabling tap-to-click or disabling the touchpad while typing. I installed Pointing Devices but it does not show up in the settings manager.

4. This is a relatively minor point after the above, but I reset the clock three reboots ago and it's still four hours off.

---

### Post by gsmanners on 2011-10-17
1. Thunderbird probably assumes you can simply load up Evolution and do an "export" from there. So, I would suggest installing Evolution. I'm not sure how well this will work considering Evolution was "designed" to work with Gnome, but it is theoretically possible to use under Xubuntu.

2. You seem to have won the bug lottery. That's some random problem that apparently cropped up in Xfce 4.4 without any discernable way to reproduce it. I actually wish I had that problem so I could help track down what's causing it.

3. Sorry, but I guess I don't have a solution for that.

4. Is it possible to set the clock in the BIOS settings? Maybe you can fix it from there.

---

### Post by MarjaE on 2011-10-17
> **gsmanners said:**
> 1. Thunderbird probably assumes you can simply load up Evolution and do an "export" from there. So, I would suggest installing Evolution. I'm not sure how well this will work considering Evolution was "designed" to work with Gnome, but it is theoretically possible to use under Xubuntu.

2. You seem to have won the bug lottery. That's some random problem that apparently cropped up in Xfce 4.4 without any discernable way to reproduce it. I actually wish I had that problem so I could help track down what's causing it.

3. Sorry, but I guess I don't have a solution for that.

4. Is it possible to set the clock in the BIOS settings? Maybe you can fix it from there.

1. It's a pretty common oversight. Importing from application to application is usually an option. But after reinstalling, or the like, and other critical moments, it may not be.

2. I had the settings manager open, because of 3. It doesn't work with the settings manager open, and it usually works with it closeed. Sometimes I need to open and close the panel preferences or something to get it working.

3. Kinda critical. [P.S. Pointing Devices doesn't seem to show up, but Synaptiks turns up in Accessories, and with the psmouse patch, now works.]

4. I removed the clock from the panel, added an orage clock to the panel, and was able to reset the time within its preferences.

P.S. It would help if we could move Pointing Devices and Synaptiks to Settings.

---

### Post by gsmanners on 2011-10-17
I have seen the panel and the menu flicker at times like that, but I've never had that particular bug. Interesting.

Nice to hear about the clock. Yeah, I use Orage because I like the calendar and the calendar functions it has. Very handy.

---

### Post by Carborundum on 2011-10-17
> **MarjaE said:**
> P.S. It would help if we could move Pointing Devices and Synaptiks to Settings.

You can, if you install the app "Main Menu". It does seem odd that there is no way to do it with pre-installed software though.

---

### Post by MarjaE on 2011-10-17
Anyway, Thunderbird's still not importing from Evolution. I'll look up Main Menu. [P.S. one of the reviews for Main Menu warns Xubuntu users to avoid it.]

---

### Post by Carborundum on 2011-10-17
> **MarjaE said:**
> [P.S. one of the reviews for Main Menu warns Xubuntu users to avoid it.]
Yeah, I saw that. I just installed it though, and I'm running Xubuntu 11.10 (32-bit). It doesn't seem to be causing any trouble for me.

---

### Post by MarjaE on 2011-10-17
I finally copied my evolution emails into Thunderbird. But now when I start Thunderbird, it asks if it is to be the default email application, and then quits.

P.S. And then Firefox and Thunar quit too. I rebooted. By the way, how do I enable a compose key and enable a keyboard-layout-toggle in Xubuntu?

---

