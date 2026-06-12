---
title: "Linux Degrade?"
date: 2011-02-11
forum: General Help
---

### Post by darkenvy6 on 2011-02-11
Yes im refering to Windows Degrade and how over time windows just running will degrade and start causing errors. DLLs go missing and bizzare things. Ive seen wierd things happen on a windows machine that is dedicated to one function.

Well to my point, recently I have been having many linux issues, not like normal or anything throughout the years I have experimented with linux though.

1)entering fullscreen on VMware crashes linux sometimes (no Ctrl+Alt or Ctrl+Alt+F2 ect)
2)using a different monitor haults the virtual machine while other monitors do not (I have 4)
3)Java apps freeze and require moving the window offscreen (below the screen) to redraw
4)general linux freezing
5)glitch with xinerama that repeatedly teleports mouse between two monitors causing the system to be unusable (no Ctrl+Alt+F2 or anything either)

At first I thought they were all related to VMware but they may not be. I run VMware everyday for my slingbox and light EXE-ing when wine isnt an option.

So I may not be asking for fixes to all these problems but whats going on? Ive seen linux installs last years and believed linux to not degrade.

---

### Post by P4man on 2011-02-11
Have you ruled out a hardware issue? Ram, videocard, power supply, harddrive, overheating..?

---

### Post by darkenvy6 on 2011-02-11
I rules out overheating. Hardrive failure shouldnt crash the system (synce it resides in RAM)

I'll run Memtest now

---

### Post by darkenvy6 on 2011-02-11
Memory test performed 2 passes with no errors. I don't want to disable the nvidia driver, it took ages to get all 4 monitors to appear in the right order without error (yea I had problems with xinerama before). My previous xinerama problem included the same mouse bug but even if that was its own issue then it seems that my issue is vmware related?

---

### Post by darkenvy6 on 2011-02-12
Bump...........

---

### Post by darkenvy6 on 2011-02-13
This is still an issue. Update on VMWare, if I dont start fullscreened on one screen during the boot of the OS then when I hit fullscreen linux will crash. Now oddly enough animated gifs still roll but java games (minecraft) will stop functioning along with everything else.

---

### Post by darkenvy6 on 2011-02-15
tried reinstalling VMWare with no success
The problem is also hard to create when actually trying

bump....

---

### Post by 3Miro on 2011-02-15
All of your problems point to an issue with the Nvidia driver. Check fro bugs regarding your video card/setup and the version of the Nvidia drivers. Since it is a proprietary drivers, you have to look for that at the Nvidia forums and wait or Nvidia to fix the issue.

In the mean time, you can try to lower the number of monitors/video cards to see if this is still causing issues.

(BTW, memtest doesn't check for corrupt video RAM, although my guess is that you have a pure software issue)

---

### Post by darkenvy6 on 2011-02-15
> **3Miro said:**
> All of your problems point to an issue with the Nvidia driver. Check fro bugs regarding your video card/setup and the version of the Nvidia drivers. Since it is a proprietary drivers, you have to look for that at the Nvidia forums and wait or Nvidia to fix the issue.

In the mean time, you can try to lower the number of monitors/video cards to see if this is still causing issues.

(BTW, memtest doesn't check for corrupt video RAM, although my guess is that you have a pure software issue)

yea I know it doesn't check video ram. I actually did find a good comprehensive GPU checker for Linux ill dig it out and report on it. Thats how I found out my last graphics card had a bad GPU (dual-GPU card) with the other intact. Hopefully its all software because I REALLY enjoy using 4 monitors, I multi-task and use up my 4 spaces like you wouldn't believe.

---

### Post by tgalati4 on 2011-02-15
I'm inclined to agree that GPU or video RAM issue may be causing the freezes.  Did you look in dmesg for errors?

dmesg | more    (spacebar to page through and q to quit)

How old is the video card?  Sometimes the heat sinks need to be removed and the heat paste replaced if this card has seen some hard gaming use.

---

### Post by sydbat on 2011-02-15
Dumb question time...mostly because I may have missed something...but, how are you running Ubuntu? Is it in the VM, with Windows as the host? Or is the VM running on Ubuntu as host and has other OS's in it?

If Ubuntu is the VM guest on a Windows host, then all fingers point to Windows.

If Ubuntu is the host, then 3Miro is onto something.

---

### Post by 3Miro on 2011-02-15
One more idea. Changing the windows manager can help the issue. Compiz is using heavy OpenGL acceleration and rather demanding on video RAM, on the other hand it utilizes power that other WM may not use. Try Metacity vs Compiz (assuming you are using Gnome). This is the easiest thing to try and it will help narrow down the possibilities.

---

