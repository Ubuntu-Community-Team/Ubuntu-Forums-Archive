---
title: "Screen Flicker on Suspend with AMD E-350"
date: 2011-09-24
forum: General Help
---

### Post by arrow.69 on 2011-09-24
Hi,

I'm running Ubuntu Oneiric Beta 2, but I had the same problem with Fedora 15, so this is clearly an X/video driver issue.  When I suspend the computer for a while, the screen will flicker heavily upon waking up.  The flickering eventually stops after 10-15 minutes, but rebooting, changing resolution, resetting X, don't seem to affect the flickering.  In fact, once wake from sleep has triggered the flickering, the flickering will happen in the BIOS or in Windows if I reboot into it.  The flickering can only be triggered in Linux, not Windows, so I know it's not a hardware issue.

I'm using the open source radeon driver, though switching to fglrx didn't solve anything.  My computer is the Sony Vaio YB, with the AMD E-350 'APU'.

Any ideas on how to troubleshoot this, or is it just hopeless until the driver gods do their magic?  This doesn't seem to be a common issue, so I wonder what is specific about my setup that makes it happen.

Thanks.

---

### Post by arrow.69 on 2011-09-26
anyone?

---

### Post by dFlyer on 2011-09-26
My advice is to submit a bug report as 11.10 is in beta status. I was test driving it for a few days but too many bugs yet for my liking so reinstall 11.04. Hopefully by the time it gets to rc status it's more stable.

---

### Post by nej_simon on 2011-09-29
The E350 apparently has flicker/corruption issues. I have the same problem as you (in Windows everything works) but others have similar problems in windows too.

[https://bugs.freedesktop.org/show_bug.cgi?id=36513](https://bugs.freedesktop.org/show_bug.cgi?id=36513)
[http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/x120e-Flickering/td-p/389523](http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/x120e-Flickering/td-p/389523)
[http://forums.amd.com/forum/messageview.cfm?catid=33&threadid=154377](http://forums.amd.com/forum/messageview.cfm?catid=33&threadid=154377)
[http://www.youtube.com/watch?v=1F2H2vaROqM](http://www.youtube.com/watch?v=1F2H2vaROqM)
Etc..

---

### Post by Harold B on 2011-09-30
I have a similar problem with screen flicker and the resolution changes. This happens after screen dim that I have set for 10 minutes of inactivity. I have to reboot to get out of it. 

Have a Dell XPS One A2010. Intel® Core™2 Duo CPU E4500 @ 2.20GHz × 2 and a Radeon HD 2400.

---

