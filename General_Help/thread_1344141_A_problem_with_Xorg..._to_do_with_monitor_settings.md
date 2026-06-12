---
title: "A problem with Xorg... to do with monitor settings and Failsafe mode - help!"
date: 2009-12-02
forum: General Help
---

### Post by hoppipolla on 2009-12-02
Well, here I am... posting this from "Links" in the prompt!! lol :(

So basically... I booted up my PC at approximately 3:46 today (the time of the last Xorg log file in /var/logs, and since then it has been writing to it's failsafe log file, implying it is trying to start X in Failsafe mode. It then quickly  fails as the monitor gives it's message to say the signal is over it's range (I forget the exact message, but it's words to that effect!).

I always do get these errors when I try to do things like running games, I think it's something to do with the Horizontal Sync and Vertical Refresh values for my monitor being incorrect, as sometimes it fails to display resolutions that should be within it's range, such as 800x600.

So... what should I do? :(  I have been hunting around for a way to tell X to boot normally as opposed to in Failsafe, but I'm not sure how to do this. I also tried startx as root and as my own user, but both often seem to fail. I also tried adding fairly conservative but reasonable HorizSync and VertRefresh lines to my Xorg.conf to correct the eroneous values that seem to be held by RandR or the Nvidia drivers or Vesa or whatever it is that is getting my monitor wrong... but this made no difference :(

I would post my Xorg.conf but I can't copy and paste in the prompt lol, basically it says my monitor is "Configured Monitor" and then I put my Horiz and Vert lines, and that's it, I don't think there's anything else of significance.

Thanks so much, this has properly got me stumped! I'd imagine the first best thing to do is tell it to stop starting X in Failsafe on boot, or somehow set new settings for my monitor for RandR, Nvidia and Vesa to follow, but I don't know how to do either :(

Thanks,

Hoppi! :)


PS, oh I selected "Ubuntu" for the type of thread as that's what I use, but I do use KDM and KDE :)  Thanks!

---

### Post by NoaHall on 2009-12-02
Oh, you're using Nvidia card? You never said that xD 
Try ```
 sudo nvidia-xconfig
```
And if that fails, maybe ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hoppipolla on 2009-12-02
It works!! IT WORKS!!!

The fix was actually a bit unusual.

What I did, was go into my xorg.conf and make sure the Horizontal Sync and Vertical Refresh for my monitor, depths and modes were all set ok, I checked the file over a few times, then I later learned about xorg.conf.failsafe so I fixed that up too!

Then I wiped it's log files for some reason (the Xorg ones)... and done! It all works! I think having both files at adequate settings just sorted out all problems, and maybe wiping the log files made it forget about the previous problems!

Anyway, yippeeeee! And thanks for the help as well Noah, those commands were actually useful as the Nvidia Xorg gave me some great pointers!

Peace out all and yay I'm back on Linux!!


Hoppi :)

---

