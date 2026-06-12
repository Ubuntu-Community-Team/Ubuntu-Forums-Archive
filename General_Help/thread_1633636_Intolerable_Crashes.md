---
title: "Intolerable Crashes"
date: 2010-11-29
forum: General Help
---

### Post by smilingfrog on 2010-11-29
I need some advise.
I want to know what other people have done to stop their computers from crashing. My main computer has now crashed 5 times in the last hour and a half.

I am not using Compiz, and to the best of my knowledge it is uninstalled.
I try not to use flash with the internet.
I am using the 64 bit version of 10.04, because I want to make use of my 8GB of RAM.

The computer crashes constantly. Constantly. Usually when I am using it. I can leave it on for days without a problem; but as soon as I need to get work done, it starts crashing.

Some specs:
ASUS P7P55D Pro motherboard
Intel i5-750 processor.
evga GTS 250 video card with NVIDIA drivers (uptodate)
8GB RAM
Ubuntu 10.04 64 bit

I need a gameplan to make this computer stop crashing. It is driving me crazy. Any suggestions on how to start diagnosing the causes of these crashes is appreciated.

---

### Post by smilingfrog on 2010-11-29
With a little research I cam across this not so reassuring post:

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

I have started by purging ubuntuone from my system, since I don't use it. 

[http://www.howtogeek.com/howto/22881/remove-ubuntu-one-from-ubuntu-10.04/](http://www.howtogeek.com/howto/22881/remove-ubuntu-one-from-ubuntu-10.04/)

See if that helps.

---

### Post by bodhi.zazen on 2010-11-29
This kind of a problem can be due to almost anything, including overheating.

You will need to check your logs or try to determine your box is crashing.

If all else fails, unplug the box and clean it.

---

### Post by Slim Odds on 2010-11-29
I find that these kinds of problems are often caused by a flaky power supply.

---

### Post by akand074 on 2010-11-29
Judging by your specs, it looks very possible that you built your computer. If that's the case, are you using the default BIOS settings? When I built one of my computers, it was crashing over and over again. I later found out that my RAM voltage written in the package said they ran at 1.6V. When I went to the website it showed 1.9V. When I brought the RAM voltage up it ran fine ever since. If you did build your computer, it is possible that its just a misconfiguration somewhere. Either over heating or not enough power, or like mentioned above, faulty power supply.

---

### Post by smilingfrog on 2010-11-30
@akand074: Thank you for your suggestion. I did build the computer. My RAM voltage was set to spec, but I reviewed the RAM online and found that many other people had similar problems. I have turned the voltage up to 1.7 V and so far the computer appears more stable. For instance, it doesn't crash with youtube-- this is new.

I don't believe it is the power supply, but I will put it through some other tests to see. Thanks for the help.

I am concerned at the number of posts from people who are complaining of similar problems to what I have complained about. Could it be massive hardware misconfiguration? Or does Linux inherently put more load on a machine?

---

### Post by bodhi.zazen on 2010-11-30
> **smilingfrog said:**
> I am concerned at the number of posts from people who are complaining of similar problems to what I have complained about. Could it be massive hardware misconfiguration? Or does Linux inherently put more load on a machine?

This is a hardware (configuration) problem and not a linux problem.

---

### Post by Slim Odds on 2010-11-30
> **smilingfrog said:**
> ...
I am concerned at the number of posts from people who are complaining of similar problems to what I have complained about. Could it be massive hardware misconfiguration? Or does Linux inherently put more load on a machine?

I hear too many people saying things like this and I must respond as I often do that Linux is NOT magic. It uses the CPU, memory, etc just like any other OS, only more efficiently.

---

### Post by smilingfrog on 2010-12-01
> **Slim Odds said:**
> I hear too many people saying things like this and I must respond as I often do that Linux is NOT magic. It uses the CPU, memory, etc just like any other OS, only more efficiently.

My query re: crashing is not a slag on Linux. I built my computer, and as has been pointed out to me, my computer crashes were a result of misconfiguration. My concern is more to do with the sheer volume of threads relating to other peoples machines crashing. I was not alone in this complaint (search it). I wonder all the other people complaining are having problems because of system misconfiguration, and are blaming the OS instead of the build.

Problem solved, by the way, 2 full days of work doing all the stuff that used to crash the machine! Thanks tons for the help.

---

### Post by bodhi.zazen on 2010-12-01
> **smilingfrog said:**
> My query re: crashing is not a slag on Linux. I built my computer, and as has been pointed out to me, my computer crashes were a result of misconfiguration. My concern is more to do with the sheer volume of threads relating to other peoples machines crashing. I was not alone in this complaint (search it). I wonder all the other people complaining are having problems because of system misconfiguration, and are blaming the OS instead of the build.

Problem solved, by the way, 2 full days of work doing all the stuff that used to crash the machine! Thanks tons for the help.

"crashing" is a very broad term and is due to a multitude of potential problems.

I know on no OS that is free of crashes, but, IMO Linux is more reliable and has less crashes then Windows.

If you want a stable system, free of crashes, use Centos, Debian stable, or Slackware (these three OS are more stable, IMO).

---

