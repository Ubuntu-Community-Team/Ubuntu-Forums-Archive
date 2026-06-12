---
title: "Trash bin inaccessible by nautilus"
date: 2010-09-28
forum: General Help
---

### Post by Doctadrez on 2010-09-28
I get the error: Sorry, could not display all the contents of "trash": Operation not supported.

Of course I know I can remove all the contents of the trash directly via ~/.local/share/Trash/ however, I'd rather have Ubuntu the work the way it was intended.

I've tried opening Nautilus using the gksu command, but the problem persists.

As per another post, I also tried a fsck on the partition, and no errors were returned.

Anyone have any luck in solving this?

---

### Post by uRock on 2010-09-28
Can you try to delete using nautilus again and take a screenshot of the error message?

---

### Post by Doctadrez on 2010-09-28
Deleting files appropriately places the files in the trash folder (when I navigate to it), however opening the location via the usual methods doesn't.

It doesn't even try to open with nautilus, when clicking on the trashcan. It attempts to open in gedit.  [Screen Here]("http://imgur.com/IpzNG")

When I try to click on the Trash under places (or typing in trash:///) in nautilus I get [This Error]("http://imgur.com/XIirn.png").

Even the "Empty Trash" option in the right-click menu on the trashcan is greyed out.

---

### Post by uRock on 2010-09-28
Have you by some chance uninstalled the gnome-applets listed in the screenshot below?

---

### Post by Doctadrez on 2010-09-28
That's a negative. I have the same version as you :(

---

### Post by MadJestyr on 2010-11-14
Anyone figure this out, I have a new install of 10.10 on my moms system and I am having the same problem.

---

