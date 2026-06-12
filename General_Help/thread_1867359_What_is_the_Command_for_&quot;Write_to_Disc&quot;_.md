---
title: "What is the Command for &quot;Write to Disc&quot; (ISO Images) in Nautilus 3.2/Ubuntu 11.10?"
date: 2011-10-22
forum: General Help
---

### Post by OzzyFrank on 2011-10-22
Hi there. I've looked everywhere, but the little info I found on what the actual command Nautilus uses for its "**[COLOR="Red"]Write to Disc...[/COLOR]**" context menu option for ISO disc images is outdated. **nautilus-cd-burner** no longer does this, apparently, so I am at a loss, and would like to change the default option for double-clicking ISOs to that, as Brasero has gone from popping up when it decides to (the record was 15 double-clicks!) to now not managing to appear at all after the 11.10 upgrade.

So, "**[COLOR="Red"]Write to Disc...[/COLOR]**" works fine, so I am glad it reappeared there, as a few Ubuntu versions back it disappeared, probably when Brasero became the default. Anyway, while it is accessible via a right-click, I would like to set it as the default for double-clicks and, since it isn't in the list of suggested ***Open With*** applications, need the command to do this. Obviously, there has to be a command behind it, so your wisdom on this would be appreciated.

---

### Post by crdlb on 2011-10-22
"Write to Disc" is provided by a nautilus extension that ships with brasero. The only difference between it and running brasero is that the operation runs inside nautilus using libbrasero-* instead of in brasero itself. It looks like brasero is not terminating correctly, so it will not re-launch unless you kill the process. That is a bug which should be filed if it isn't already.

---

### Post by OzzyFrank on 2011-10-22
I thought it may have been something like that, but wasn't going to speculate, since the default Brasero app that pops up for ISOs and the Write to Disc one aren't exactly the same (with the latter resembling the old Write to Disc of Nautilus).

So, is there any way to specify that via Open With, as Brasero is in the list and already the default, which isn't what I want.

As for the Brasero bug, yeah made a bug report way back, then a few months later I was informed it had been removed or abandoned or whatever (read: IGNORED), due to "lack of movement". Like, what else is there to report? That it got worse and worse? So I've given up on Brasero, since filing bugs reports is obviously a waste of time, and nobody was looking into rectifying this.

---

### Post by crdlb on 2011-10-22
The two dialogs look practically identical to me.

I have found the source of the bug if you want to file it again: When brasero is run with an image on the command line, brasero_cli_apply_options calls brasero_app_open_uri, which runs the image burning dialog. After that dialog is closed, brasero_cli_apply_options calls brasero_app_run_mainwin, even though there is no main window in this code path. The result is that the process hangs, preventing brasero from being reopened.

---

