---
title: "Unity - Blank Desktop"
date: 2011-04-30
forum: General Help
---

### Post by John Vance on 2011-04-30
I have an i5-650 with integrated graphics.

Unity appears to not start.  After logging in I have a completely empty desktop.  No top bar.  No side bar.  Nothing except a background image.

I installed Unity-2d and it works as expected.  Ubuntu Classic starts up fine.

What log files should I be looking at?  What diagnostic steps should I take?

---

### Post by John Vance on 2011-04-30
Okay, I had a cheapass Radeon HD5450 lying around so I slapped it in.  Booted to Ubuntu Classic, fired up jockey and installed the proprietary drivers.  Rebooted to Ubuntu Classic and it was busted.  Ctrl Alt T, kill -9ed my way out back to GDM, logged back in as Ubuntu Classic (No effects).  All gl acceleration was on.  Compiz was NOT installed.

Let me repeat that.  A required dependency for Unity was NOT installed during the upgrade.  There were compiz-plugins installed, but the compiz and compiz-gnome packages were not installed.

Installed compiz.  Logged out, logged in to "Ubuntu" session, and there's Unity.  If I'm feeling like wasting more time on this I will remove the Radeon card and see if the problem was just that compiz was missing.

Now for the pure joy of seeing if my 9.04 and Windows XP partitions will still start up with the new video card. :guitar:

---

### Post by John Vance on 2011-05-01
You know, I'm sure tons of other people are having similar problems, and my limited search skills didn't turn up anything similar.  It would be nice if someone with some insight at least dumped a few links to more relevant threads in here for other search-challenged folks to find.

I'd also like to point out that were I not a software developer myself and therefore a professional problem solver, then this problem, combined with Grub's insistence on changing my drive boot order every freaking upgrade, and the sound of crickets in this forum in response to my queries, would have sent me straight back to Windows 7.

---

