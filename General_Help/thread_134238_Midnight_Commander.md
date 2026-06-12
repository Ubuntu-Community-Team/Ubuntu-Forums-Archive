---
title: "Midnight Commander"
date: 2006-02-21
forum: General Help
---

### Post by dmh-bidlah on 2006-02-21
I recently started using the GNU Midnight Commander, or mc in the repositories, a great console file manager.
Now I have 2 questions:

[LIST=2]
[*]I have seen it is possible to get the blue background semi-transparent in a terminal emulator, so you can see your background image. I have not yet managed to for this in gnome-terminal, I can get other terminal applications to transparent but mc seems to insist on repainting the screen so the blue background remains.
[*]When I start mc from the virtual terminal (CTRL-ALT-F1), then initially it looks fine but as I open some menus the screen gets really weird, some places are not erased correctly etc. This really sucks because it would be great to use it in a virtual terminal.
[/LIST]

Thanks for any help! :KS

---

### Post by xinix on 2006-02-21
Updating MC to the version in backports will fix the issue with the screen getting all screwy.  I love MC but this bug was killing me.

---

### Post by az on 2006-02-21
[QUOTE=xinix]Updating MC to the version in backports will fix the issue with the screen getting all screwy.  I love MC but this bug was killing me.[/QUOTE]
Yeah, tell me about it.  It was a UTF (character set) bug.

AFAIK, if ncurses paints the screen blue, it is opaque.  Since the terminal program is responsible for transparency, and it only shows the terminal background as transparent, you cannot make the blue background transparent (yet).  You can configure mc to paint a black background which should be transparent.....

---

### Post by glave on 2006-02-21
I just started using mc as well, but I've hit a question I've yet to figure out. I know I can have it view the inside of rar files and then have it copy the contents over to the other pane, but is it possible to just have a rar file highlighted and tell it to extract it to the other pane (or just extract at all)?

---

### Post by dmh-bidlah on 2006-02-22
[QUOTE=xinix]Updating MC to the version in backports will fix the issue with the screen getting all screwy.[/QUOTE]
Great to hear that!
But how do I install the backports version?

---

### Post by xinix on 2006-02-22
[QUOTE=dmh-bidlah]Great to hear that!
But how do I install the backports version?[/QUOTE]
Edit "/etc/apt/sources.list"  towards the bottom of the file you'll see the lines that reference backports.  Just uncomment them and run "apt-get update" or fire up synaptic and hit reload.

I was playing around with this and, well, the bug is mostly fixed.  The screen stays clean if you use it as your regular user and if you "sudo mc".  But if you run it while in "sudo -i" (which leaves you in root mode for more than one command) the screen does the same old thing.  Dunno if there is a fix for that.

---

### Post by dmh-bidlah on 2006-02-23
I don't have my original sources.list file anymore, could someone just post the lines here?

---

### Post by xinix on 2006-02-23
[QUOTE=dmh-bidlah]I don't have my original sources.list file anymore, could someone just post the lines here?[/QUOTE]

Here:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

