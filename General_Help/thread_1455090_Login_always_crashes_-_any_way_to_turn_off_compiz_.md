---
title: "Login always crashes - any way to turn off compiz before login?"
date: 2010-04-15
forum: General Help
---

### Post by NoBugs! on 2010-04-15
After turning on one of the compiz effects (reflection), everything froze... After reboot, I can't log in, it shows the desktop but then completely freezes again. How do you turn off the compiz effects at commandline / before login??

---

### Post by plucky on 2010-04-15
> **NoBugs! said:**
> After turning on one of the compiz effects (reflection), everything froze... After reboot, I can't log in, it shows the desktop but then completely freezes again. How do you turn off the compiz effects at commandline / before login??

On the login screen at the bottom,one of the boxes shows **Gnome**.If you click on that box you should be able to select **Failsafe Gnome**.

That should get you to the Desktop.

Good Luck

---

### Post by NoBugs! on 2010-04-15
I had tried that, but it didn't work. Here's how I fixed it:

Instead of logging in, went to CTRL-ALT-F2 to log in to terminal,
then moved the gconf to a different folder.

mv ~/.gconf/apps/compiz/ ~/.gconf/apps/.old.compiz

This reset the settings to default and it's working again:)

---

### Post by plucky on 2010-04-16
> **NoBugs! said:**
> I had tried that, but it didn't work. Here's how I fixed it:

Instead of logging in, went to CTRL-ALT-F2 to log in to terminal,
then moved the gconf to a different folder.

mv ~/.gconf/apps/compiz/ ~/.gconf/apps/.old.compiz

This reset the settings to default and it's working again:)

Well Done

Can you please mark the thread as [color=blue]Solved[/color] using the Thread Tools Button at the top of the page.

---

