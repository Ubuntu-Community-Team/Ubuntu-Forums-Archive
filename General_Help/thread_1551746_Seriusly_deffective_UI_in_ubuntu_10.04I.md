---
title: "Seriusly deffective UI in ubuntu 10.04I"
date: 2010-08-12
forum: General Help
---

### Post by intrader on 2010-08-12
I have installed 10.04 on Dell Inspiron 8200 with 1GB of memory. The system ran ubuntu 9.04 without a hitch until I messed up the sound after trying to get Skype running on it. So I downloaded 10.04 iso and installed it. 
Ubuntu 10.04 runs Skype Ok. except that all applications including Skype suffer problems with the following observed problems:
.Slow responding to button or link click - as for example Close, or Apply, or submit.
&#8226; Slow response of window when switching to another window
&#8226; Click on scrollbar bottom arrow button remains activated and continues to move even when mouse is lifted. It does cancel with a click (does cancel with ESC). Scrollbar remains active once the scrollbar button is clicked - moving the mouse on window scrolls once it starts; stops only when clicking (repeatedly) on scrollbar button or via the ESC key.
&#8226; After left mouse click on an icon or link, the mouse often changes to a hand icon and the icon moves along with the mouse (trailing a small thumbprint image)
&#8226; Hangs up on occasion on while moving mouse to some action - requires restart.tarts highlighting without the need to move mouse.
&#8226; Highlighting of text is difficult to cancel; it extremely difficult to reliably start the highlight action

By the way I have reported this behaviour for 9.10 without anybody helping.

The system is very annoying to use in this state. I am considering moving moving to Suse (as I have a version running without a hitch on another laptop).

Update of observations [
These problems may not be solely on ubuntu; I have tried the latest distributions of Fedora and Suse with the same problems. Ubuntu 9.04 (except for Skype) and  Suse 9.2 worked.

&#8226; Slow responding to click on tab, button, scrollbar or link; Applications-->System-->Preferences-->Mouse click at one second rate does not always respond.
&#8226; Slow response of window when switching to another window
&#8226; Scrollbar remains active once the scrollbar button is clicked - mouse movement causes scroll even out of scrollbar;  scrolls even when mouse is in another window; stops only when clicking (repeatedly) on scrollbar button or via the ESC key.
&#8226; After left mouse click on an icon or link, without perceptible move from the mouse, the mouse pointer often changes to a hand icon and the icon moves along with the mouse (trailing a small thumb-print image)
&#8226; Hangs up on occasion on while moving mouse to some action - requires restart.
&#8226; Highlighting text is difficult to cancel; extremely difficult to reliably start the highlight action.
]

---

### Post by earthpigg on 2010-08-12
hi,

i suspect you did some tweaking of 9.04 to make it smoother/faster on that hardware?

do you remember what it was?

an easy place to start is system -> preferences -> startup applications... and start disabling things that look useless to you.

---

### Post by brokenromeo on 2010-08-12
Maybe this is a display driver issue...

---

### Post by DeanMc on 2010-08-12
I dunno, one gig of ram isn't all that great. I would also suggest disabling all of the fluff that you don't need. There are Linux distro's out there where 1gb of ram is more than enough but I have always thought the best way to treat Ubuntu is to use the same specs as Vista to determine if your laptop/pc will run smoothly or not.

---

### Post by earthpigg on 2010-08-12
I disagree with the poster above me. 1gb of RAM is plenty for Ubuntu 10.04.

with firefox (5 tabs), pidgin, empathy, and rhythmbox (3000 song playlist) open I am using 596 mb of ram according to "free -m".

CPU usage is more likely to be what's slowing the OP down, not RAM. Though, it could be a display driver issue, as someone above suggested. 

@OP - try going to system -> preferences -> appearance -> visual effects -> "none". Click around a bit, see if that improves things.

---

### Post by earthpigg on 2010-08-12
> **intrader said:**
> 
&#8226; Click on scrollbar bottom arrow button remains activated and continues to move even when mouse is lifted. It does cancel with a click (does cancel with ESC). Scrollbar remains active once the scrollbar button is clicked - moving the mouse on window scrolls once it starts; stops only when clicking (repeatedly) on scrollbar button or via the ESC key.


What website(s)? Lot's of advertisements, flash, and other rubbish on the website? Like, for example, FarmVille in Facebook? There are ways we can address that if it's isolated to a few websites or a certain type of website.

How does ubuntuforums.org run in firefox, without any other tabs open?

---

### Post by intrader on 2010-08-13
Starting from most recent:
1. Any window not only web site's. Yes it is worse when flash is busy.Currently running 9.3% CPU with firefox-, 3.% Xorg. I have many tabs open in three firefox windows. ubuntuforums.org shows scroll problem with no other tabs.
2. earthpigg:1gb of RAM was plenty for 9.04. I usually also have tomboy running. When CPU usage is high > 50%, I see the problems more. But I am seen the problem now wit 23.4% CPU as I scroll, move the button onto the scrolled window, the mouse follows move the scroll. Visual effects is set to none. I have uninstalled the enhanced driver (version 96). It is a little more peppy, but problems remain. Most annoying is that when I click on an icon or link, a large proportion of the time, the hand icon appears, and a thumnail follows the mouse.
3.DeanMc:As I said, 9.04 ran fine with no settings change and version 96 of the driver. My problems started when I tried Skype and I messed up the sound system. So I tried 9.10 and immediately noticed the problems, but still Skype would not work. I went back to 9.04, but my sound was still hosed. So I decided to try 10.04. Skype works on 10.04 with the system fully loaded, albeit with the icon and links problems (hand conversion).
4. Brokenromeo: I have unistalled the enhanced driver. System is somewhat peppier, but problems remain. I believe the problem to be Xorg with the latests changes for multitouch.
5. earthpigg: No tweaking for 9.04 except that I accepted the new driver for NVIDIA (version 96). Subsequently I unstalled resulting in.... (see 4)


I really appreciate your help. When I reported the issue with 9.10, nothing, nothing. Please advise what I need to furnish in configuration files, etc 

This is the first few lines of top's output
top - 11:27:29 up 3 days,  1:30,  2 users,  load average: 0.56, 0.60, 0.61
Tasks: 155 total,   1 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.9%us,  3.0%sy,  0.0%ni, 88.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026448k total,   984888k used,    41560k free,    77316k buffers
Swap:  1220900k total,    10056k used,  1210844k free,   368236k cached

So system is loaded, but so was the 9.04. I am running XAMPP in the waiting, and servicing a web site. But without it I still have the problem.

Additional info: I have installed xubuntu as an alternate desktop. It seems much more responsive, but still exhibits the problems in all applications. It seems to confirm my thinking that it is Xorg causing the problems.


I hope that you'll can help me solve this problem.:(

---

### Post by intrader on 2010-08-29
> **earthpigg said:**
> hi,

i suspect you did some tweaking of 9.04 to make it smoother/faster on that hardware?

do you remember what it was?

an easy place to start is system -> preferences -> startup applications... and start disabling things that look useless to you.

No changes to 9.04.
I was unable to run Skype and installed 9.10.
I noticed the UI problems
Could not run Skype
I re-installed 9.04. 
When the update from canonical was performed, I had the same UI problems as with 9.10; no Skype on 9.04
Decided to install 10.04 from scratch (but maintaining /home). UI problems as described. Skype runs fine on 10.04.

Please help, as the system is really unusable.

I have also updated the post with recent observations.](*,)](*,)](*,)

---

### Post by intrader on 2010-08-29
> **DeanMc said:**
> I dunno, one gig of ram isn't all that great. I would also suggest disabling all of the fluff that you don't need. There are Linux distro's out there where 1gb of ram is more than enough but I have always thought the best way to treat Ubuntu is to use the same specs as Vista to determine if your laptop/pc will run smoothly or not.
This system runs ok with XP
This system also ran OK with 9.04 with no changes. However, once I reinstalled 9.04 and accepted the updates from canonical, I got the UI problems in 9.04.
](*,)

---

### Post by intrader on 2010-08-29
> **earthpigg said:**
> What website(s)? Lot's of advertisements, flash, and other rubbish on the website? Like, for example, FarmVille in Facebook? There are ways we can address that if it's isolated to a few websites or a certain type of website.

How does ubuntuforums.org run in firefox, without any other tabs open?

No particular website. It seems worse when advertisements are running (like flash). I have the same problem with chrome or firefox; although chrome is noticeable faster to load.

firefox with ubuntuforums.org in one tab has the problems; the most annoying is the scroll problems,next is the highlight problems, next is the slow response to click.](*,)

---

### Post by intrader on 2010-09-25
This problem continues to plague my ubuntu 10.04

I have reported a bug 631130 which has been accepted.

In the meantime, the automated update has updated the NVIDEA driver. The new driver seems peppier but I still have the described problems.

---

