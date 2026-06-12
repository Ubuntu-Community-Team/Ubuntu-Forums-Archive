---
title: "Change Refresh Rate..Going Insane..Please Help"
date: 2009-10-30
forum: General Help
---

### Post by mikeymo on 2009-10-30
Hi guys. For a while now I've been using Ubuntu on and off.(Yes, I'm a Winders user) I would REALLY like to switch over to Ubuntu exclusively but there are a couple of things that I can't resolve that are driving me crazy. The main one is the refresh rate. I started off with Ubuntu 9.04 RC and it gave me a choice of different refresh rates. Everything was cool. Then I switched to 9.04 Release and no choice. It was stuck at 75HZ which gives me shimmering edges and a headache. I just switched to 9.10 and same deal..stuck at 75HZ. Even pulling it back to 72HZ or 70HZ stops the shimmering. (In Windows, it gives me from 60HZ-75HZ choice.) I've tried every method I can find and nothing works. There is no xorg.conf file, sudo dpkg-reconfigure xserver-xorg does nothing whatsoever, so what I want to know is this. Is there a file in 9.10 that I can manually edit to change the available refresh rates? If there isn't, how in Heaven's name do I change this? I hate that this one thing is keeping me from switching over..but it is. I've been worrying with this since 9.04 so somebody please help me before I'm bald. 
(PS..I'm not a "noob" or a "novice" with working at the command line level so you don't have to hold my hand....much)..Thanks

---

### Post by Giblet5 on 2009-10-30
Let me guess: you're using a monitor v a laptop, right?

If so, that noise around the edges of things is due to noise leaking through the shield on your video cable.

At 75Hz, the cable is starting to lose signal and the electro-magnetic interference created by your PC is becoming a more significant percentage of the overall video signal.

At 70Hz, the real video signal reaching the monitor is higher and the noise is mostly rejected. There will still be noise but it won't be as obnoxious.

An analogy:
Turn your TV up all the way. Now tap your foot. Can you hear your foot tapping? Now turn the TV down to half volume and try it...

I buy Belkin cables. They cost more but they perform better.

Go to a computer store. Tell a salesperson what's happening and that you'd like to *try* a good cable, but you want to bring it back if it doesn't solve the problem.

That way, it's no risk.

Your eyes will be happier with a 75Hz refresh and a clean video signal.

---

### Post by mikeymo on 2009-10-30
Well dog my cat....it worked. 25 years in the electronics and computer service industry and I never thought about the cable. Oh well...42 going on 92. What can you do...It's actually a desktop PC but same principle. Giblet5...you are da man. Looks like it's time to tell Bill to hit the bricks. Thanks for your help. I am grateful.

---

