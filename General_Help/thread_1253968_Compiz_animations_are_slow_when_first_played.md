---
title: "Compiz animations are slow when first played"
date: 2009-08-30
forum: General Help
---

### Post by LifeEnemy on 2009-08-30
I have Compiz Fusion running on Jaunty, and I really like the window animations that I've set up. My only problem is, some of the animations run slow sometimes when they play for the first time, but afterwards they work fine. The animations will run slow again is they don't appear for a few minutes after being used last. It's the most obvious using the "burn" animation, especially on larger windows.

Thanks for any help!

---

### Post by chriskin on 2009-08-30
> **LifeEnemy said:**
> I have Compiz Fusion running on Jaunty, and I really like the window animations that I've set up. My only problem is, some of the animations run slow sometimes when they play for the first time, but afterwards they work fine. The animations will run slow again is they don't appear for a few minutes after being used last. It's the most obvious using the "burn" animation, especially on larger windows.

Thanks for any help!

can you tell us your graphics card?

the burn animation can be sometimes be a little slow even on newer models

---

### Post by tgeer43 on 2009-08-30
By 'run slow' do you mean that there is a delay between the time that you click and the time that the animation begins?

If so, and you are using an ATI Radeon based graphics card then this is related to a documented bug in Jaunty.

See my post in this thread for a workaround:

[http://ubuntuforums.org/showthread.php?t=1252990](http://ubuntuforums.org/showthread.php?t=1252990)

tgeer

---

### Post by LifeEnemy on 2009-08-30
> **tgeer43 said:**
> By 'run slow' do you mean that there is a delay between the time that you click and the time that the animation begins?

If so, and you are using an ATI Radeon based graphics card then this is related to a documented bug in Jaunty.

See my post in this thread for a workaround:

[http://ubuntuforums.org/showthread.php?t=1252990](http://ubuntuforums.org/showthread.php?t=1252990)

tgeer


Not quite. The animations start on time, but proceed slowly once started, but only sometimes as I described in my first post. I'm using a NVIDA GeForce 8400M GS on a Dell XPS M1530.

Thanks for the speedy responses so far :)

---

### Post by chriskin on 2009-08-30
> **LifeEnemy said:**
> Not quite. The animations start on time, but proceed slowly once started, but only sometimes as I described in my first post. I'm using a NVIDA GeForce 8400M GS on a Dell XPS M1530.

Thanks for the speedy responses so far :)

i have the 8600 of nvidia, and i saw a great change when i installed the 185 driver instead of the 180 default.

the 185 IS stable, it is just not included in ubuntu yet because of the feature freeze for jaunty. you can get it through envyng, which can be found in synaptic. even though it is stable, and it is supposed to work perfectly (it did for me at least and anyone else on the internet) i can't guarantee in any way that it will work for you, or that it will solve your problem like it did for me

---

### Post by tgeer43 on 2009-08-30
I have an 8600 as well but I'm still running the 180 driver. No slowdown issues whatsoever so it's unlikely to be a driver issue.

tgeer

---

### Post by chriskin on 2009-08-30
are you using the same effect though?

---

### Post by tgeer43 on 2009-08-30
If you mean am I currently using the 'burn' animation, then no. But I have tried it as well as all of the others.

tgeer

[edit] Just tried 'burn' again just to be sure - no slowdown problems.

---

### Post by LifeEnemy on 2009-08-31
> **chriskin said:**
> i have the 8600 of nvidia, and i saw a great change when i installed the 185 driver instead of the 180 default.

the 185 IS stable, it is just not included in ubuntu yet because of the feature freeze for jaunty. you can get it through envyng, which can be found in synaptic. even though it is stable, and it is supposed to work perfectly (it did for me at least and anyone else on the internet) i can't guarantee in any way that it will work for you, or that it will solve your problem like it did for me

I downloaded EnvyNG and the UI (envyng-qt i think), but it doesn't show the 185 driver. Just the 180 that I have and a few older ones.

---

### Post by chriskin on 2009-08-31
> **LifeEnemy said:**
> I downloaded EnvyNG and the UI (envyng-qt i think), but it doesn't show the 185 driver. Just the 180 that I have and a few older ones.

strange, i got the 185 from there :S

---

### Post by LifeEnemy on 2009-08-31
> **chriskin said:**
> strange, i got the 185 from there :S

Yeah. I just checked again, but no dice. It only has 180, 173, 96, and 71.

---

### Post by LifeEnemy on 2009-09-03
Still having trouble with this. It *looks* like my computer just can't handle the animation. But if other people with the same graphics card can do it, I don't see why I'm having this problem. If it matters, I have 3gb of RAM.

---

### Post by LifeEnemy on 2009-09-06
bump

---

### Post by LifeEnemy on 2009-09-20
Still having this problem. Not a big deal, but annoying nonetheless.

---

### Post by Tipped OuT on 2009-09-20
What do you mean by it's slow? Do you mean it's laggy?

---

### Post by LifeEnemy on 2009-09-20
As I said earlier, "The animations start on time, but proceed slowly once started..."

---

### Post by Tipped OuT on 2009-09-20
> **LifeEnemy said:**
> As I said earlier, "The animations start on time, but proceed slowly once started..."

Do you have your Xorg configuration file setup for your graphics card? Or are you just using defaults?

---

### Post by LifeEnemy on 2009-09-20
I have no idea what that even is, so I'm guessing default.

---

### Post by LifeEnemy on 2009-09-22
bump

---

### Post by LifeEnemy on 2009-09-28
I've tried putting the animation settings low (fire particle size, life, number, etc.), but the problem remains. It works fine after the first run for a few minutes, though. And what was that about the Xorg file??? I have no idea what that is or what I would do to it to fix this.

---

### Post by Giblet5 on 2009-09-28
I can confirm this.

I have observed the same behavior with 180.44 on an nvidia gtx 280 w/ 1G. Quad core i7 w/ 8GB DDR3 RAM.

Good example: cube rotate - the first rotate is jerky with visible tearing. Subsequent rotates are smooth as glass (better than 60 FPS).

I had assumed it was a mipmap delay or something and haven't bothered investigating, but yeah, it's slow the first time, or if you haven't done that in awhile.

Compiz display settings:
Texture filter: Good
Sync to vtrace (no triple buffer option)

It behaves like compiz.real got paged out.

---

### Post by LifeEnemy on 2009-09-28
I've noticed that, too. I don't have much tearing, but using the cube is a little jerky for the first few seconds, but then it works fine.

---

### Post by LifeEnemy on 2009-10-05
Bump

---

### Post by radu.c on 2009-11-01
If it helps anyone (to laugh, anyway), here's my experience:

I setup so that when a window opens, it uses the "Beam Up" effect, and when it closes it uses the "Burn" effect. For minimisation I just set it to "Magic Lamp", and that one works just fine.

The "Burn" and "Beam Up" plugins are as fast (or should I say "as slow") on both my laptops.

Here's my big laptop:

[INDENT]CPU: Intel Core 2 Duo T5800
RAM: 3GB
Video: nVidia 8200M w/ dedicated 256MB (nVidia 185.18.36)
Resolution: 1280x800
[/INDENT]
Here's my little laptop:

[INDENT]CPU: Intel Pentium M @ 1.1 GHz :KS
RAM: 1.25GB (256MB soldered to the board, in case you're wondering)
Video: Intel 915GM :KS
Resolution: 1280x768
[/INDENT]
Distro on both: Ubuntu "Karmic Koala" 9.10

:popcorn:

Did you laugh yet? Yes, there is THAT much of a difference between my two laptops. My little laptop was a bit slow even without the burn and beam up effects in 9.04, but it's much faster in 9.10 (eat your heart out Windows Vista/7 users!)

Small windows seem fine on both laptops (my little laptop is only a bit slower than my big laptop), but maximised windows... same speed.

I checked that the settings are identical, because, at first, my big laptop was SLOWER than my little laptop. It had some extra fade effects for opening and closing windows, and I got rid of those TO MATCH SPEED.

If you ask me, the answer is "speed-up loops": **[http://thedailywtf.com/Articles/The-Speedup-Loop.aspx](http://thedailywtf.com/Articles/The-Speedup-Loop.aspx)**

---

### Post by mbuller10 on 2009-12-06
I opened up the Compiz Settings Manager, went to general options, clicked on the display setting tab, then checked the Sync to Vblank option, I'm using the 185 drivers as well and that seems to have worked for me so far

---

### Post by LifeEnemy on 2009-12-07
Thanks for the suggestion. There is still some lag on the burn animation at times, but there is a noticeable increase now!

---

### Post by aviedw on 2009-12-07
this is my setup

windows 7/ Ubuntu 9.10 dual boot
2 hard drives 
2 gigs of memory
amd athlon xp 3000+ 
Nvidia 8400

I had a similar issue with graphics feeling like its effects was lagging, so i decided to not use the 185 that is automatically offered and went to the Nvidia website and got the 190.42 drivers and my computer has been so much better.

---

### Post by andydread on 2010-12-13
I did not have this problem with a 8800GT but when i swapped the card to a much newer 470GTX this problem showed up.  Expecially with the burn animation.   It turns out to be a problem with the power saving settings on newer nVidia cards.   Set the Powermizer settings to full performance in nvidia-settings makes this problem completely disappear for me.

---

