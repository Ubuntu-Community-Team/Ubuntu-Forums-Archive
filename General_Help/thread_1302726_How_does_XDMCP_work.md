---
title: "How does XDMCP work?"
date: 2009-10-27
forum: General Help
---

### Post by ajb2 on 2009-10-27
Hi, everyone,

I've been tasked with trying to get a user with a
rather old NCD X terminal to be able to log into
an Ubuntu system via XDMCP.  Although it sort of
works, it's been behaving inconsistently.
Specifically, if I log in and log out a number of
times, there are several things that may be
different:

(1) Sometimes the background is clear; sometimes it's fuzzy.
(2) Sometimes the icons look good (e.g. the ones
    on the pull-down menus), and sometimes they're
    fuzzy.
(3) Sometimes the fonts come up as a decent size;
    other times they show up really tiny.
(4) Sometimes the keyboard works fine and
    sometimes the map is screwed up (I press "a"
    and "t" shows up, etc.), even though I've set
    up an .xmodmaprc in the home directory.

#1 and #2 usually happen together, but I've had
cases where the background is clear but the icons
are poor.

If someone can give me specific things to fix,
that would be great; but I'm thinking that right
now what I need are pointers to information that
would help me understand better how everything
works when the system comes up.  I.e., who decides
(server or client) what resolution to use when
displaying the background and icons, and how, and
what information does it use when making this
decision, and how does it get that information?
And similarly for font and keymap information.
Hopefully there's something around which will give
me insight into how this works without a month's
worth of reading.

Also, when the server and display manager are
talking to each other and working all this out, is
there a way to get them to dump more info on the
messages they send?  I'm thinking that may be
seeing those may help me determine why it's
behaving inconsistently (I suspect some sort of
timing issue) and what I need to do to work around
it.  The .xsession-errors info hasn't helped much.

Thanks for any help you can provide.

---

### Post by Giblet5 on 2009-10-27
It sounds like the X-terminal is having problems.

Try using xdpyinfo (from the X-terminal's session) to verify that the session is always starting at a predictable resolution and color depth.

I'm guessing that one or the other is changing from one session to another.

If either the resolution or color depth change, you'll see all of the symptoms you describe.

If not, then the X-terminal probably has flaky hardware and you should get an HP or Tektronix. ;)

---

### Post by kjohri on 2009-10-27
Try to avoid using proprietary drivers for display  at both the terminal and the main system. Also see if this link helps,

[http://www.softprayog.in/troubleshooting/linux/x-window-remote-display.shtml](http://www.softprayog.in/troubleshooting/linux/x-window-remote-display.shtml)

---

### Post by Giblet5 on 2009-10-27
> **kjohri said:**
> Try to avoid using proprietary drivers for display  at both the terminal and the main system. Also see if this link helps,

[http://www.softprayog.in/troubleshooting/linux/x-window-remote-display.shtml](http://www.softprayog.in/troubleshooting/linux/x-window-remote-display.shtml)

One can't use proprietary drivers from an X-terminal.

An X-terminal has the X11R4/6 server in ROM and barely the smarts to configure it.

---

### Post by ajb2 on 2009-11-03
Thanks for the suggestions.  I've been able to extract a little more information from the system, but it hasn't helped.

I tried a number of tests where I logged in, brought up a Terminal window, tried to type something in it to see if the keyboard worked OK, then either I closed the Terminal window or left it up, then I logged out.  

Although I previously had had problems with the background appearing fuzzy, in my latest 20 tests this problem did not come up.  In one case, the icons were fuzzy.  In two cases, the first window that came up (a window that the NCD X-terminal uses for its own functions) had some fuzziness in the top bar of the window. 

The keymap was still a problem; the keys behaved correctly only 7 times out of the 20, even though I have an .xmodmaprc file (.Xmodmap symlinks to it).  The fonts came up too small 4 times out of 20; for some reason, this happened only when I closed the Terminal window in the previous test, although it didn't happen every time I closed the Terminal window.  Nevertheless, I think there's a connection.

I'm convinced that the fuzziness issues are related to timing---i.e. if the server or display manager does things or gets responses in one order, it can figure out the correct resolution, while if the order is different then some things come out fuzzy.  The behavior and appearance are not consistent with hardware problems.

I have no idea why the keyboard works only some of the time.

I set GDM to dump debug information to the syslog, but this debug information hasn't given me a clue as to what's going on.  Neither has .xsession-errors, nor the output of xdpyinfo.

If anyone has any other idea of what I can try, I'd appreciate it.  I'm probably also going to try asking a different forum.

---

