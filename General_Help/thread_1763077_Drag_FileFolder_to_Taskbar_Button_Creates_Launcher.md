---
title: "Drag File/Folder to Taskbar Button Creates Launcher, Not Bring Folder to Foreground"
date: 2011-05-20
forum: General Help
---

### Post by OzzyFrank on 2011-05-20
After upgrading to 11.04, I noticed something strange, being that when I want to drag a file or folder from one Nautilus folder window to another which is not visible, I can no longer hold the item over said folder's taskbar button and wait for it to appear. It just shows the + for copy, and when I let go (which I have no choice but to eventually do), it creates a launcher to that item (I assume it's doing that, and not actually copying there, but the + has me unsure).

I've looked in Nautilus's preferences to see if this is some new behaviour that I can revert back to, but could find nothing there.

I'm of course using the Classic desktop with bottom panel being the taskbar. If you know how I can rectify this, please let me know, as the times I would want to create a file or folder launcher without the usual hassle would be rare, but I am constantly dragging stuff from one folder to another, and it would be a real pain to have to line up source and destination folders each time. Many thanks in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Try using a different file manager like PCMANFM

---

### Post by shashanksingh on 2011-05-20
> **OzzyFrank said:**
> After upgrading to 11.04, I noticed something strange, being that when I want to drag a file or folder from one Nautilus folder window to another which is not visible, I can no longer hold the item over said folder's taskbar button and wait for it to appear. It just shows the + for copy, and when I let go (which I have no choice but to eventually do), it creates a launcher to that item (I assume it's doing that, and not actually copying there, but the + has me unsure).

I've looked in Nautilus's preferences to see if this is some new behaviour that I can revert back to, but could find nothing there.

I'm of course using the Classic desktop with bottom panel being the taskbar. If you know how I can rectify this, please let me know, as the times I would want to create a file or folder launcher without the usual hassle would be rare, but I am constantly dragging stuff from one folder to another, and it would be a real pain to have to line up source and destination folders each time. Many thanks in advance.

I have the exact same problem.

[Read this]("http://ubuntuforums.org/showthread.php?t=1757053")

Try ```
compiz --replace
``` and then check out if it works.
I also reported a bug to launchpad, you could add to that if its the same..

[The reported bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/783926")

---

### Post by OzzyFrank on 2011-05-20
Yes, I tried **Thunar**, between it and Nautilus windows, and between Thunar ones, to no avail. But **[COLOR="Red"]compiz --replace[/COLOR]** did the trick, until the next reboot I assume. Thanks for that tip. I added a comment on the bug report, and marked it as a bug.

So, not sure if I should marked this as solved, but being it isn't a hidden setting, but a bug by the looks of it, I think I should. That way, others experiencing the same problem will be compelled to come here, and can at least run the command they find here to fix the problem for each session.

And please think about adding to the bug report, as more voices mean things get fixed quicker. If you haven't already got a Launchpad account, click the bug report link about and join. Cheers.

---

### Post by shashanksingh on 2011-05-21
Thanks OzzyFrank.

I was getting lonely with the bug :)

---

