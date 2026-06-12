---
title: "strange noise at login screen"
date: 2009-06-29
forum: General Help
---

### Post by the_prototype on 2009-06-29
If there is anyone out there who might be able to assist me with my dilemma I would greatly appreciate it. Whenever I boot Ubuntu on my laptop and arrive at the login screen where the user must type in his or her username and password, a strange noise begins to emit from the laptops' speakers. It sounds quite similar to someone constantly beating on some type of drum. The noise is incessant and will not cease so long as I am using Ubuntu. I just installed Ubuntu 9.04 on my laptop alongside Windows Vista (partitioned the drive). When I boot Windows Vista, I do not get any strange noise whatsoever. What is going on? :-(

---

### Post by itsjareds on 2009-06-29
That's strange. It's just the beating drums noise that plays when your login screen first shows up -- but it should only run once. Not sure why it is looping like that.

---

### Post by lisati on 2009-06-29
I've had similar on my old laptop (which I recently gave away to a nephew). I'm not sure why it happens - my old laptop had a "small" amount of RAM - but the workaround I used was to restart the machine a few times until the normal login sounds were played.

---

### Post by jocko on 2009-06-29
One solution is to disable the sound at the login screen. Open gdmsetup (System-->Administration-->Login Screen, or type "gksudo gdmsetup" in a terminal).
Under the "Accessibility" tab, uncheck all sounds.

---

### Post by the_prototype on 2009-06-29
So the drum noise is a normal startup sound? I'll try restarting it a few times and see if it does any good. If not then I will try disabling the startup sound. I would hope that it has nothing to do with the installation or sound drivers for the OS. I downloaded the OS right from the ubuntu website and verified the hash with winMD5SUM. It should work properly if I'm not mistaken, which, it does only it keeps looping the same sound over and over.

---

### Post by credobyte on 2009-06-29
> **the_prototype said:**
> So the drum noise is a normal startup sound? I'll try restarting it a few times and see if it does any good. If not then I will try disabling the startup sound. I would hope that it has nothing to do with the installation or sound drivers for the OS. I downloaded the OS right from the ubuntu website and verified the hash with winMD5SUM. It should work properly if I'm not mistaken, which, it does only it keeps looping the same sound over and over.

Yes, startup sounds are always enabled ( for sure, you can disable them ).

---

### Post by Whisp3r on 2010-07-06
> **jocko said:**
> One solution is to disable the sound at the login screen. Open gdmsetup (System-->Administration-->Login Screen, or type "gksudo gdmsetup" in a terminal).
Under the "Accessibility" tab, uncheck all sounds.

I'm running Lucid and that isn't an option under the Login screen menu. All the login screen menu offers me is to "Show the Screen for choosing who will log in" and log in automatically. There are no tabs for sound or any other options.

---

