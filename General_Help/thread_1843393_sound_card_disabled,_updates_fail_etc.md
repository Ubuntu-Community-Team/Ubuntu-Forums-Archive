---
title: "sound card disabled, updates fail etc"
date: 2011-09-13
forum: General Help
---

### Post by beansdad on 2011-09-13
Please help. My desktop has been gradually getting worse over the last few months since I re-installed 10.10 on a bigger hard drive added a soundblaster card and Geforce video card to drive 2 monitors. It all worked fine but I then lost the use of the sound card and couldn't get it working again whatever I tried so I gave up & went back to the built in sound on the motherboard. After a while, updates started to fail and couldn't be corrected. Eventually no updates would work as Opera was trying (& failing) to update first and this stopped all other updates even trying.

I tried a complete install of 11.04 but this also kept failing saying it was either the installation CD, CD/DVD reader or hard drive. In desperation I replaced the hard drive & DVD writer and used another installation CD produced on my laptop. This also gave me grief with files failing to install and repeated error messages. Eventually I got a working version of 11.04 and started to set it up for the way I wanted to work.

During a lunch break with a shut down and restart, the sound card again stopped working. I then uninstalled Audacity (the last thing I'd done) and now nothing works.

I'm getting seriously fed up with working to get the system to work and not achieving anything I need to do which is precisely why I moved away from m$ years ago.

Can anyone suggest why I'm getting all this grief and how I can overcome it to get a system that actually does what it's supposed to?:confused:

---

### Post by Elfy on 2011-09-13
Have you managed to at least get it to boot again? 

If so have you looked in the log file viewer at any logs? I'd start there. 

If you can't boot - you should be able to view them from within a livecd. 

Is the update situation dealt with following the reinstall?

---

### Post by beansdad on 2011-09-13
Lost it completely so have done a complete re-install. Now I have Update Manager telling me that 230 updates have been selected but when I try to install these it fails immediately saying there are errors. when I try to run upgrade in terminal it fails telling me that /var/lib/dpkg/available has errors. Couldn't correct these so I've deleted the file. Now update refuses as the file isn't there anymore.

Can't face, or see any point in](*,) doing a re-install for about the tenth time!

---

### Post by beansdad on 2011-09-13
Managed to rename /var/lib/dpkg/available-old to available and updating then worked without errors!

Am now nervous about losing sound card again and suspect this happens when I install a new player such as Amarok, Audacity or Rhythmbox. Any ideas on how to stop the soundblaster stopping working?

---

### Post by Elfy on 2011-09-14
I've never had my soundcard stop working due to installing software. 

I'd run aplay -l save the output to a file and then install the music player and see what happened.

If it stops working you could look at the first post here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I'd also look in messages in the log file viewer. 

You don't say if you've looked at alsamixer previously - you could just need to reset levels, I know that in the past the first thing I've needed to do with my audigy was to turn of the digital ouput.

---

### Post by beansdad on 2011-09-14
Many thanks for support - I'll follow your advice tomorrow and just wait & see what happens.

Last time I tried to get the soundcard back I tried allsorts incl alsamixer and, from somewhere in the forums, got the impression that alsa could be causing the problem but never resolved it.

Still don't know why the system gave up doing updates properly or why the several tries at install with a new hard drive, new DVD writer & new install CD failed with error message about CD, DVD writer or hard drive being the problem, but eventually allowed a clean install which then gave the update prob previously mentioned. Have now got a UPS as we get lots of blips on supply and also wondered if the broadband is unclean or noisy causing problems, guess I'll never know.

Think I'd better mark this one as solved and see what happens.

Thanks again.

This forum has saved my sanity several times.

---

