---
title: "KRDC/KRFB problems (remote desktop)"
date: 2010-08-22
forum: General Help
---

### Post by Old *ix Geek on 2010-08-22
I'm having a problem with two computers using KRDC and KRFB for remote connections. Let's call them "desktop" and "laptop."

When laptop connects to desktop, it sees nothing but a black, blank screen with the mouse pointer in the top left corner. It's unable to move the pointer or do anything else.

When desktop connects to laptop, it sees whatever is on laptop's screen at the moment it connects--and that's it; after that it appears frozen. Navigating and selecting things, such as other programs running on laptop, appears to do nothing--but if you look at laptop in person, it's responding to those gestures. So it's like a refresh issue on desktop--but I see no way to force a refresh.

Note that it's NOT a connection issue--they connect just fine after prompting for and receiving their respective passwords.

These same computers used to connect without problems on earlier versions of Kubuntu. They're both running 9.10 at present.

---

### Post by Doctor-No on 2010-08-23
I can confirm this bug on (K)Ubuntu 10.04 / Lucid, too.
Display of remote machine appears frozen, but moving mouse on local machine leads to movements on remote machine (expected behaviour).

---

### Post by Old *ix Geek on 2010-08-23
I'm glad it's not just me!

---

### Post by Old *ix Geek on 2010-08-30
After mucking around on both computers a bit, my results are now somewhat different.

I experimented with numerous settings, including the NVIDIA 3D-accelerated graphics drivers, choosing each of the two (out of three) that I don't normally use. I was using the 'recommended' one on both computers. I tried switching up using KDE [my usual] and Gnome, using different remote desktop applications, and turning on/off desktop effects such as cube.

So now when I connect from either computer to the other, I see whatever is on the remote computer at the moment of connection. At first. (More on that later.)

Depending on which combo I'm using, I may or may not see the remote pointer move as I move my trackball on the local PC.

BUT, once again, selecting anything on the remote computer APPEARS to do nothing on the local computer--but it actually *IS* working on the remote PC.  I put the laptop and desktop next to each other and watched the remote PC while navigating with the local one's trackball, and I could do whatever I wanted on the remote by watching its actual display. But NONE of it showed up on the local's screen. That just continues displaying whatever was on the remote's screen when I connected.

Finally, if I disconnect and then reconnect later--even with a DIFFERENT remote desktop app--whatever was on the remote's screen when I connected earlier is still there. It's like it's displaying a cached version, even though the app I'm using ISN'T the one I used earlier.

I REALLY need this to work like it used to. Any ideas? :confused: ](*,)

---

### Post by toolszak on 2010-10-15
You must disable desktop effects and everything will work fine

---

### Post by dgray_from_dc on 2011-03-14
Has there been any improvement to this?

  I've encountered the same problem and while I'd be willing to disable the effects, I like having them there.  I have a Kubuntu Lucid box acting as a HTPC Server / Frontend Hybrid.  I'd like to keep all of the eye-candy on when showing it off to those who are still drinking the MS-KoolAid :D.

---

### Post by sgruendel on 2011-08-06
I've reported this bug as [https://bugs.kde.org/show_bug.cgi?id=279520](https://bugs.kde.org/show_bug.cgi?id=279520), please vote for it if you want if fixed.

---

### Post by Mark Tomlinson on 2011-11-07
> **toolszak said:**
> You must disable desktop effects and everything will work fine

BUMP

It took me forever to find this.  (Okay, two days).  To make it easier to Google, I'll repeat the keywords I looked for: kubuntu, vnc, tightvnc, remote desktop, desktop sharing, black screen, blinking screen.

For clarity for those who just found this work-around,
(1)  Click the Kubuntu icon,
(2)  Select "Computer"
(3)  Select "System Settings"
(4)  Select "Desktop Effects"
(5)  Uncheck "Enable desktop effects at startup"
(6)  Apply

---

