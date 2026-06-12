---
title: "Ubuntu 12.04 - Thunderbird in launcher bar"
date: 2012-06-17
forum: General Help
---

### Post by Newbunto on 2012-06-17
I just upgraded from Ubuntu 11.10 to 12.04 and now Thunderbird is not being "managed" properly in the launcher bar.

It used to be that an application in the launcher bar that had been started would then just have a little triangle to the left of the icon that is used to start the application.

Now, when I start Thunderbird, I get *two* Thunderbird icons in the launcher bar - one to start Thunderbird (permanent and unchanged) and one showing that it is running (with the little triangle to the left).

I'm not seeing this behaviour with any other applications. For example, FireFox works correctly and as it did with Ubuntu 11.10 as do LibreOffice Writer and Calc, Terminal, gedit, nautilus.

I've tried removing Thunderbird from the launcher bar and re-adding it but it made no difference.

Thunderbird 12.0.1

---

### Post by sffvba[e0rt on 2012-06-17
Strange... could you try removing it from the launcher, then running it (from the dash) and then pinning the running instance to the launcher?  Then closing it and re-starting it from the launcher.


404

---

### Post by Newbunto on 2012-06-17
Never mind - I think now solved.

I had to logout and login again.

Also, I have my own customised copy of the .desktop file so removing and re-adding changed the contents somewhat.

So basically I removed the existing item from the launcher bar and my private copy of the .desktop file, I copied the .desktop file from /usr/share/applications to a private copy, I deleted all the 'random' lines (with apologies to non-English speakers), I dragged my copy back to the launcher bar, then logged out and logged in again - and all is good.

... in case it helps someone else.

---

### Post by eindgebruiker on 2012-06-28
Had the same problem. The method suggested in #2 solved it.
However now I have this problem: [http://ubuntuforums.org/showthread.php?t=1985580](http://ubuntuforums.org/showthread.php?t=1985580) (icon doesn't show unread messages).

---

### Post by habana on 2012-06-28
> **eindgebruiker said:**
> Had the same problem. The method suggested in #2 solved it.
However now I have this problem: [http://ubuntuforums.org/showthread.php?t=1985580](http://ubuntuforums.org/showthread.php?t=1985580) (icon doesn't show unread messages).

My experience is identical

---

### Post by Marric on 2012-08-13
I had a similar problem  of showing two instances of Thunderbird in the dash and found out that it was related to the Thunderbird "Minimize to Tray" or "Fire Tray" add-ons. 
I disabled the add-on and closed Thunderbird. Then restarted it, closed one of the two windows, reactivated the add-on and restarted Thunderbird.

---

### Post by marlow59 on 2012-08-13
please mark the thread are solved so other users would find it more easily.

---

