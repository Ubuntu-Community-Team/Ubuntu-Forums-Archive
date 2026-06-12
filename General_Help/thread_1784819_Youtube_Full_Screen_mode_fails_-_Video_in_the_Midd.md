---
title: "Youtube Full Screen mode fails - Video in the Middle"
date: 2011-06-17
forum: General Help
---

### Post by apollothethird on 2011-06-17
Youtube full screen doesn't work properly.  When clicking on the button for full screen I get a partial screen in the middle.

This only happens on one of my Ubuntu 11.04 systems in my network.  The other machines shows the Full screen videos ok.

I tried it in the following environment modes, Ubuntu, Ubuntu Classic and Ubuntu 2D.

It's probably something to do with my video card.  I'm running the nVidia GeForce GX 260.  The current driver version is 270.41.06.  I had tested an experimental version and reverted back to this one.  This is the driver version set as recommended in the “Additional Drivers” program of the system's menu.

Thanks in advance for anyone with suggestions of how to fix this.

-- L. D. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Joe- on 2011-06-17
So are you saying the when you put the video into full screen mode the video just doesn't fit the whole of the screen? Does changing the quality of the video on YouTube help?

---

### Post by apollothethird on 2011-06-17
> **Joe- said:**
> So are you saying the when you put the video into full screen mode the video just doesn't fit the whole of the screen? Does changing the quality of the video on YouTube help?

Yes.  The only way I can get a good fit is to right click on the video and choose the Pop out option.  Once it's popped out I can toggle maximise, and get a fuller session.  However, it's different from the full screen that shows on all my other machines, as well as in Windows.

The quality modes doesn't change anything except for the quality.  The full screen doesn't work.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Joe- on 2011-06-19
Ok then.

Does is do this for every video you watch on that computer?
What happens if you go to this page [http://www.youtube.com/account_playback](http://www.youtube.com/account_playback) ? (YT Account required). Can you change the options there?
If you right click anywhere on the video and go settings can you enable hardware accerleration? See picture:

Hope this might help

---

### Post by apollothethird on 2011-06-19
> **Joe- said:**
> Ok then.

Does is do this for every video you watch on that computer?
What happens if you go to this page [http://www.youtube.com/account_playback](http://www.youtube.com/account_playback) ? (YT Account required). Can you change the options there?
If you right click anywhere on the video and go settings can you enable hardware accerleration? See picture:

Hope this might help

It happens with all youtube videos.  I didn't signin to the account link you gave me because the screen appeared to be suggesting that I'd have to sign in always to view videos.  Other people besides me use the computer and won't be able to sign in using my account.  I don't want to break the normal operation of youtube viewing.

Signing in with a youtube account has never been a full screen requirement for any other installation.  If it's a problem with this installation I'd have to settle without being able to use full screen until this requirement is removed.

Again, I have 6 computers running Lnux in my local network.  This is the only computer that will not play any of the videos in full screen.  I have never had to do anything special with any of the other computers.  I also haven't had to pick out special videos to play in full screen.  All of them will play in full screen on all my other computers.  None of them will play in full screen on this computer.

As far as I can see, the only significant difference is the video card (nvideo GX260).  I'll be replacing it sometime in the future and will let you know if the full screen option becomes functional.

I have already tried three driver downloads, and am not currently using the one that the additional drivers program specified as recommended (Driver Version 270.41.06).

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2011-08-03
This issue was resolved by removing the Adobe Flash player and using gnash/broswer-plugin-gnash instead.

Thanks kindly to everyone who contributed to this thread, as well as those who read it and pondered or did any research to look for a resolution.

I guess in this case the Adobe Flash player isn't compatible with my video card.  I tried many variations of xorg.conf settings, video card drivers and driver settings, various web browsers, to no avail.  The gnash application did the trick.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2012-01-01
I found another fix for this problem.

While gnash is a good alternative, it's a big resource hungry application.

The issue is a adobe flash bug and is resolved with the following fix:

```

sudo mkdir /etc/adobe
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

```I'm very surprised the the bug, so prevalent in my environment is referenced in this forum except in this thread.  Every time there has been a Linux Adobe update, nVidia update, Ubuntu version update, I've installed it and quickly tested Youtube and experienced the same bug.  Maybe others are just contending to live with the blemished video.  But I'm glad to have finally got it working correctly.

When I get some time I'll start to contribute the fixes I'm discovering to the [https://help.ubuntu.com/community](https://help.ubuntu.com/community) documentation.

Thanks again for all who read and would have contributed a resolution had you experienced it or understood the problem, as well to all the other help I continue to receive from this community.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

