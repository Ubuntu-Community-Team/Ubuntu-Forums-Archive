---
title: "Can't log in to Ubuntu 10.04"
date: 2010-06-30
forum: General Help
---

### Post by dfrankow on 2010-06-30
I've been running 10.04 on a partition of my Dell laptop successfully for weeks. Now, I get the login screen, and when I give my username and password and click "Ok" it logs in, looks like X starts, then immediately goes back to the login screen with the drum sound (is that a bell?). If I type the wrong password, it doesn't log in, so I know it's getting past authentication.

I've tried logging in as one of several users.

I've tried running in recovery mode and running "clean", running "repair packages" (it downloaded and installed a lot of packages), running in safe graphics mode (failsafeX). None of those had any effect.

I've tried looking in /var/adm/messages and looking at X logs that are presented in safe graphics mode. I see tons of stuff, and none of it obviously stands out as an error.

It is likely almost out of disk (maybe 300M left?), but I can't find evidence that that is causing this problem.

I'd like to somehow repair my Ubuntu install without wiping it.

Any advice?

---

### Post by wilee-nilee on 2010-06-30
Not sure of the problem but you can reset the password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I just noticed the disc space, that is probably the problem, never use more then 3/4 of the disc space unless it's a emergency. Log files will take up the rest without you knowing it when your down to such a small amount of free space . Clean out with a live cd to a external source to begin with.

---

### Post by warfacegod on 2010-06-30
I've always read that 5 -10% of an HDD should be left open not 25%. Regardless, cleaning out some things would be a good idea. I can see how a full HDD could stop you from logging in. However, over the last several days, I have seen around a dozen other Threads with essentially identical symptoms. I suspect a buggy update is to blame. It seems like there are more and more of those, as of late. Try booting with an older Kernel if you have one available in GRUB.

---

### Post by Seanlol on 2010-06-30
> **warfacegod said:**
> I've always read that 5 -10% of an HDD should be left open not 25%. Regardless, cleaning out somethings would be a good idea. I can see how a full HDD could stop you from logging in. However, over the last several days, I have seen around a dozen other Threads with essentially identical symptoms. I suspect a buggy update is to blame. It seems like there are more and more of those, as of late. Try booting with an older Kernel if you have one available in GRUB.

300M is still way, way less than 5% of the drive unless he's using a 3-6 GB drive.

---

### Post by warfacegod on 2010-06-30
> **Seanlol said:**
> 300M is still way, way less than 5% of the drive unless he's using a 3-6 GB drive.

Sure is. That's why I also posted this: "Regardless, cleaning out some things would be a good idea."

---

### Post by wilee-nilee on 2010-06-30
Personally I just use the computer to run multiple OS, and use a external for the rest. With externals being so cheap it is a good safety measure to never lose anything and reinstall at a whim whatever I want, but that's just my personal choice. I load some things onto the computer but not much.

---

### Post by warfacegod on 2010-06-30
I keep a separate /home partition as an additional cushion against screw ups in addition to using an External. If I break one of my OS's, my stuff is safe and cozy in it's own partition, no worries. Besides, I'm on a laptop. I can't be worrying about dragging around an extra HDD every time I stand up and wander off or leave my house.

---

### Post by wilee-nilee on 2010-06-30
> **warfacegod said:**
> I keep a separate /home partition as an additional cushion against screw ups in addition to using an External. If I break one of my OS's, my stuff is safe and cozy in it's own partition, no worries. Besides, I'm on a laptop. I can't be worrying about dragging around an extra HDD every time I stand up and wander off or leave my house.

I use a netbook I just hardly never need to take it anywhere, if I leave my apt, it's to get away from the computer at times. The seperate home is a good idea many use it, but I have never seen the need personally.

I also have two other laptops and a desktop so if I want to use any of them I just plug the external in and go.

---

### Post by dfrankow on 2010-07-01
> **wilee-nilee said:**
> Not sure of the problem but you can reset the password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I just noticed the disc space, that is probably the problem, never use more then 3/4 of the disc space unless it's a emergency. Log files will take up the rest without you knowing it when your down to such a small amount of free space . Clean out with a live cd to a external source to begin with.

It's an old machine with a 40G drive, mostly taken up by Windows (can't change that). So the Ubuntu partition has 8G I think. I've tried cleaning out everything I know how, removing packages and so on. I don't know how to clean more.

More importantly, I'd like some honest-to-god evidence that it's the problem. I can log in just fine through the recovery process as long as I don't start X. What symptoms can I check for?

---

