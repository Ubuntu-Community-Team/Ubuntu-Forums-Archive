---
title: "Persistent flash (?) related system freezes"
date: 2011-11-12
forum: General Help
---

### Post by anlag on 2011-11-12
I've had this problem for several months. It happens occasionally, and lately nearly on a daily basis, that my system hangs and freezes, especially when I'm using flash and/or java applications. A java download manager, and Youtube, feature heavily. Sometimes flash ads will cause it too, or graphics heavy work applications. What happens is that especially when I have a lot of things running, and I go to watch a flash video (Youtube), it will start up and then the screen blinks once after which the system becomes nonresponsive. I can move the mouse pointer, and sound may continue for a time, but I can't touch, move or do anything. In the past I was sometimes able to access a non-X terminal with Ctrl-Alt-F6 for example, and use that to kill the browser and possibly other things, which would sometimes be enough to save the session. Failing that, and nowadays nearly always, I am simply forced to a hard reboot via power button.

Since it seems to occur mostly related to flash, I've tried different flash plugin versions. Using the Firefox extension Flash-Aid I tried all its three options: Adobe Flash stable, Adobe Flash beta, and the Google Chrome bundled flash. The freezes happened with all. 

I thought it might be related to my desktop environment. Typically I used the full hardware accelerated Unity environment in 11.04, but for the past week or so have gone through Unity 2D, Ubuntu Classic (Gnome 2) and Ubuntu Classic without effects. In all cases it continues to happen, although it took longer than usual before it did with Gnome 2 with no effects (Compiz, I guess). 

Since graphics may be a factor, I've also made sure I have the latest NVIDIA drivers (version 285.05.09) including uninstalling and reinstalling. 

Anyway, I'm quite out of ideas for what else to look at. I'm not even sure how to analyze the problem, to see what it is that's crashing. As far as I know, the flash plugin itself (or java for that matter) should not be able to hang the entire X server, so perhaps it's something deeper down?

Very grateful for any suggestions. My system is still Ubuntu 11.04 32 bit version, and the hardware is a Lenovo ThinkPad T61, which has an NVIDIA Quadro NVS 140M graphics card.

---

### Post by ballantony on 2011-11-14
I didn't have this problem until the last week or so. Increasingly I am getting flash related freeze on Chrome and an application not responding on Firefox.  No idea where it came from...

---

### Post by ballantony on 2011-11-14
Just deleted ~/.mozilla (something I seem to be doing on a more and more frequent basis) and that seems to have sorted out the Firefox problem.  For the moment at least

---

### Post by anlag on 2011-11-26
It doesn't sound like we have the same problem. When the problem occurs for me, it doesn't freeze a browser and doesn't give a message, it freezes the entire X server. On occasion, especially if I act quickly after it gives the first ominous blink, I am able to shift to a "dumb" terminal and kill processes. Tonight I found also that holding down Ctrl-Alt-Backspace to kill the X server sometimes after a few seconds, shortly before it does kill the server, kills something else that makes the Youtube video or whatever start working again. 

Might add also that I upgraded to 11.10 about a week ago to see if that would help. I had no freezes for several days; it happened sometimes that I would get a similar blink across the screen as if it were about to hang, but after a second or so, it continued as before. Alas, now the problem is back like it was before. For the record, I have shifted from using Chrome to Chromium which as far as I know has separate configuration folders, so I don't believe the problem lies there either.

Can noone offer any clue as to what might be the problem? Or at least give some suggestion as to how I can track down where the actual error lies? For all I know it could be the graphics cards, it could be drivers, it could be the flash plugin, or a number of other things. I'm bloody tired of it, and don't really have time to deal with it properly, but it's an extremely frustrating error. Especially when considering the old adage that misbehaving applications in Linux should not hang the system, which certainly is what happens here, whatever is misbehaving.

---

### Post by oldtimer7777 on 2011-11-26
Occasionally it is a good idea to clear all your caches..

in terminal:

sudo apt-get install bleachbit
sudo bleachbit

and do a complete cleaning of your entire system.. and see if the problem remains..  Usually this will clear up issues like this when they happen on my own system and don't forget to do a power cycle of your system when you are done cleaning everything out with bleachbit.

> **anlag said:**
> It doesn't sound like we have the same problem. When the problem occurs for me, it doesn't freeze a browser and doesn't give a message, it freezes the entire X server. On occasion, especially if I act quickly after it gives the first ominous blink, I am able to shift to a "dumb" terminal and kill processes. Tonight I found also that holding down Ctrl-Alt-Backspace to kill the X server sometimes after a few seconds, shortly before it does kill the server, kills something else that makes the Youtube video or whatever start working again. 

Might add also that I upgraded to 11.10 about a week ago to see if that would help. I had no freezes for several days; it happened sometimes that I would get a similar blink across the screen as if it were about to hang, but after a second or so, it continued as before. Alas, now the problem is back like it was before. For the record, I have shifted from using Chrome to Chromium which as far as I know has separate configuration folders, so I don't believe the problem lies there either.

Can noone offer any clue as to what might be the problem? Or at least give some suggestion as to how I can track down where the actual error lies? For all I know it could be the graphics cards, it could be drivers, it could be the flash plugin, or a number of other things. I'm bloody tired of it, and don't really have time to deal with it properly, but it's an extremely frustrating error. Especially when considering the old adage that misbehaving applications in Linux should not hang the system, which certainly is what happens here, whatever is misbehaving.

---

### Post by pretty_whistle on 2011-11-26
What is a power cycle?

---

### Post by pretty_whistle on 2011-11-26
Never mind.  I googled power cycle.
:)

---

### Post by anlag on 2011-11-27
> **oldtimer7777 said:**
> Occasionally it is a good idea to clear all your caches..

in terminal:

sudo apt-get install bleachbit
sudo bleachbit

and do a complete cleaning of your entire system.. and see if the problem remains..  Usually this will clear up issues like this when they happen on my own system and don't forget to do a power cycle of your system when you are done cleaning everything out with bleachbit.

Thanks for the suggestion! I've installed it and done a cleaning of flash cache+cookies, browser cache and the vacuuming, system cache and various other options. I'll see how it goes from here. I appreciate it, seems a generally handy program as well.

---

### Post by oldtimer7777 on 2011-11-27
> **anlag said:**
> Thanks for the suggestion! I've installed it and done a cleaning of flash cache+cookies, browser cache and the vacuuming, system cache and various other options. I'll see how it goes from here. I appreciate it, seems a generally handy program as well.

I've seen bleachbit remove Gb's of data in one cleaning sometimes..  Very handy to use from time to time, and highly recommended too. You can even schedule it to run from time to time, which is probably a good idea.

---

### Post by anlag on 2011-11-27
Indeed. I didn't think I picked all that many options, and it still cleaned out in the region of 1.3 Gb. It's worthwhile for that reason alone, and if it solves persistent and annoying issues, all the more so.

---

### Post by oldtimer7777 on 2011-11-27
> **anlag said:**
> Indeed. I didn't think I picked all that many options, and it still cleaned out in the region of 1.3 Gb. It's worthwhile for that reason alone, and if it solves persistent and annoying issues, all the more so.

If it fixed it, make sure to mark this thread as solved too btw.. You are very welcome. :)

---

### Post by anlag on 2011-11-27
I definitely will, but since the problems have been a bit irregular I'll give it a few days to see if it resurfaces. Might try and provoke it a bit too... guess I'll have to find time to do a bit of youtubing one of these nights. ;)

---

### Post by anlag on 2011-12-01
Sad to say that after a couple of days without problems, I've again experienced freezes yesterday and today. So while bleachbit is undoubtedly a useful program and I will be using it, it did not - at least with what I purged - solve the problem. 

A thought - isn't there some kind of log I could check to find what the last thing that happened before a freeze was? Internally that is. It might offer some clue as to where the problem lies. I tried having a look around the system logs GUI the other week but couldn't really find where to look. Any ideas, anyone?

---

### Post by Miljet on 2011-12-01
This is just a thought, but are you monitoring your system temps?  I know that streaming video drives my cpu temps up dramatically. Since your problem seems to get progressively worse over time, I'm thinking that it's possible that your fans are getting clogged with dust.

I use sensors-applet to monitor temperatures.

---

### Post by anlag on 2011-12-01
Thanks. I did have heating issues a few months ago, when heavy use would push the CPU temperature up to nearly 100 &#8451;. I was able to fix that with a bit of high pressure air cleaning of the fans. I created at the time also a simple script to write the CPU temperature to a log file every 5 minutes, and can see that it has been ranging between 50 and 62 &#8451; during the last hour, during which I had one such freeze. I don't believe it could have risen quickly enough to cause a problem inside of any 5 minute interval. Additionally the problems nearly always happen when I start a youtube video for example; if it starts fine then it usually stays that way. If it were a heating issue I would expect it to be more likely (or at least as likely) for the problems to occur at a later point while watching.

Nevertheless I will add monitoring of my GPU temperature to the log file as well, just in case...

---

### Post by Miljet on 2011-12-01
Sounds like you have already covered that possibility pretty well then. I can't think of anything else right now. I'll keep monitoring this thread and if I come up with any other possibilities, I'll let you know. In the meantime, maybe someone more knowledgeable than I am will show up.

---

### Post by cajunlibra on 2011-12-29
I've been having this issue ever since upgrading to Ubuntu 11.04.
I can't play facebook games or watch videos online without Ubuntu crashing after a few minutes. It is happening with both Chrome and FF. I have the newest versions of everything and even a fresh install didn't fix it.  In XP, the flash plugin might crash but not the whole system.

---

### Post by DanR01 on 2011-12-29
I had a similar problem where flash would cause the system to hang and crash to the login screen.

The problem seemed to be with the NVIDIA drivers. I uninstalled them and installed the nouveau package which has solved the problem.

If you choose to try this you may need to use the --purge flag when removing the proprietary drivers.

---

### Post by cajunlibra on 2011-12-29
I have ATI.  Any other ideas?

---

### Post by cajunlibra on 2012-02-03
Anyone?  The persistent crashing is really grating on me. It has interrupted my Ubuntu experience and I'm about ready to give up.

---

