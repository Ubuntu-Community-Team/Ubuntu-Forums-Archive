---
title: "Changing the refresh screen rate"
date: 2009-12-29
forum: General Help
---

### Post by linux_dream on 2009-12-29
Under Windows XP I can set my resolution to 1280x960 and have a 85 Hz refresh rate.
Under Ubuntu I can set the same resolution but can't go over 70 Hz, which is really annoying to my eyes.  
I've googled about the problem, but either I didn't understand what to do, either it didn't work.

What command should I type?  I'm somewhat new to Linux and Ubuntu... 
Thank you!

---

### Post by linux_dream on 2009-12-30
Any idea?

---

### Post by linux_dream on 2010-01-04
I'm still having the problem.
I've been told to add a modeline in xrandr.  
Now typing xrandr in a terminal I have > Screen 0: minimum 320 x 175, current 1280 x 960, maximum 1280 x 960
default connected 1280x960+0+0 0mm x 0mm
   1024x768       50.0     51.0     52.0     53.0     54.0    102.0  
   960x540        55.0  
   840x525        56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   720x400        67.0  
   680x384        68.0     69.0  
   640x512        70.0  
   640x480        71.0     72.0     73.0     74.0     75.0     76.0     77.0  
   640x400        78.0  
   640x350        79.0  
   576x432        80.0     81.0     82.0     83.0  
   512x384        84.0     85.0     86.0     87.0     88.0  
   416x312        89.0  
   400x300        90.0     91.0     92.0     93.0     94.0  
   360x200        95.0  
   320x240        96.0     97.0     98.0     99.0  
   320x200       100.0  
   320x175       101.0  
   1280x960      102.0* 
   1280x960_85.00   85.0  So I set my resolution to 1280x960 and then I typed in a terminal "xrandr -r 85" but I get "Failed to change the screen configuration!".
I'm desperate.  
Thanks in advance for any help!


Edit: Problem solved, nevermind.

---

