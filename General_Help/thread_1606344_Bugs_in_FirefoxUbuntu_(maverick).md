---
title: "Bugs in Firefox/Ubuntu? (maverick)"
date: 2010-10-26
forum: General Help
---

### Post by orrie on 2010-10-26
**Description of issue 1:** 
Randomly left-clicking in a textarea/input-field results in paste from things that I've copied.

**Description of issue 2:**
When left-clicking on a link, a new tab opens with the link.


These two issues are quite annoying, and I'm convinced that this isn't new features, but bugs.
True?
Solutions to this?

---

### Post by wilee-nilee on 2010-10-26
> **orrie said:**
> Description of issue 1:
Randomly right-clicking in a textarea/input-field results in paste from things that I've copied.

Description of issue 2:
When leftclicking on a link, a new tab opens with the link.


These two issues are quite annoying, and I'm convinced that this isn't new features, but bugs.
True?
Solutions to this?

First one is going to happen no matter what, it is the nature of using the right click to copy and paste.

The second one makes no sense. If your right handed and have your mouse set up to have the left click to open something what are you actually expecting.

FF has a edit-preferences you might look through them to make sure it is set to your liking.

---

### Post by philinux on 2010-10-26
1. When I right click in a text or input area I get the usual context menu.

---

### Post by pqwoerituytrueiwoq on 2010-10-26
have you checked firefox's settings?
edit->preferences tabs

i usually have some problems with firefox until i disable the ubuntu modifications addon
(minor things i can not recall)

it is possible you are middle clicking instead of right clicking?

---

### Post by orrie on 2010-10-28
> **philinux said:**
> 1. When I right click in a text or input area I get the usual context menu.

Pardon me, I was saying right when I actually ment left.


The strange thing here is that I didn't have this problem until I installed maverick.

---

### Post by orrie on 2010-10-28
> **pqwoerituytrueiwoq said:**
> have you checked firefox's settings?
edit->preferences tabs

i usually have some problems with firefox until i disable the ubuntu modifications addon
(minor things i can not recall)

it is possible you are middle clicking instead of right clicking?

It is possible that I'm middle clicking yes.
I'm clicking on the area to get it in focus.

---

### Post by chopstickkk on 2010-11-20
> **orrie said:**
> **Description of issue 1:** 
Randomly left-clicking in a textarea/input-field results in paste from things that I've copied.

**Description of issue 2:**
When left-clicking on a link, a new tab opens with the link.


These two issues are quite annoying, and I'm convinced that this isn't new features, but bugs.
True?
Solutions to this?

AH! The same problem! This is DEFINITELY a bug in Maverick. I've just done a clean install of 10.10 after my 10.04 went haywire and I've been experiencing this problem not only in Firefox but in Nautilus too.

I'm having both of those issues exactly the same as you describe. I've no idea how to repeat this as it's seemedly random but hopefully someone more technically minded can solve this!?!? It's very very annoying and thinking of downgrading.


Can the topic title of this thread be changed to 'Bugs in Maverick' since it seems to be a global problem?


I think more people would take notice then or perhaps are having the same problems.

John.

---

### Post by chopstickkk on 2010-11-20
Also when I left click on a tab sometimes it just disappears!!!

John.

---

### Post by efflandt on 2010-11-20
These things are not a general issue.

1: It may have to do with settings (whether to remember data for form fields based name of the field).  Or in X, the middle mouse button, or left and right together, or pressing on the scroll wheel, which is the 3rd button (not rolling it), has traditionally pasted "highlighted" text (which may not be what is in the clipboard).

I have never had trouble with clipboard data automatically appearing in a field.  In a forum message window when I left click it.  I typically use Windows like Ctrl+V to paste text (if not right click mouse menu to paste).

When I have used Chromium I have had a particular problem pasting links containing spaces, because Chromium pastes such links with actual spaces which breaks them at the first space.  Firefox does it right by passing %20 place holders for spaces, so they are properly interpreted by the forum software. 

2: Whether to follow a link or open a separate tab is generally controlled by specifics of the link tag (which you do not see unless you view source).  For example links in Ubuntu forums seem to be configured to open a new tab.  So if you follow a link from the forum to check something out and possibly download a file from there, you can quickly get back to where you were by simply closing the tab.  If you want a choice of whether to follow a link, open it in a new tab, or new window, you can right click a link.

---

### Post by chopstickkk on 2010-11-22
Perhaps I am hitting the scrollbar on the right of my touchpad accidentally for the strange pasting behaviour. How do I check what buttons/keys are sent? Perhaps if I knew that I could reproduce.

But what about left clicking a tab making it disappear?
And things randomly opening in new tabs behind?
And the fact that it happens in Nautilus also?

It's just strange that it only happened since I've freshly installed Maverick. Lucid was fine.

---

### Post by chopstickkk on 2010-11-22
[https://bugs.launchpad.net/ubuntu/+bug/636720/comments/12](https://bugs.launchpad.net/ubuntu/+bug/636720/comments/12)

There seems to be a workaround here for anyone who's following this thread. Hope it helps.

---

### Post by trinitydan on 2010-12-20
Is that relevant to the tabs disappearing when I primary click on them?  I tend to open links in a new tab and when they are done loading view them so it is getting terribly annoying to have pages load and not even get to look at them before the tab disappears.  Any help would be greatly appreciated.

---

