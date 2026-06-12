---
title: "&quot;Places&quot; menu items tied to rhythmbox. . ."
date: 2011-01-25
forum: General Help
---

### Post by jiminoregon on 2011-01-25
I have installed Ubuntu 10.10, and it was doing well as I learned to do the tweaks for internet, etc.  However, recently when I click on an item in the "Places" menu, all of the items in the top two "boxes" opened Rhythmbox instead of opening the item listed.  I removed Rhythmbox, and now I get the following error message:

[ATTACH]181947[/ATTACH]

Haven't tried to use attachment before so I hope this works. 

Also, hope someone can give me a clue as to how to change this. I have been tinkering with various Linux distros for some time but decided to get serious about getting one to work for me. This version of Ubuntu seems to be pretty good, but most of the process is still greek to me.

---

### Post by Verbeck on 2011-01-25
its problem with file associations..
right click a folder on your desktop (create one if you don't have) > open with other application > file browser > check 'remember this application......"

hope that helps

---

### Post by cgroza on 2011-01-25
Right click on a folder on the desktop, select open with, select your file browser from the list and make sure that the check box at the bottom is ticked and hit Open.

Hope that helps.

---

### Post by tredegar on 2011-01-25
Good answer Verbeck, and I'm sure it'll solve jiminoregon's problem, but what puzzles me is _why_ is this such a common problem in the ubuntu forums?

Why is ubuntu so broken? This doesn't seem to be a problem with any other distro.

Any ideas?

---

### Post by Verbeck on 2011-01-25
> **tredegar said:**
> 
Any ideas?
looks like its gnome related
[https://bbs.archlinux.org/viewtopic.php?id=72741](https://bbs.archlinux.org/viewtopic.php?id=72741)
[http://forums.debian.net/viewtopic.php?f=6&t=47682](http://forums.debian.net/viewtopic.php?f=6&t=47682)
[https://bugzilla.redhat.com/show_bug.cgi?id=473320](https://bugzilla.redhat.com/show_bug.cgi?id=473320)[URL="https://bugs.launchpad.net/libgnome/+bug/35997"]
[/URL]

---

### Post by garvinrick4 on 2011-01-25
I can reproduce this effect by right clicking on music directory and opening with lets say vlc  that is already in menu. 
It seems to make it default for nautilus to open in vlc even though you have not gone to menu to open and check box 
to make default for this application. So now I get directories to open in wrong application by default.
 #I choose now to open music player and follow path to music desired until fix is produced.

---

### Post by mc4man on 2011-01-25
> me is why is this such a common problem in the ubuntu forums?

It's a nautilus 'bug' that won't likely be fixed. The reason the default is changed is because the "Remember this...." option from the 'other application' menu is enabled and that has the effect of setting a new default whether used on folders or files.

In ubuntu that option is enabled by default, so -  many people don't notice or misunderstand what it will do.

I spent close to 5 months trying first to get the bug fixed, then switching to at least disable the option by default as a way to lessen the chance of switching.
The patch to nautilus was finally accepted and applied to not enable the option, unfortunately, even though this was filed on and intended for maverick the patch was applied to  nautilus in  natty only.
(where ironically it may ultimately may be not needed if natty goes to the 2.9X or 3 version of nautilus.

 Best thing to do is disable that option when using the 'other application' menu

Here is the semi open 2nd bug on the changing of default enabled, possibly if enough complained then they might consider appling to 10.10 or if an update to nautilus for 10.10 came about then remember to add the patch.

[https://bugs.launchpad.net/nautilus/+bug/662194](https://bugs.launchpad.net/nautilus/+bug/662194)

---

### Post by tredegar on 2011-01-26
> It's a nautilus 'bug' that won't likely be fixed.
Thanks for the explanation, and your efforts to get it fixed.

---

### Post by jiminoregon on 2011-01-26
:P Thank you all for the prompt replies.  The solution given by Verbeck did the trick, and Garvinrick4's explanation is similar to what I had probably done to cause the problem, and, if I desist from that behavior will probably prevent its happening again. Again, thanks to you all.

---

### Post by jiminoregon on 2011-01-26
How do I mark this as solved?  Or is that someone else's chore?

---

### Post by plucky on 2011-01-27
> **jiminoregon said:**
> How do I mark this as solved?  Or is that someone else's chore?

[color=red][Thread Tools][/color] dropdown menu at top of page.

---

### Post by bebopiiam on 2011-03-16
Hi.  I just had this problem pop up after installing VLC.  I used either Synaptic or Ubuntu Software Center to do the install and afterward ~/.local/share/applications/mimeapps.list looks like:
[Added Associations]
inode/directory=vlc.desktop;totem.desktop;

Reseting it to 
inode/directory=nautilus-folder-handler.desktop;
fixed the problem but this happened once before.

There's a thread on Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > General Help titled '[B]Panel Places menu broken' and I'm cross-posting here to let you know when and how the problem occured.


[/B]

---

