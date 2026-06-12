---
title: "Ubuntu 9.10 crashes on HP NC6000"
date: 2009-11-02
forum: General Help
---

### Post by bowgart on 2009-11-02
I have just installed unbuntu 9.10 onto my HP NC6000 and it freezes just prior to the main screen opening.  When I try to run it from the live cd environment the freeze occurs when the main screen appears.  I am a novice at Linux, but I have successfully install 8.04 on my Toshiba satellite S1800-412 so have limited knowledge. I have tested the install CD and it checks out ok.   I was wondering if anyone have suffered a similar problem and if so is there a solution?

---

### Post by absolutepressure on 2009-11-02
I've got a similar problem.  I was running 9.04 as a dual boot, upgraded to 9.10, and now all of a sudden it says my hard drive "has many bad sectors," that it could crash, and I should replace the hdd.  I booted up in windows, and it didn't think anything was wrong, so it must all be in my linux partitions.  Well, ubuntu crashed today when I was on the irc trying to get help.  Also, after the upgrade, if it goes into suspend, it won't come out.  And, I still can't figure out the keyring password reset.  I'm pretty close to becoming a mac user.  I hate windows, and now Ubuntu is giving me just as much, if not more grief.  I am very disappointed with the Koala.

---

### Post by absolutepressure on 2009-11-02
Well, after looking at all the problems people are having with 9.10, I followed some sound advice and did a fresh install of 9.04 and will wait for a newer version that works, if I ever want to switch, that is.  I'm back to 9.04, and it's smooth as ever!  The fresh install to 90% of how I had it before the update took less time than trying to fix one of the 9.10 problems.  Oh, and reformatting the hdd linux partitions got rid of the "bad sectors" deal.  Those, I believe were definately caused by 9.10.  My advice, unless it went perfectly smooth for you, don't mess with it and go back to 9.04.  If you haven't upgraded yet, DON'T.  Not until the problems have been fixed.

-I'm out, peace!

---

### Post by bowgart on 2009-11-03
> **absolutepressure said:**
> Well, after looking at all the problems people are having with 9.10, I followed some sound advice and did a fresh install of 9.04 and will wait for a newer version that works, if I ever want to switch, that is.  I'm back to 9.04, and it's smooth as ever!  The fresh install to 90% of how I had it before the update took less time than trying to fix one of the 9.10 problems.  Oh, and reformatting the hdd linux partitions got rid of the "bad sectors" deal.  Those, I believe were definately caused by 9.10.  My advice, unless it went perfectly smooth for you, don't mess with it and go back to 9.04.  If you haven't upgraded yet, DON'T.  Not until the problems have been fixed.

-I'm out, peace!
[SIZE=4][FONT=Century Gothic]

[SIZE=3]Thank you very much, I will follow your lead on this and install 9.04 over 9.10 if that's possible.[/SIZE][/FONT][/SIZE]

---

### Post by mjbright on 2009-11-05
I installed Ubuntu 9.10 on my HP nc6000 3 days ago.
The only problem I've encountered is that it didn't come back from Suspend, or Hibernate, the 1 time I tried them ... so I had to cold boot.
Otherwise, it's been great so far.
:popcorn:

I have WiFi, Gnome/X11, Sound/Video (after Medibuntu setup) and sound buttons working out of the box.
I have 2GBy RAM and an 160GBy hard disk.

---

### Post by astowe32 on 2010-03-11
Anyone brave enough to retry this upgrade on the NC6000? I am still on 9.0.4 without issue and see very little updates in the bug reporting site on the hibernate freeze issues.

  Allen...

---

### Post by Craigwell on 2010-04-18
I am running 9.10 on my nc6230 without problems, with one exception:

If i suspend to ram, it works fine, and will resume ok - BUT the main display or LVDS comes up garbled, with no alternative but to reboot. I can do this by ctrl-alt-f1, and then ctrl-alt-del, so not a real bad deal. 

The interesting part: If I have a secondary display attached - which i often do at home - the secondary display works fine upon resume, while the main display is garbled. 

I have yet to try different video drivers, but I will and report back.

---

### Post by solorize on 2010-05-15
I also have a problem running ubuntu & xubuntu on my Hp NC6000.

I start my laptop and it goes through BIOS etc.. and then just sits
there with an underscore cursor blinking in the top left of a black screen.

Sometimes it will eventually get to the main login screen, but most of the
time it just sits there..

I had a similar problem with windows on the same machine before I installed Linux, where it would not boot into the OS. I found out that it was because my Hard Drive was running in DMA mode, and I had to switch it to "pio only"and then Windows would load everytime! 

So I thought it may have something to do with the same problem, but under Ubuntu... you can read my thread here:
[http://ubuntuforums.org/showthread.php?t=1481503]("http://ubuntuforums.org/showthread.php?t=1481503")

But I have still unfortunately not sorted the problem out.

I also thought that it may have something to do with the Wi Fi
which did sort the problem out for a while and allowed me to actually
get into Ubuntu every so often...
My thread here: [http://ubuntuforums.org/showthread.php?t=1420422]("http://ubuntuforums.org/showthread.php?t=1420422")

Dont know if any of the above will help you, but you can see what sort of
problems I am having with Linux on my HP NC6000.

I have two Hard drives, which I switch in and out of the laptop. one with Win XP on which works all the time, and the other has Xubuntu on which is the one I really want to keep in as I enjoy linux more than Win OS.

Side Note:
Sometimes, if I cant boot into Xubuntu, if I take my hard drive out and then put it back in it will load up straight away! which is odd.

Hopefully with future updates etc.. it may make linux on the HP NC6000 more stable.

Regards

Mark

---

### Post by solorize on 2010-05-28
Does anyone else who has Ubuntu or Xubuntu installed on a
**HP NC6000** laptop have problems booting into the OS?


I am still having the problem of:

[I]I start my laptop and it goes through BIOS etc.. and then
just sits there with an underscore cursor blinking in the top
left of a black screen and does not load into the OS.[/I]

The above happens intermittently, sometimes it loads into the OS
and other times I have to keep powering off and trying over and
over again.


I am now running **Xubuntu 10.04**. and am still having the above
happen.

If anyone have any idea what could be wrong or how to best
trouble shoot the problem I would be grateful to hear from you.

---

