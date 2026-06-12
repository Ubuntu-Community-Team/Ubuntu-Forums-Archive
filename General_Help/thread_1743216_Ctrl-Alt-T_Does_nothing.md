---
title: "Ctrl-Alt-T Does nothing"
date: 2011-04-29
forum: General Help
---

### Post by J.L.C. on 2011-04-29
I upgraded to 11.04 (64-bit) yesterday (from 10.04) and have been trying to get used to Unity.

I think the keyboard shortcuts will be really helpful for workflow, but - only if they work.

I have logged out, logged in, rebooted, powered off completely, and restarted compiz several times. But CTRL-ALT-T does not open a terminal or anything else. It only seems to bring up the Global Menu options for any window that's open.

Due to the general glitchy-ness of the launcher, being able to get to a terminal efficiently would go a long way.

Anyone else having this problem?

Can anyone suggest a fix or what I should look at?

---

### Post by r-senior on 2011-04-29
It was working for me in the beta, but not now I've just upgraded.

Easy enough to get it working. Fire up "Keyboard Shortcuts" and add Ctrl-Alt-T as the shortcut to "Run a Terminal".

EDIT: What's glitchy about the launcher BTW?

---

### Post by J.L.C. on 2011-04-29
> **r-senior said:**
> It was working for me in the beta, but not now I've just upgraded.

Easy enough to get it working. Fire up "Keyboard Shortcuts" and add Ctrl-Alt-T as the shortcut to "Run a Terminal".

EDIT: What's glitchy about the launcher BTW?

Thanks for the quick reply!

I tried the work-around, but it still won't work. I went into 'keyboard shortcuts' and Ctrl-Alt-T was already listed for "Run a Terminal", so I cleared that and entered Ctrl-Alt-T manually.

But, after exiting 'keyboard shortcuts' it still won't launch a terminal window.

**EDIT:** I've gotten around it by creating a custom command called "Terminal", with the command 'gnome-terminal' and the shortcut Ctrl-Alt-T

So that's working now :)



As for the launcher:
On my system, the launcher doesn't always want to show up and often clicking the icons doesn't launch the application.

I also just noticed that the panel on my 2nd display is slowly creeping off the screen to the right. Everything was there when I first booted up, but now only the weather-indicator is visible, all the other indicators have crept off the screen. All is well on the primary display though. I wish we could remove the panel from the 2nd display entirely.

---

### Post by mc4man on 2011-04-29
If you have compizconf-setting-manager installed then open it up (ccsm) and check if the gnome Compatibility plugin is enabled.
If so then open up and ck. the binding - 
It doesn't have to be filled in (though you can do so), just not showing 'disabled'
see screen, it was empty (but working), I filled in ( and still works

If you go into ccsm be very careful about enabling and or disabling some plugins if tempted - some will unset all the plugins and you'd have to re-enable them, a bit of a pita

After changing anything in ccsm usually good to do a log out/in

---

### Post by J.L.C. on 2011-04-29
Thanks!

I went into to Gnome Compatibility, and sure enough - it was disabled.

---

### Post by phoenixzee on 2012-09-04
Great. Worked for me fine.:p

---

