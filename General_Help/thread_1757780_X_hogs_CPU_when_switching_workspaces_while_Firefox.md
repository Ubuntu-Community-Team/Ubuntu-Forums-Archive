---
title: "X hogs CPU when switching workspaces while Firefox is running"
date: 2011-05-13
forum: General Help
---

### Post by bchurchill on 2011-05-13
This probably sounds like another 'Firefox/Flash' is far too bloated post, but I think this situation is different.

If I open youtube and play a video it runs well.  The whole system uses less than about 5% of one CPU core.  These days, that's great.  Now, if I switch workspaces two things happen:

1.  npwrapper.libflashplayer.so starts taking about 45% of the CPU
2.  "/usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-Z88pAh/database -nolisten tcp vt7" also starts taking about 55% of one CPU.

The first one doesn't surprise me.  Who knows what flash does when nobody is looking (no pun intended).  However, the second one does.  This seems like it's an X issue more than a firefox/flash one.  What's worse is that #2 (but not #1) occurs even after the video stops playing as long as the tab is open -- and this is what's really frustrating.  Any thoughts on what X could be doing?  Or what flash is asking it to do?  Is this a known problem? (I could find this particular issue via search).  Any suggestions?  I didn't see anything unusual in X logs or kernel logs.

Running XUbuntu / Lucid.   Firefox 3.6.17. 
about:  plugins 
File:  npwrapper.libflashplayer.soVersion: Shockwave Flash 10.2 r159

---

