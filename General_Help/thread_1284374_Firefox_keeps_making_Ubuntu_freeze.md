---
title: "Firefox keeps making Ubuntu freeze"
date: 2009-10-06
forum: General Help
---

### Post by snakeman21 on 2009-10-06
Hi all!  I've been using ubuntu for about 3 years, and until now I haven't had any serious issues with Firefox.  But I recently bought a new laptop, and I think this must be a hardware issue.  Firefox keeps making Ubuntu freeze to the point where NOTHING is responsive.  I can't even get to a shell, and I have to reboot the computer.

Perhaps the stranges thing about this is that it's random...

Sometimes, I can download stuff and watch streaming video for hours before it acts up, and other times it will freeze up as soon as I start Firefox.  I got Epiphany from the repos, and so far I haven't had any freezing.  But I really miss Firefox.  Any ideas?

I'm running Ubuntu 9.04 on an HP dv6000 with an Nvidia graphics card, a Broadcom wireless card, and an AMD Turion 64 processor.  (Could it be because I'm running 32-bit Ubuntu with a 64-bit processor?)

---

### Post by lovinglinux on 2009-10-06
See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Most of the optimization tips available there should help improve Firefox performance. Nevertheless, I recommend trying Firefox 3.5, which is much better than 3.0. Installation instructions also available on that tutorial.

Another thing that might help is described in **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section.

---

### Post by jpaugh64 on 2009-10-06
> **snakeman21 said:**
> Could it be because I'm running 32-bit Ubuntu with a 64-bit processor?
I seriously doubt that this could be an issue. x86 chips are backwards compatible back to the very beginning of the line. A 64 CPU running in 32bit mode should behave exactly as a 32bit processor, except for the inclusion of an instruction to switch to 64bit mode, of course.

---

### Post by snakeman21 on 2009-10-07
> **lovinglinux said:**
> See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Most of the optimization tips available there should help improve Firefox performance. Nevertheless, I recommend trying Firefox 3.5, which is much better than 3.0. Installation instructions also available on that tutorial.

Another thing that might help is described in **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section.

I thought about that, but I read somewhere that Firefox 3.5 is not compatible with a lot of addons.  I use Video DownloadHelper, Smart Stop/Reload, Speed Dial, and the Aero Fox theme.  Do you know offhand if these will be compatible?

Also I read something about Firefox 3.5 being called something like "shiretoko", what's the story on that?

EDIT:  I formatted my drive last night and installed Ubuntu 64-bit.  So far, Firefox has forced me to do a hard restart once.

---

### Post by lovinglinux on 2009-10-08
> **snakeman21 said:**
> I thought about that, but I read somewhere that Firefox 3.5 is not compatible with a lot of addons.  I use Video DownloadHelper, Smart Stop/Reload, Speed Dial, and the Aero Fox theme.  Do you know offhand if these will be compatible?

It is compatible with most add-ons I use (41). Nevertheless, my tutorial also explains how to override the extension compatibility check, to install "incompatible extensions". I'm forcing for example TagSifter, which a relatively complex extension, without issues.

I know DownloadHelper and Speed Dial are compatible, because I use them. Smart Stop/Reload is also compatible, according to Mozilla Add-ons site. Unfortunately, it seems Aero is not compatible, but you could try to force it. I did that with Chromifox before the author released a compatible version.

> **snakeman21 said:**
> Also I read something about Firefox 3.5 being called something like "shiretoko", what's the story on that?

It's just the development codename. They didn't change it to Firefox in Jaunty to avoid confusion. But there are other methods of installation that install Firefox 3.5 with logo and name. Check the tutorial for further instructions.

---

### Post by snakeman21 on 2009-10-08
Well, I installed Firefox 3.5... It made no difference.  I still have to use Epiphany.  I didn't even have a chance to try to get my addons working, because it kept freezing up my computer.  I don't understand why this is happening.  I know of three people with the same OS, updates, and browser as I do, and this doesn't happen to them.  My wife's computer is set up the same way mine is, and Firefox works like a dream.

---

### Post by ubun_two on 2009-10-08
Maybe try using epiphany?  I tried it recently, and it's a lot snappier.  It uses Gecko rendering engine.  One that uses Webkit is being worked on (NOT in standard repo).

On the downside, it is missing a lot features compared to Firefox.

You can find it in Synaptic.  Search for epiphany-browser.

---

### Post by snakeman21 on 2009-10-08
> **ubun_two said:**
> Maybe try using epiphany?  I tried it recently, and it's a lot snappier.  It uses Gecko rendering engine.  One that uses Webkit is being worked on (NOT in standard repo).

On the downside, it is missing a lot features compared to Firefox.

You can find it in Synaptic.  Search for epiphany-browser.

Read my first post in this thread.  I have been using Epiphany because Firefox is freezing my computer.  I don't like it, so I want to solve the Firefox problem

---

### Post by lovinglinux on 2009-10-09
> **snakeman21 said:**
> Well, I installed Firefox 3.5... It made no difference.  I still have to use Epiphany.  I didn't even have a chance to try to get my addons working, because it kept freezing up my computer.  I don't understand why this is happening.  I know of three people with the same OS, updates, and browser as I do, and this doesn't happen to them.  My wife's computer is set up the same way mine is, and Firefox works like a dream.

Are you sure you have launched Firefox 3.5 and not 3.0? After launching firefox, go to "Help >> About Mozilla Firefox" and verify the version described there.

If you installed FF 3.5 from the repositories, then you need to launch it through "Applications >> Internet >> Shiretoko Web Browser"

Have you tried to optimize Firefox with the tips from my tutorial? Have you tried the solution [**[COLOR="Red"]FOT010[/COLOR]**]?

If yes, then try to launch Firefox in safe mode:

```
firefox -safe-mode
```

If that helps, then is probably an extension causing the crashes. If not, then try to create a new profile and check if solves the problem:

```
firefox -P
```

---

### Post by snakeman21 on 2009-10-09
Yes, I made sure it was FF 3.5 I was using... and I did follow your tutorial.  I will try launching it in safe mode later, I have some stuff I have to do now.  If my wife comes home and finds out I've been on the computer all day, she'll shoot me.  I'll report back once I give it a shot.

---

### Post by lovinglinux on 2009-10-09
> **snakeman21 said:**
> Yes, I made sure it was FF 3.5 I was using... and I did follow your tutorial.  I will try launching it in safe mode later, I have some stuff I have to do now.  If my wife comes home and finds out I've been on the computer all day, she'll shoot me.  I'll report back once I give it a shot.

Good luck.

---

### Post by snakeman21 on 2009-10-09
Well, I tried it in safe mode, and it ran normally.  So I disabled all of my extensions, and, lo and behold, it's working the way it should.  I'm going to re-enable them one at a time throughout the rest of the day to find out which one is causing the problem.  Thanks for your help!

UPDATE:  Enabled Video DownloadHelper at 2:10 pm

---

### Post by lovinglinux on 2009-10-09
> **snakeman21 said:**
> Well, I tried it in safe mode, and it ran normally.  So I disabled all of my extensions, and, lo and behold, it's working the way it should.  I'm going to re-enable them one at a time throughout the rest of the day to find out which one is causing the problem.  Thanks for your help!

UPDATE:  Enabled Video DownloadHelper at 2:10 pm

You are welcome. I hope is not an extension that you need really bad. If it is a common extension this will probably help several users.

---

