---
title: "Problems with Jaunty (9.04) and Karmic (9.10)"
date: 2009-12-03
forum: General Help
---

### Post by wingrider78 on 2009-12-03
Hello, this is my first post here, but have been searching around for a while now and have found many answers to many problems...but I can't find the answer to these...Here is a little background on what I have already gone through to get to this point...

Two months ago (roughly), I decided to try Ubuntu Jaunty on my desktop (Dell Dimension 8400), it ran great and I was loving it, until I did the upgrade to 9.10...then my desktop wouldn't even boot into ubuntu at all, it would just hang at one of the first boot screens...looked around some more until I found Linux Mint 7, installed that, loved it, and it worked...so I put it on my laptop too (Acer Extensa 5230E) worked like a charm there too.  I kept trying out programs to replace all my windows programs and everything was going well until I tried Skype.  I couldn't get the microphone to pick up anything while using Linux Mint.  I then downloaded the iso for Karmic and tried it on my laptop for a week (using the Live CD) everything was going smoothly...so I did a fresh install on my lappy with Karmic, had some crash reports happen while I running updates, got the updates finished, and everything has been fine since (using it right now, in fact).  My problem has been the desktop...I got cocky and just full installed Karmic on the desktop, the install got hung up and didn't finish, couldn't boot into linux at all (still could boot to my xp, so that was okay).  Then I tried to Live CD the Karmic.  After many black screens with flashing underscore cursor, and text scrolling up and down the screen (can't remember what any of it was) it finally came up, but didn't work all that great, I couldn't get the wifi card to work, I didn't have audio, it was depressing.  Then I tried the Live CD of 8.04 (Hardy) still had wifi problems, and a webcam problem (Logitech Quickcam for Notebooks).  Tried 8.10 Live CD...no go.  Finally put Jaunty back on...it works, but the only problem I am still facing is the webcam...finally, my questions...

1.  Is there any tricks to get Karmic to install properly on my desktop (dell dimension 8400)???  Just let me know what info you will need from me and I will gladly post it, I would really like to get Karmic on both computers.

2.  If I can't install Karmic, how can I get this webcam working (btw, it works perfectly fine on 9.10 on the lappy, no problems at all)  on 9.04 it shows in lsusb (046d:09c1) but doesn't show up as /dev/video0 or anything, it just doesn't show in the /dev folder at all.  Cheese won't find it and neither will Skype.  Can I try anything to get it working???

Sorry for the long post, but I wanted to let you know that I am newbie, but have done more playing and searching and fixing most of my own problems than most newbies have probably done...I really hate asking questions, because I love to find answers on my own, I just can't do it on this one (or two).  Thanks in advance for your help.

wingrider78

---

### Post by wingrider78 on 2009-12-03
Okay, so I did some more playing around...I figured I would put my Live CD of Jaunty in my laptop and see if the webcam would still work with this distro...and it does!!!  So the webcam will work in jaunty out of the box for some reason on my lappy, but not the desktop...The laptop is a 64bit machine, but running the 32bit version of Karmic (installed) and the 32bit version of Jaunty (Live CD) and the webcam works.  The desktop is 32bit and running 32bit Jaunty (installed side by side with winxp, but on separate hard drives) and the webcam does not work.  

I was, however, able to get it to work after reading a thread about this camera needing to be plugged in before booting up the computer.  This kind of works.  I can get the video to work in gstreamer-properties (about 25 percent of the time) otherwise it gives errors in the terminal window.  It also works about 25 percent of the time running cheese.  I haven't been able to get it to work at all in skype.  It shows the /dev/video0 in the drop down list, but when I click test, nothing happens, the test button doesn't even go away.

Any suggestions???

---

