---
title: "Aargh! Crash and system now failing"
date: 2009-12-29
forum: General Help
---

### Post by tiggsy on 2009-12-29
Using Karmic Koala on a 32 bit system.

About a week ago, my screen suddenly went gray and everything stopped working (though the power was still running to the fans). I had no choice but to power down. Just before the crash happened there was this noise like the drive had ejected. A quick glance showed it closed, so I walked over and looked. It was closed. I was surprised, but didn't realize it was anything but a wierd noise... I was listening to the BBC iPlayer in a Firefox window and playing cards. I had another Firefox window open with around 30 tabs. I can't recall if anything else was running. If so, possibly Thunderbird and maybe Gedit as well and Tweetdeck for sure, probably Pidgin and Kalarm (yeah, I do run a lot of stuff at once).

I tried to restart but the system didn't get all the way through the boot process before the power seemed to go down, apart from the fans. I tried booting from the CD, and it got so far, but again did not complete the boot process.

I spent a bit of time researching what had happened and it seemed that the RAM might have blown so I found a supplier and bought 2gb of new RAM, which I just replaced (previously I had 1gb). This is DDR DIMM so pretty expensive.

Now it boots, but I'm getting error messages and the boot doesn't get to the desktop. The initial Ubuntu boot splash shows, then it drops to a display of the steps it's taking (I don't generally see this).

Here are the messages that came up as FAIL in the list:

```
Kernel log daemon
Unable to start /sbin/klogd 
Permission denied (Permission denied)

Avahim-DNS/SD Daemon avahi-daemon 
Timeout reached while waiting for return value
Could not receive return value from daemon process

MySQL database server myqlsd 
[no explanatory messages]
```

Then there's a red asterisk next to
```
No suitable module for running kernel found
```

It took quite a while to continue, but eventually asked me to log in, but after that there didn't seem to be much i could do (it didn't log into the GUI), so I started researching this on here, and then the screen went gray again and there was no response so I closed down with the big button. The closedown seemed reasonably normal (the screen woke up at this point).

I have read that ```
chmod / 755
``` might make the kernel work, but don't know how to use this command without access to a terminal (or is the space I logged in to effectively a terminal?)

Please help!! I've been offline for too long, except for this backup machine which has no space, so i can't even watch an online vid.

---

### Post by tiggsy on 2009-12-29
I still have some problems, but can get into the system now. But I have to boot from the 1st hard disk (which has hardy installed, and which crashed with similar problems some time back), I found that the place I logged into was indeed a terminal, so I did ```
sudo chmod 755 /
``` which seems to have fixed the first disk - but not the second. 

I just tried to boot to the second disk (which has karmic installed), and it hangs after all those messages - with a black screen. I just tried rebooting, It waited 30 seconds to load the grub, then i got a screen with about the top third black, two thick stripes of that pinky color ?magenta ?cyan I have no idea. its sort of pinky purple, then under that the whole screen is that color. 

So now, I have to use the CD to boot.

---

