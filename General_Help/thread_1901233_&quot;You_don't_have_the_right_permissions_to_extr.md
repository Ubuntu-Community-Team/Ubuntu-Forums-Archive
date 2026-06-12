---
title: "&quot;You don't have the right permissions to extract archives in the folder&quot;"
date: 2011-12-28
forum: General Help
---

### Post by BHTX84 on 2011-12-28
Major glitch here. If I attempt to drag anything from a compressed file to a location in PCManFM, I get this error:

[IMG]http://img577.imageshack.us/img577/8665/pcmanfmerror.png[/IMG]

And that&#8217;s it. I can&#8217;t close the dialog, as none of the buttons are responsive. I can&#8217;t close it with CTRL+W either. I can&#8217;t switch to another window. I can't do anything. The entire system just sits there with a stupid jacked up cursor, and I'm forced to hold the power button on my laptop until it shuts off so that I can turn it back on again. I don't think the hard drive likes this very much.

I tried opening the window as root, only to end up with yet another error, simply stating "Permission denied". What am I supposed to do?

---

### Post by mikewhatever on 2011-12-28
You can file a bug report as well as refrain from triggering the bug.

---

### Post by utnubuuser on 2011-12-28
the bug is in the error report... see the paranthesis' "" - an obvious syntax booboo...
lol

---

### Post by BHTX84 on 2011-12-29
Anyway, after about 24 hours of Lubuntu, I ended up going with another distro. It was just far too buggy. I was running into too many issues with it. I grew tired of having to "fix" computers all my life for friends and family for the same exact reason every time, over and over again (MS Windows). I started using Ubuntu with 10.04, and was pretty happy with it. When I started trying it out on other people's computers, 11.04 had just arrived. Every single one of them hates Unity, and so do I. So, I was looking for something that would not only help illiterate users feel more at home, but a distro that also worked well "out of the box". Lubuntu just isn't it. It's definitely a light OS though. Probably the lightest I've ever used since win98. However, it hasn't matured enough yet I guess.

---

### Post by 666f6f on 2012-01-27
I just encountered this problem. I switched over to a real tty (I entered Ctrl+Alt+F1) and typed ```
killall file-roller
```. That doesn't fix the problem, but at least unblocks the UI.

It seems like a [file-roller]("http://fileroller.sourceforge.net/")/[PCManFM]("http://pcmanfm.sourceforge.net/") integration bug. After unblocking the UI, whenever I double click a desktop folder or whenever I launch PCManFM, a new tab is created (if a PCManFM window already exists) instead of a new PCManFM window. Weird..

---

### Post by Cheesemill on 2012-01-27
> **BHTX84 said:**
> Anyway, after about 24 hours of Lubuntu, I ended up going with another distro. It was just far too buggy. I was running into too many issues with it. I grew tired of having to "fix" computers all my life for friends and family for the same exact reason every time, over and over again (MS Windows). I started using Ubuntu with 10.04, and was pretty happy with it. When I started trying it out on other people's computers, 11.04 had just arrived. Every single one of them hates Unity, and so do I. So, I was looking for something that would not only help illiterate users feel more at home, but a distro that also worked well "out of the box". Lubuntu just isn't it. It's definitely a light OS though. Probably the lightest I've ever used since win98. However, it hasn't matured enough yet I guess.

You could try Xubuntu.

I use XFCE across several distros and have never had any problems with it.
It's only slightly heavier than LXDE and you still have the old Gnome 2 look and feel. It uses GTK so all of the Gnome applications work without pulling in any extra dependancies.

---

### Post by BHTX84 on 2012-03-13
Since starting this thread, I've done the distro hopping and had enough. And now I'm back at Lubuntu again. This issue still hasn't been resolved. I can't see how such a ridiculous bug that wreaks such havoc has yet to be addressed. :confused:

---

### Post by 666f6f on 2012-03-14
Yeah but.. like mikewhatever said earlier, for bugs to get fixed, someone has to report them first!

---

### Post by stefan_g on 2012-05-28
The bug has been filed quite some time ago already, both in 

launchpad ([https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/878993](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/878993))

and 

pcmanfm-sourceforge ([http://sourceforge.net/tracker/?func=detail&aid=3496591&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3496591&group_id=156956&atid=801864)).

It is strictly connected to pcmanfm in connection with file-roller (and several others (but not all)) and Drag'N'Drop. Hence, you suffer from it, when you drag and drop from this archive program to your lubuntu desktop, as well as to any pcmanfm file manager window.

In order to get your system functional again, press "CTRL-ALT-F1", login, and type "killall file-roller <ENTER>", press "CTRL-ALT-F7", and be back again.

As a temporary workaround, you may use another file manager, for example thunar. But keep in mind that, without any further changes, pcmanfm still manages your desktop. So do NOT D'N'D to the desktop. In fact, you must not even move the mouse across the desktop at all, while dragging from the file-roller window to the thunar window!

I hope this gets fixed eventually. It's so annoying and D'N'D is rather essential nowadays.

Best wishes,
-- Stefan

---

### Post by stefan_g on 2012-08-10
Hi there.

The bug has been reported to be closed (please see here ([http://ubuntuforums.org/showthread.php?p=12162066#post12162066](http://ubuntuforums.org/showthread.php?p=12162066#post12162066)), which seems to be a duplicate of this thread, or the other way round).

Best wishes, 
-- Stefan

---

### Post by RyanHall on 2013-02-25
It is 2/24/13 and I installed Lubuntu 12.04 X64 and ran into this issue. This issue still has not been fixed and is quite a nuisance. The other threaded mentioned in the post above states that the fix was in the proposed repository.6 months later, still no dice...

---

