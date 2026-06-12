---
title: "Synergy not working properly in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by kooldino on 2011-10-15
I just installed the most recent version of synergy on my fresh 11.10 installation.

However, it's not working properly.  I have my ubuntu box set up as the server, and a W7 machine to the right set up as a client, just like I always have.

The problem is that when I move my cursor to the right edge of the screen (which is where it should jump to the other computer), it usually just stays at the edge of my display.  Occasionally, it will go over to the right, but it's seemingly random.  I'd like to point out that the machines are connected 100% of the time.

The only way I can get it to go to the other machine 100% of the time is if the mouse cursor is over the gray menu bar at the top of the screen.

On the other hand, the cusor will easily move back to my ubuntu machine from the windows machine.

What gives?

---

### Post by kooldino on 2011-10-15
The linux version in the repositories is 1.36, the windows version is 1.37.

This is really odd.  It's like it's not properly detecting the edge of the screen.  Could this be a unity issue?

---

### Post by kooldino on 2011-10-15
More info:

If I set my other computer to be to the RIGHT or BELOW this one, I have the issue.

If I set the other computer to be ABOVE or to the LEFT of this one, it works every time.  What's interesting here is that the top of the screen has the toolbar, and the left of the screen has the unity/launcher thing.  OTOH, the right and bottom of the screens are empty.

So this got me thinking.  Will the cursor jump to the next screen reliably only if there is some kind of window or GUI graphic touching that edge of the screen?  I moved a nautilus window to the right edge of the screen, and the cursor would jump to my other computer every time, as long as the cursor hovered above the window.  Whenever I try to move the mouse cursor to the next screen in an area on that same edge that isn't occupied by that same nautilus window, it will not work.

This is obviously some kind of bug.

Edit: Also, I can usually jump between screens whether there are gui graphics there or not, as long as I wait a minute or two to do it.

---

### Post by dangruhn on 2011-10-17
kooldino,

I can verify your experience with my new Ubuntu 11.10 installation, thanks for posting as I thought I was going crazy trying to pin down when it worked and when it didn't.

I am using Synergy 1.3.6 on my Ubunutu machine and 1.4.2 on my WinXP machine. The WinXP has not changed.

I have noticed that when I run with debug turned on I'm not getting any 'try to leave "dgruhn-ub" on left' messages in the log when there is no window abutting or overlapping the left edge (which is where my WinXP screen is "located").

My thought is that Ubunutu has stopped giving some event that is used to provide.

I'm hoping someone will take a look here. Leaving a window over there is not convenient

---

### Post by kooldino on 2011-10-17
Phew, at least I'm not the only one.

Yes, it's almost as if whatever event senses the edge of the screen isn't running if the cursor is on the desktop.

Did you run 11.04?  If so, I assume you didn't have this issue?

---

### Post by traffas on 2011-10-18
I'm experiencing exactly the same symptoms. Under 11.04, Ubuntu Synergy server on the left interacted flawlessly with Windows 7 client on the right. After upgrading to Oneiric, it sporadically works if I get a running start to cross the screen, but the only way to consistently travel from Ubuntu to Windows is in the upper right corner in the system tray area. I've upgraded to the 64-bit 1.4.4 beta from synergy-foss.org and continue to experience the same problem.

Glad I'm not the only one.

---

### Post by traffas on 2011-10-18
I've opened a ticket on synergy-foss.org. Please feel free to contribute anything I've missed.

[http://synergy-foss.org/tracker/issues/3037](http://synergy-foss.org/tracker/issues/3037)

---

### Post by wjgeorge on 2011-10-18
actuall found a weird work around.

Open a window and have it overlap the edge you want to move to (either left or right). Then scroll your mouse over this window; the cursor will move to other machine.

My quess is that without the overlapping window, gnome-session-fallback is clipping its cursor

---

### Post by dgstangel on 2011-10-18
I am also having this exact same issue;  my other desktop is situated to the right of my Ubuntu desktop, and I can only move the cursor rightward by going thru the menu bar at the top.  I have used Synergy for several years, and it worked fine on Ubuntu 11.04. I just updated to 11.10 today and discovered this bug.

---

### Post by kooldino on 2011-10-19
> **traffas said:**
> I've opened a ticket on synergy-foss.org. Please feel free to contribute anything I've missed.

[http://synergy-foss.org/tracker/issues/3037](http://synergy-foss.org/tracker/issues/3037)

You should probably specify that it doesn't transfer correctly unless the screen edge has some kind of window drawn on it.  For instance, you can't transfer to the bottom either.

---

### Post by kooldino on 2011-10-19
> **wjgeorge said:**
> actuall found a weird work around.

Open a window and have it overlap the edge you want to move to (either left or right). Then scroll your mouse over this window; the cursor will move to other machine.


Right, I pointed this out in the third post.

---

### Post by dangruhn on 2011-10-19
Nice to see so many adding their information.

I can verify that leaving a window on the edge (left in my case) allows the cursor to move from one machine to the other. I've taken to putting a small window there (sort of like adding a doorway between my screens) but I am hoping this can be fixed somehow.

---

### Post by pathennessy on 2011-10-20
Sounds like the same issue as..

[http://synergy-foss.org/tracker/issues/2958]("http://synergy-foss.org/tracker/issues/2958")

---

### Post by kooldino on 2011-10-20
> **pathennessy said:**
> Sounds like the same issue as..

[http://synergy-foss.org/tracker/issues/2958]("http://synergy-foss.org/tracker/issues/2958")

So it looks like there is a fix on that page, but I'm not clear on what to do with it.

---

### Post by Jamina1 on 2011-10-21
I am having the same issue, and like others have said it only manifests without a window against the side of the screen. If I have a program open full screen it works flawlessly but if I am on an empty desktop, the right edge of the screen is wholly unresponsive.

---

### Post by bigoten on 2011-10-27
> **pathennessy said:**
> Sounds like the same issue as..

[http://synergy-foss.org/tracker/issues/2958]("http://synergy-foss.org/tracker/issues/2958")

Actually this link does show a solution for this problem, but I have no idea how to implement it. A .diff patch file is given, but how does one install it? Anyway, this is not the "legal" way to solve this problem, right?

---

### Post by Gaferion on 2011-10-31
Actually, there are step-by-step instructions in comment #29 now.

[http://synergy-foss.org/tracker/issues/2958#note-29](http://synergy-foss.org/tracker/issues/2958#note-29)

---

### Post by bigoten on 2011-11-03
Indeed! This solution worked for me, great!
Thanks :D

---

### Post by moresun on 2012-03-20
Thanks for the quick workaround, it works

> **wjgeorge said:**
> actuall found a weird work around.

Open a window and have it overlap the edge you want to move to (either left or right). Then scroll your mouse over this window; the cursor will move to other machine.

My quess is that without the overlapping window, gnome-session-fallback is clipping its cursor

---

### Post by Deuce1912 on 2012-03-20
I'm having a similar issue in that its not working properly. I have it setup to a hot key and when I press said combination it just moves the cursor.

I hope this will be resolved soon. I'll be keeping my eye on that support ticket.

- Deuce1912

---

### Post by t3ckfr3ak on 2012-04-09
i cant get synergy to do anything at all. i have an ubuntu host, and an ubuntu guest, both running 12.04 

any help would be apreciated

---

