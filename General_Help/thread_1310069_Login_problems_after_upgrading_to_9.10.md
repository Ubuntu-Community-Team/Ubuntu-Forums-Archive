---
title: "Login problems after upgrading to 9.10"
date: 2009-11-01
forum: General Help
---

### Post by wrgb2 on 2009-11-01
I am running a Beta 9.10 version of Xubuntu that was upgraded to 9.10-by applying updates on the day of the release.  After the ubdate, about 75% of the time, when I try to log in, I get the boot up splash screen with the bubbles floating around for a bit, then I get an error screen -- all I have time to see is "Error - lockup ,...Error space 65520" (listed several times with different numbers), I can't catch the rest of the error message, then it displays the splash screen with the bubbles again and takes me back to the login screen.   I sometimes have to do this 2 or 3 times before I can get logged in.  This wasn't happening before update day, and I'm positive I'm typing my password in correctly. I'm running the Xfce desktop.  Anyone else have this problem or know what might be causing it?

Thanks,
Randy

---

### Post by Brandon Williams on 2009-11-01
I'm having a similar problem. I opened [this bug](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/461277). Please take a look and mark the bug confirmed if it looks like the same thing that you're experiencing.

Unfortunately, the only thing I've found that seems to help is to wait a bit before logging in. It seems that some element of X isn't fully initialized if I try to log in too quickly.

---

### Post by wrgb2 on 2009-11-02
Hey Brandon,

Thanks for the reply.  After looking at the forum thread associated with the bug, I deleted my xfce4 .config folder and that seems to have fixed it.  I've since changed the screen resolution, and I'm still able to log in ok.  Hopefully it won't crop up again as I change other settings.

Appreciate the help,
Randy

---

### Post by Brandon Williams on 2009-11-04
Thanks for the update Randy!

I tried the method you suggested, and it appears to have resolved the problem for me, too. I can't figure out why, though. As far as I can tell, me settings now are the same as they were before ... at least that's what diff -r tells me.

It would be nice to have a tidy explanation, but I'm much happier with mysteriously fixed than I was with mysteriously broken :-)

---

### Post by PendoLeMellon on 2009-11-15
I have the exact same problem with xubuntu 9.10 on an old Dell Optiplex GX150. In the beginning I managed to login after a couple of retries, but later on I couldn't login at all. Maybe I could login at first because I waited longer?

After reading some forum threads, I deleted the config folder, and then I could successfully login again.[INDENT]I'm still a little bit new to (x)ubuntu, and I couldn't find the config folder at first. I managed to delete it by typing "sudo rm -r ~/.config", so I guess it's in a hidden folder at the root or something?
[/INDENT]I discovered that the problem arises when I change the desktop resolution. Xubuntu automatically selects 1600 x 1200 @ 60 Hz (the maximum resolution), and that is too small for a 19" crt monitor.

If I don't change the resolution, I can login fine. So, now that we probably know the cause for the problem, does anybody know how to fix it?

---

### Post by PendoLeMellon on 2009-11-23
I read this thread:

**Xubuntu login problem**
[http://ubuntuforums.org/showthread.php?t=1317265](http://ubuntuforums.org/showthread.php?t=1317265)

... and I went to *Applications > System > Updates > Preferences* and enabled *"pre-released updates (karmic-proposed)"*.

These updates can be a little bit unstable and risky, so I deactived them again after running the update procedure once. I have now rebooted and logged in successfully twice (with my preferred desktop resolution), so the problem seems to be fixed.

---

### Post by peyre on 2009-12-01
That's great PendoLeMellon, but how are we to do that when we can't log in to X in the first place?

---

### Post by black28 on 2009-12-11
how do you guys delete the xfce4 config folder? i did the code in terminal "sudo rm -r ~/.config" it asks for password then does nothing. how can i check? i'm gettin the lockup prob too.

---

### Post by wilytm on 2010-02-26
Hi, I'm getting the login problem too.

XUbuntu 9.10 installed yesterday 2010-02-26

Problem description: After applying all the updates I cannot login at all. I'm stuck in an endless loop. I select my account and give the pw and then some messages flash by on the screen and I end up back at the login screen to do it all over again.

Note I'm using an old IBM CRT and have set the resolution smaller than what the install gave me (I set it to 1024 x 768)

After reading these posts I have a fix:
On start-up press ctrl-alt-f1 every couple of seconds until a text based login screen appears. (If it dosen't re-boot and try again.)
login and give pw. (I had to use all lower case to login here.)
Type: sudo rm -r ~/.config
Type: exit
Power down computer
Turn on computer and login!!!

NOTE:
The login the screen resolution will be set to the Xubuntu default which is unpleasant on my old small 17" IBM CRT, and if I change it back to 1024 x 768 the login problem will re-occur!!!

NOTE:
At one point I managed to stop the screen when the text messages were flying by. Here is what was showing:

Ubuntu desktop 9.10 xxxxx-desktop tty1
xxxxx-desktop login: [   60.420031] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[60.420103] [drm:i810_wait_ring] *ERROR* lockup

I think its some sort of storage allocation problem. The program has 65520, and it wants 65528.

I think it might be due to a programmers type-o Zero and eight look the same if the zero has a stroke through it.

HEY:
How about someone fixes this up!!! Its a high priority bug. It dosen't seem to hard to do.

BYE

---

### Post by casperl on 2010-03-20
> How about someone fixes this up!!! Its a high priority bug. It dosen't seem to hard to do.

Four, five months after the launch of 9.10 I have moved over.  

BIG MISTAKE!

This and other bugs are certainly not fixed and nobody seems to care.

The point has been reached where the relentless 6 month upgrade cycle of Ubuntu is a major drain on my productivity.  Either I stick to older versions, LTS (and be stuck with obsolete versions of old packages), or I am investigating a different Linux distro - Suse maybe.

Not fixing priority bugs is a HUGE no-no in my book, and if nobody cares then I am out of here.  And yes, not being able to log in is about as big a bug as they come...

---

