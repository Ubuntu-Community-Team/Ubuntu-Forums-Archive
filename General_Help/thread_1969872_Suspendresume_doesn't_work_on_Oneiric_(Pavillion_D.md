---
title: "Suspend/resume doesn't work on Oneiric (Pavillion DM4)"
date: 2012-04-30
forum: General Help
---

### Post by mfpompadour on 2012-04-30
I upgraded to Oneiric on a Pavillion DM4 laptop.

Now, suspend/resume doesn't work.

When I close my laptop and open it, I have a black screen. The power light is on, but I cannot resume my work and have to hard shutdown with the power button.

How do I get suspend/resume working? How would I troubleshoot this?

This may be related to how I can't boot except with Recovery + Resume: [http://ubuntuforums.org/showthread.php?t=1928848](http://ubuntuforums.org/showthread.php?t=1928848)

---

### Post by znorris on 2012-04-30
I've had the same suspend and resume issues with my Dell Studio 1569. On top of which I've had general stability issues. Everything freezing, screen going black and freezing... Is this common with 12.04? For a LTS this appears to be the most unstable version of Ubuntu yet.

---

### Post by mfpompadour on 2012-04-30
> **znorris said:**
> I've had the same suspend and resume issues with my Dell Studio 1569. On top of which I've had general stability issues. Everything freezing, screen going black and freezing... Is this common with 12.04? For a LTS this appears to be the most unstable version of Ubuntu yet.

I have this problem with Oneiric, not 12.04.

---

### Post by BlueAZ on 2012-05-02
[SIZE=3]Hi,   I also have this problem.  Running 11.10 Oneiric on new AMD quad-core desktop.  Trying to suspend or hibernate just shuts the computer down.  Then when I restart, some settings are messed up.  Does anyone have a solution?
I tried a utility offered by Software Center called 'smartly shut down....'  This utility crashed my computer & I had to wipe & reinstall Oneiric.  So I don't recommend that!
[/SIZE]

---

### Post by Stovey on 2012-05-02
Hi Everyone!!

I have the same problem.  I shut the lid, but when I open it up I get a black screen.  And I can't shutdown with the power button.  This must be a real bug.

Pangolin 12.04, Acer 1810T.

---

### Post by mfpompadour on 2012-05-04
> **Stovey said:**
> Hi Everyone!!

I have the same problem.  I shut the lid, but when I open it up I get a black screen.  And I can't shutdown with the power button.  This must be a real bug.

Pangolin 12.04, Acer 1810T.


I know that Hibernate (but not Sleep) is disabled by default in 12.04: [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

I wonder if I should upgrade my 11.10 to 12.04, or whether I will have more problems in 12.04.

Regardless, I want suspend / resume to work.

---

### Post by Ubun2to on 2012-05-04
> **Stovey said:**
> Hi Everyone!!

I have the same problem.  I shut the lid, but when I open it up I get a black screen.  And I can't shutdown with the power button.  This must be a real bug.

Pangolin 12.04, Acer 1810T.

Well, just let the battery drain is one option. There is no possible way it can override that (unless it has the ability to break the fourth wall). Have you tried doing a hard reboot/shutdown and waiting 30 minutes to an hour? That's what I had to do.
Try using a virtual machine (like the free and open source Oracle VM VirtualBox-it may be a bit unstable, but it still works great) with Ubuntu if this persists, or downgrade-that's what I used before deciding to upgrade to LTS (it may be crappy, but I haven't run into as many bugs as lots of other people have).

---

