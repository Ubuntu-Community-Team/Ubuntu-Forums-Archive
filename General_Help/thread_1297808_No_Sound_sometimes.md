---
title: "No Sound sometimes"
date: 2009-10-22
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-10-22
I have a dell inspiron laptop and seem to be having a problem with my sound. Sometimes it works and sometimes it dont. Not sure what info is needed, but here is a screenshot of available mixers.

---

### Post by wojox on 2009-10-22
I use alsa. Try opening a terminal and 

```
alsamixer
```

Then set your sound up. Make sure nothing is muted. Then exit and type:

```
sudo alsactl store
```

---

### Post by Feelin_froggy8877 on 2009-10-25
Well there is nothing muted in alsamixer, also when I (do) have sound, the volume control in the panel does not seem to control the volume, only volume keys on keyboard control it. I have gone over the settings when I have sound and don't have sound (all are the same) Volume devices tend to confuse me when choosing between "pulse audio, hda intel alsa mixer, idt oss mixer" Witch normally don't have to, all just set to autodetect w/ no problems (normally). Is there possibly a sound property in bios I might want to disable? I did have to do that with my desktop, only because it has onboard and a pci card. Would'nt think that would be the case here though.

---

### Post by Feelin_froggy8877 on 2009-10-25
Bump?

---

### Post by Feelin_froggy8877 on 2009-10-26
one more bump attempt.

---

### Post by Living2007 on 2009-10-27
IF you have two apps using sound, they won't work together, only the first sound app will work. This is if you are using Open Sound System. To get the other app to work., close both apps, and restart the other.

Or use a different sound type. I don't know of any other method.

---

### Post by smcleish on 2009-10-27
> **Living2007 said:**
> IF you have two apps using sound, they won't work together, only the first sound app will work. This is if you are using Open Sound System. To get the other app to work., close both apps, and restart the other.

Or use a different sound type. I don't know of any other method.

I find, on my Dell desktop PC, that this sometimes happens with other sound systems than OSS. I have sound except when I have visited a web site with a flash plugin which has sound. Then nothing else can talk to the sound card until the browser is closed.

I'd suspect that something like this is happening in this case, because the sound is intermittent. If something is blocking access to the soundcard for other processes, the easiest way to find it is to use lsof and grep the output to pick up the sound device you're using. Something like lsof | grep "/dev/dsp".

---

### Post by Feelin_froggy8877 on 2009-10-27
Well I really am at a loss. Been a few reboots now and no sound at all. Running tests from sound properties seems ok "testing" but no sound. I've checked everywhere I know to make sure nothing is muted.

---

### Post by GiveLove on 2009-10-27
Hello Feelin_froggy8877, :)

I'm no expert by any means, so I'm not sure if this will apply to you. I've noticed over the years of using Linux, that with my Creative Labs Audigy 2 ZX sound card, occasionally I'll boot up and have no sound. And the solution is to go into the "Volume Control", click on the "Switches" tab, and either check mark or un-check mark the "Audigy Analog/Digital Output Jack". And that fixes the problem. Give it a try.

GiveLove

---

### Post by Feelin_froggy8877 on 2009-10-27
I do appreciate the reply, But I to have had to do that with my desktop w/ a SB card, But w/ this lappy I have no such tab for switches for my intel sound. That was one of the first things I looked for.

---

### Post by Feelin_froggy8877 on 2009-10-27
After looking through some other sound problem posts, I noticed that people were having troubles after certain updates. I attempted to boot into previous  kernals w/ a lil hope, but no luck. On the verge of just doing a reinstall and start from scratch.

---

### Post by Feelin_froggy8877 on 2009-10-27
ok,went ahead and did a complete reinstall w/ a fresh Ubuntu iso and new disk. I was actually having trouble with booting the iso, (nautilus would always crash on me) using the live cd. Never really had a problem w/ the install though. Either way, no luck, didnt get sound on first boot up or after updates.

---

### Post by smcleish on 2009-10-28
> **Feelin_froggy8877 said:**
> I do appreciate the reply, But I to have had to do that with my desktop w/ a SB card, But w/ this lappy I have no such tab for switches for my intel sound. That was one of the first things I looked for.

Don't know if this will help, but I've thought this too when following similar suggestioins - and then discovered that I needed to click on "Preferences" in the volume control to ensure that this tab is visible.

---

### Post by Feelin_froggy8877 on 2009-10-28
looked through a bit more, nothing. btw, this bites.

---

### Post by Feelin_froggy8877 on 2009-10-28
Downloaded the 1.08.19 alsa version and configured from source and no help. I been through setting so much I'm going cross eyed. I'll keep searching for solutions and report any if any fixes, please, If any1 has any suggestions let me know. Thanx

---

### Post by GiveLove on 2009-10-28
Hello Feelin_froggy8877, :)

I don't have any concrete answers for you. But here is some ideas...

Well Ubuntu 9.10 comes out in one day. You could always try installing that new version and see if it makes a difference. You never know. Particularly if it is newer hardware, you might have a better chance of it working correctly. 

By the way, is your sound card listed as supported in Alsa?
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Another idea is to ditch Ubuntu and try another distribution. How about Debian, or CentOS for stable distro's? Or Fedora, or Linux Mint that fall into the testing branches of code much like Ubuntu.

---

### Post by Feelin_froggy8877 on 2009-10-29
It is newer hardware. For a change,never had any problems w/ sound till now.  Benn using Ubuntu for a while now, and have grown quite used  to it. But thanx for the ideas, willing to try anything, cant have a comp w/ no sound.

---

### Post by Feelin_froggy8877 on 2009-10-30
Upgraded to 9.10. And (so far so good, so what) ha "Iron Maiden" Anyway, Must've been an issue w/ the newer intel sound. I'm pretty much stuck on Ubuntu. Especially for the new lappy (wubi install) Not quite ready to go partitioning the hhd yet.

---

