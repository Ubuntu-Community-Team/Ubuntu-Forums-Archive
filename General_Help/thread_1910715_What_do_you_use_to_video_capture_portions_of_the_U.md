---
title: "What do you use to video capture portions of the Ubuntu screen?"
date: 2012-01-17
forum: General Help
---

### Post by rocksockdoc on 2012-01-17
What is a recommended video-screen capture program to capture odd workings of Ubuntu Gnome desktop?

I have weird intermittent "dancing icons" that I'd like to capture in a video screenshot (because it's hard to explain statically).

What do you use to video capture portions of the Ubuntu screen?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211037&stc=1&d=1326836473[/IMG]

---

### Post by Double.J on 2012-01-17
Xvidcap in the repos sounds like it'll do what you need, I've used it a few times - the red box that pops up is the area to capture - you can resize it to anything from the screen to about a square inch :) it's pretty basic and outputs in either avi or mpeg - there sems to be a bug with playback, but you just go to your Videos directory and play the file with your fav. editor/player :)

---

### Post by Ms. Daisy on 2012-01-17
To directly answer your question, I use a virtual machine ([virtualbox]("https://help.ubuntu.com/community/VirtualBox")). It's a long way to go simply for a quick video of the screen, but it would work.

---

### Post by rocksockdoc on 2012-01-17
> **gnu/mirow said:**
> Xvidcap in the repos sounds like it'll do what you need

Thanks for taking the time & energy to advise me. 

I'll install XVidCap and then test it to see how it works to do a video capture of a portion of the screen.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211047&stc=1&d=1326853307[/IMG]

---

### Post by rocksockdoc on 2012-01-17
It's going to take some getting used to ... but the XVidCap appears to work.

At the moment, it's creating files far longer than what I captured ... (for example, this 13-second video capture shows up as 8 minutes long) ... but I'll work on it 'till I figure it out.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211060&stc=1&d=1326862433[/IMG]

---

### Post by rocksockdoc on 2012-01-18
I couldn't do much with the ~/test-0000.mpeg file created by XVidCap ... which showed up as if it were 8 minutes long ... so I converted it to an AVI using Avidemux.

Here's that 13-second AVI file (inside a zip folder) by way of sample.

It's just a simple test where I created a folder named foo, and then created another named bar, and then deleted 'em both.

But, the point is that XVidCap works. It's not intuitive. But it works to capture a portion of the screen and audio to a video file.

Thanks!

---

### Post by rocksockdoc on 2012-04-06
I recently found "recordmydesktop" from the Ubuntu software repository which seems to be as good or better than XVidCap for capturing the screen and audio to a video file.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215605&stc=1&d=1333762982[/IMG]

---

