---
title: "Gui Freezes when using mouse"
date: 2011-01-20
forum: General Help
---

### Post by Roger Steiner on 2011-01-20
I have a Foxconn with Intel 330 processor, 1 gig RAM, and 80 gig hard drive. Unit will freeze when using the mouse at infrequent intervals. I had Edubuntu 8.10 installed and have now installed 10-10 Ubuntu to rule out software issues. During the new install, the video would stop after a period of time, and could return to operation by moving the mouse. The same mouse,keyboard, and monitor are being used on three other computer boxes using a KVM switch. The problem is unique to this Foxconn box. An identical Foxconn box runs normal and is set up as a server

After the unit freezes, I can use the alt-ctr-sysrq RES to eliminate the GUI. This tells me that the Linux system is still running.

What segment of the system log should I be examining? Is this an IRQ issue?

---

### Post by Roger Steiner on 2011-01-23
While attempting to view an MP4 video, the video freezes and the audio continues to operate. I am beginning to suspect that the issue deals with the on-board video circuit.

My other Foxconn has no issues running the same operating system and video files.

I was reading other threads about videos freezing in the forums. Are some video chips more troublesome than others? Would a permanent fix be the addition of a PCI video card, or is there a software fix available?

I have many computers, both lap top and desk tops running Ubuntu without encountering similar problems. 

Thank you for any thoughts on this issue.

---

### Post by Roger Steiner on 2011-01-24
After trying many things and looking for differences in the video settings on my two Foxconn computers, I noted that the working unit had the video set for Extra Video Effects. The unit with the issues was set to normal.

System>Preferences>Appearance>Visual Effects>Extra

After switching the preference, the video is functioning properly. The last video that I played and froze, functioned perfectly today.

I will continue to do tests to be sure this is the problem and is solved.

---

### Post by Roger Steiner on 2011-01-25
Sorry, but I spoke too soon. I just had another freeze while using the mouse. I just flipped the switch to 'no effects' on the appearance menu and will try again. I am convinced that it is a video issue.

Any thoughts?

---

### Post by Roger Steiner on 2011-01-28
After many frustrating days, and no solution in sight, I loaded Fedora 14 on the computer. Everything is working fine. Why this particular Foxconn would have video issues that cause the system to freeze, is a mystery. 

I have four desktops and two lap tops, all running Ubuntu. None have freezing problems.

---

