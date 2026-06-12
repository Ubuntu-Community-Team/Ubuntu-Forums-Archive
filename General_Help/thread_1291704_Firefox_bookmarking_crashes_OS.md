---
title: "Firefox bookmarking crashes OS"
date: 2009-10-15
forum: General Help
---

### Post by rpaskudniak on 2009-10-15
Ubuntu 9.04

Greetings.

A few hours ago, I was browsing in FireFox and added a bookmark to the wrong folder.  I tried to fix this, not by clicking on "Organize Bookmarks" but by direct manipulation of the bookmark item in the drop-down menu.

The OS stopped responding to keyboard and mouse clicks, although the mouse cursor still responded to movement.  I rebooted by pressing the Power button and waiting 60 seconds for the host to reboot.  The "Rebooting in 60 seconds" window came up but I could not interact with it.

Although my login ID is privileged to be able to run sudo, I ***was*** running in non-privileged mode.  Whatever bugs Firefox 3.0.14 may carry, **_[SIZE="3"]nothing[/SIZE]_** should allow a non-root user to crash the system like that!  Somehow, Firefox bypassed some security that should be in place at the hardware level - modified a memory segment that it should [probably] have been unable to access in user mode.

This is a _security issue_, with the implication that Firefox could be manipulated into performing evil operations at the kernel level, inasmuch as it already has the capability to crash the kernel.

Replicate by following steps:
[LIST=1]
[*]Add a bookmark to the main bookmarks folder.
[*]Click on the Bookmarks menu
[*]Click/drag that new bookmark into one of the folders in the Bookmarks menu.
[/LIST]
Your OS has just crashed and will not acknowledge anything you do (other than moving the mouse).

Has anyone else run into this?  Any patch existing to fix this?  If someone has Ubuntu 9.10, can you please see if the same condition prevails?

Thanks much!

---

### Post by nvikram on 2009-10-15
> **rpaskudniak said:**
> Ubuntu 9.04

Greetings.

A few hours ago, I was browsing in FireFox and added a bookmark to the wrong folder.  I tried to fix this, not by clicking on "Organize Bookmarks" but by direct manipulation of the bookmark item in the drop-down menu.

The OS stopped responding to keyboard and mouse clicks, although the mouse cursor still responded to movement.  I rebooted by pressing the Power button and waiting 60 seconds for the host to reboot.  The "Rebooting in 60 seconds" window came up but I could not interact with it.

Although my login ID is privileged to be able to run sudo, I ***was*** running in non-privileged mode.  Whatever bugs Firefox 3.0.14 may carry, **_[SIZE="3"]nothing[/SIZE]_** should allow a non-root user to crash the system like that!  Somehow, Firefox bypassed some security that should be in place at the hardware level - modified a memory segment that it should [probably] have been unable to access in user mode.

This is a _security issue_, with the implication that Firefox could be manipulated into performing evil operations at the kernel level, inasmuch as it already has the capability to crash the kernel.

Replicate by following steps:
[LIST=1]
[*]Add a bookmark to the main bookmarks folder.
[*]Click on the Bookmarks menu
[*]Click/drag that new bookmark into one of the folders in the Bookmarks menu.
[/LIST]
Your OS has just crashed and will not acknowledge anything you do (other than moving the mouse).

Has anyone else run into this?  Any patch existing to fix this?  If someone has Ubuntu 9.10, can you please see if the same condition prevails?

Thanks much!

I haven't exactly had you're problem, but if you want to refresh firefox, all you have to do is delete your .mozilla folder thats located in your home folder. You can do this by 

```
rm .mozilla
```

Then re-open firefox, you should have a clean slate with no bookmarks but it shouldn't be messed up. try you're bookmark thing again. It may work. 

Hope this helps!

---

### Post by rpaskudniak on 2009-10-15
nvikram, You missed my point.

Whether my bookmarks are messed up or not is not the problem. (As it happens, they are not messed up at all.)  The problem was that the attempt to manipulate the bookmark crashed the whole blessed server, forcing a reboot.  There is a bug in firefox if it tries to poke something it should not poke.  It is a kernel security bug if it succeeds.

---

### Post by cdenley on 2009-10-15
> **rpaskudniak said:**
> nvikram, You missed my point.

Whether my bookmarks are messed up or not is not the problem. (As it happens, they are not messed up at all.)  The problem was that the attempt to manipulate the bookmark crashed the whole blessed server, forcing a reboot.  There is a bug in firefox if it tries to poke something it should not poke.  It is a kernel security bug if it succeeds.

Resetting your profile will probably prevent you from experiencing this problem. If it is indeed a firefox bug which is only present with some specific condition of your profile and not simply the result of a corrupted profile, then this would be a difficult bug to get to the bottom of, but this forum isn't for bug reporting (especially for beta releases).
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
If you want to find out if this problem effects everyone, backup your profile, delete it, then see if you can reproduce your problem. Firefox causing your GUI to become unresponsive does not mean you have a kernel security bug.

---

### Post by rpaskudniak on 2009-11-20
Folks,
After upgrading to Ubuntu 9.10 and Firefox to 3.5 along with that ride, the problem has gone away.

I will mark this thread [SOLVED] but it isn't, really.  It has merely gotten out of my way..  Iwill never know if the bug was in firefox or (IMO now) more likely, in Gnome.

---

### Post by J1m on 2009-12-07
I'm having this exact same issue.

I tried to drag a bookmark to the desktop when this happened.  I'm running firefox 3.5.5 on Karmic 9.10

It's pretty much a fresh install.  I'll try to delete the .mozilla folder and see if it fixes the issue.

Jim

---

### Post by J1m on 2009-12-07
Right,

Deleting the .mozilla folder has done nothing.  When I try dragging a bookmark on to the desktop, the same thing happens as described above.

However... despite not being able to click on anything else when the system has crashed, I can still type and click within firefox itself.  So I tried repeating the procedure and the issue resolved itself.

So, I can drag a bookmark on to the desktop and the system will crash (except firefox) then I can just drag a bookmark around within the bookmarks menu and the crash goes away.

Weird

---

### Post by rpaskudniak on 2009-12-09
J1m,
After posting my [SOLVED] remarks, the problem seemed to happen again, with the my old symptoms, not as you describe. ](*,)  I did not try to undo anything, however; it resolved itself by waiting a few minutes.  (I had to step away for another reason.)  It seemed to be just a very delayed response by the GUI. Not desirable at all and a possible misbehavior in Gnome. :oops: Still, not as bad as crashing my whole GUI.

I should post *this* question in a different thread: What to do when the GUI crashes.  Lemme think of a way to word that in 1,000 words and I'll ask the community.  (Mr. Concise, that's me.. NOT  :biggrin:  )

---

### Post by The Bright Side on 2009-12-09
It's funny, I have another bookmark problem with 9.10 and ff 3.5: when I select "bookmark this page", the bookmarking dialog that comes up is corrupted. When I click on the icon next to the bookmarks to expand the tree, the upper third of the window goes blank, parts of the scrollbar aren't drawn and the actual bookmark tree doesn't respons when you scroll or click on it. Basically, the graphics either disappear or freeze, while the main functionality of the bookmarking dialog remains working.

It's not a biggie, I just put my bookmarks in the root of the tree and then move them in "Organize Bookmarks", but I was wondering if anybody else encountered this and found a fix?

---

