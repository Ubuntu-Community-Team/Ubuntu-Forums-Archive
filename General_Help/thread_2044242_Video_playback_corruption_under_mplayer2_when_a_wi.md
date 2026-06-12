---
title: "Video playback corruption under mplayer2 when a window updates in the background"
date: 2012-08-19
forum: General Help
---

### Post by Eromatic on 2012-08-19
Under Ubuntu 12.04 32bit and Nvidia driver 295.49, there seems to be an issue in how Ubuntu handles screen updates. For instance, should you have a Firefox window open to a webpage that displays something with a scrolling marquee (scrolling text) and then launch a video player (mplayer2 using -vo gl) over that, part of the video player window that is now on top of the Firefox window will not update for a fraction of a second. 

The corruption seen within the mplayer2 window is no more than the total height at the position of the scrolling marquee of the Firefox window, and the corruption spans the entire width within the mplayer2 window. 

To some this may be mistaken as screen tearing related to vsync issues. This also doesn't seem to be a Firefox issue, as a scrolling terminal window can produce the same issue. Nor be it a mplayer2 issue, as an Adobe Flash Player window from a Firefox window to over another Firefox window with scrolling marquee can reproduce the issue.

The following done with the Print Screen key is a screenshot of issue described, but its corruption position is from the running terminal window that is below the firefox window. *(PITA to capture via print screen key.)*

[[IMG]http://i.imgur.com/BpEWEl.png[/IMG]](http://imgur.com/BpEWE.png)

The test video used is from: 
[http://www.youtube.com/watch?v=ceX18O9pvLs](http://www.youtube.com/watch?v=ceX18O9pvLs)

(The test video displays a white line that moves left to right on loop. The white line should not be broken in any way as the video is played back.)

A workaround that I use is to just make sure that any windows that have to redraw in the background are kept minimized.

As I believe that this is a bug, what I need to know is in which package I should file this bug under. (Compiz? Xorg? Nvidia?) ...Or if it had been previously reported, of where I can find this report.

---

### Post by Rexilion on 2012-08-19
Looking at the [bugs]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bugs") I don't see anything that matches your experience.

Perhaps you could try to disable compiz and see if that makes a different?

---

### Post by Eromatic on 2012-08-19
Disabling Compiz would likely correct it, but Compiz would be needed if I am to run Unity. :popcorn:

One other workaround that I did find is to enable Compiz workaround *"Force full screen redraws (buffer swap) on repaint"* under CCSM. There is a warning in the tool tip there that this function will result in a massive increase in CPU & GPU usage. It is true of course in that the GPU usage will be greater, but the CPU usage doen't seem to have any difference. Worst being that this setting will consume more power and the GPU will get hotter. I'm on a desktop, but I could imagine that it would suck royally for laptop users.

---

