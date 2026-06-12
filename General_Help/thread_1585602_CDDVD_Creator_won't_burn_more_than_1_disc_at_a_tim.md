---
title: "CD/DVD Creator won't burn more than 1 disc at a time"
date: 2010-09-30
forum: General Help
---

### Post by skunkbad on 2010-09-30
We just installed 10.4, and everything seems to work as needed, but we need to burn a bunch of CDs, and we are having problems with the built-in CD/DVD Creator (same as Brasero?).

What happens is, we say we want to burn more than one disc, and after the first disc is burned, it tells us that we need to eject the burned disc, because it couldn't eject it on its own. That's cool, we eject it, and it says if we want to burn more than one disc, to insert another disc, so we insert it. After we insert it, it's like the computer didn't know it was supposed to burn another. It asks us what we want to do. It shouldn't ask us what we want to do, because it should know that we were inserting another disc so that we could keep burning multiple discs.

Another thing I don't understand is, we can eject the disc from the File browser, but why does the CD/DVD Creator say it can't do it. How stupid is that?

I don't mind installing another CD/DVD burning software product if that's what it takes, but unless I'm doing something wrong (and I don't think I am) I'd think that this was a pretty basic task that Ubuntu would be able to handle.

---

### Post by gordintoronto on 2010-09-30
When the computer asks what you want to do on the second disc, just Cancel. Brasero should still be running, and you should be able to click on "burn."

What optical disk drive do you have? I've never seen a problem with Eject, but I believe you are having such a problem.

Some people really like K3B instead of Brasero.

---

### Post by skunkbad on 2010-09-30
> **gordintoronto said:**
> When the computer asks what you want to do on the second disc, just Cancel. Brasero should still be running, and you should be able to click on "burn."

What optical disk drive do you have? I've never seen a problem with Eject, but I believe you are having such a problem.

Some people really like K3B instead of Brasero.

The problem with that is that the dialog box that asks what I want to do with the new disc won't let me click on any of the buttons until I close out the one that said to put in another disc. It's just locked up. I've got two pretty generic DVD drives, both Sony, and neither works better than the other.

---

### Post by skunkbad on 2010-10-01
I ended up trying gnomebaker, but it doesn't allow for burning more than one at a time. K3B ended up being perfect for our needs. I'll probably never know why the built-in burner didn't eject and burn multiple copies, but I've seen a couple other threads that show that I'm not the only one having problems. It's too bad, but someday Ubuntu will make it perfect (I hope).

---

### Post by intel352 on 2011-07-13
Just a note, under Ubuntu 11.04, I'm having the same issue.
When burning multiple discs, it won't eject on it's own. I've burned solo discs in the recent past and it didn't have an issue there, so I think it's something to do with how the app is programmed.

When inserting a new disc, Ubuntu pops up the autoplay prompt for the blank dvd. The first time this occurred, I was able to cancel past that without any issue. Any subsequent time it's occurred, the box is locked up preventing me from cancelling out, so my only recourse is to cancel the new DVD burn, which is quite annoying.

Ultimately Ubuntu should be smart enough to know that a program is using the disc drive, and not prompt...

I've attempted disabling autoplay for blank dvds, which indeed prevents the autoplay dialog from popping up, but the DVD creator app does notice the new disc has been inserted, and thus does not continue.


Shame this issue has persisted into a new release of Ubuntu...

---

### Post by raffen on 2012-09-23
I have the same problem in 12.04. 

"Brasero: Another copy will start as soon as you insert a new writable disc. If you do not want to burn another copy, press 'Cancel'."

Nothing happens when the new disk is inserted.  Pretty annoying.

---

