---
title: "Kubuntu logs out spontaneously"
date: 2009-11-22
forum: General Help
---

### Post by nezurian on 2009-11-22
Hi!

I am using Kubuntu Karmic Koala. I am using my computer for sorfing and chatting. I use Firefox and emesene. Sometimes Kubuntu spontaneously logs out. Then I log in again, and sometimes it happens again. It happens almost everyday at least one time. Why could it be? Is it a bug? 

My all upgrades are done.

---

### Post by Zorael on 2009-11-22
That sounds like X is crashing. KDM will automatically restart it, which makes you end up at the login screen. (Unless you have automatic login enabled, in which case you will end up at the ksplash screen.)

The log file for X is at **/var/log/Xorg.0.log**, but it pertains to the currently running session. Ergo, the log with the crash details will be instantly renamed as a new X session starts. So for the log for the *previous* session, you'll want **Xorg.0.log.old** in the same directory.

Another file of interest is KDM's log, which sometimes logs errors that Xorg.0.log doesn't. It's at **/var/log/kdm.log**, and it'll be pretty long as it doesn't use the same renaming scheme, instead just appending new log entries to the end.

Lastly, your user may or may not have a file called **.xsession-errors** in your home directory. Check it too, to see if anything interesting is written there.

I just bet it's a (video) driver crashing. You're not using an Nvidia graphics card with the proprietary driver, by any chance?

---

### Post by nezurian on 2009-11-22
Hmmmh....

I am also having a similiar problem - the programs I use shuts itself down spontaneously. realplayer, emesene, Kontact, firefox, chromium, almost every program I use shuts itself time to time.

Could it be also related with the driver? 

BTW , I am using Geforce mx440. and I didn't install any driver. Do you suggest me to use EnvyNG ?

---

### Post by Zorael on 2009-11-22
In the case of applications shutting down, that's usually accompanied by a window (Apport) telling you it crashed, and offering you some options about what to do about it. Like, "report a bug", "restart application", something along those lines. In most cases you'll only really know what happened if you start the program from a terminal. That way it can output error messages to that terminal when it crashes.

I wouldn't call it impossible, but I'm not sure video drivers generally cause applications to crash, without causing the entire X session to crash. If you're getting crashes everywhere in this sense, perhaps you have a bad RAM stick, or some other piece of hardware is about to give up on you.

---

### Post by byline on 2009-11-22
[COLOR=Black]I've been having a similar problem. I upgraded to Ubuntu 9.10 last month, and just this week, while surfing Facebook apps with Firefox, I was unexpectedly logged out. The last two times, I opened my Terminal window and typed: tail /var/log/messages

The second time, I got this message which coincided with the time of the logout:

[/COLOR]   [COLOR=Black]Nov 17 09:59:55 desktop pulseaudio[2937]: pid.c: Stale PID file, overwriting.
Nov 17 10:00:03 desktop pulseaudio[2937]: ratelimit.c: 1 events suppressed 

This last time, I got a similar message also coinciding with the time of the logout:

[/COLOR]   [COLOR=#ff0000][COLOR=Black]Nov 21 16:07:16 desktop pulseaudio[3648]: pid.c: Stale PID file, overwriting.
Nov 21 16:07:22 desktop pulseaudio[3648]: ratelimit.c: 18 events suppressed

Per an earlier poster's suggestion, I also checked my .xsession-errors file. Unfortunately, it just seems to be a running list of errors and not something I can pin down to a specific date and time. I do see this line repeatedly:

(firefox:7121): Gdk-WARNING **: XID collision, trouble ahead

Would that have anything to do with the unexpected logouts? (Possibly related: I've also been having trouble with Firefox freezing up, then crashing, on a particular site. However, I started viewing that site using Konquerer and have had no problems.)

Thanks for any advice you can offer!

P.S. I'm the computer user, my husband the actual Linux guy and installer. However, because he suffers with chronic back pain, long periods of sitting to work on this are not an option for him. So, big pictures, little words, OK? :)
[/COLOR][/COLOR]

---

### Post by Zorael on 2009-11-22
@byline;
I imagine the tail of **/var/log/Xorg.0.log.old** would be of more interest. I get a lot of the "XID collision" messages too, and they don't seem to be malign.

As for GDM I'm not sure, but I think it creates a **/var/log/gdm/** directory in which it places its logs. Refer to them to see if there's anything of interest.

As for Firefox crashing on a particular page, that could for instance be caused by the browser itself not handling some element of it properly (legitimate browser rendering bug), bad cache of the page, an extension crashing the browser, or a plugin (Flash) crashing the browser, etc. I'd try clearing out the cache and disabling extensions, then trying again. If it still doesn't work, you can try starting Firefox from a terminal, as that would (as mentioned in previous posts) allow the program to output errors to there when it crashes. Unless, of course, Ubuntu's packaged Firefox has been set up to quelch those messages. (In which case I don't know where they end up, perhaps .xsession-errors.)

---

### Post by byline on 2009-11-24
Thank you for this reply, Zorael. Now I'm going to ask a stupid question (because I'm not the one who knows the nuts and bolts of my Linux setup): Where do I find the GDM logs, by typing that code in the Terminal window, or by searching through my Home directory? Thanks for bearing with me! :)

---

### Post by Zorael on 2009-11-24
(Just googling for suggestions right now, as I'm using KDM.)

There should be a directory: **/var/log/gdm**. Are there any .log files in it? Perhaps "**:0.log**"? Are there several files, or is it just one huge one?

A complicating factor is that as a rule, such log files pertain to the currently running session. So if you're looking for the error messages at a crash, you actually have to find the *previous* log and not the current one, as the currently running session hasn't crashed yet. If it is a huge file with new entries just added to the bottom of it, it's no big deal; you just have to scroll up. In the case of Xorg's log file, however, the last log gets **.old ** appended to its filename, and a new log is created in its old name. So as soon as you want to find out what caused the previous session to crash, you have to look at the **.old** file.

I'm not sure how GDM does its logging, and I don't have a GNOME machine around to check, I'm afraid. If there are "old" files, look at the previous one, or one you know was ended with a crash. If there's just one and it's huge, it may be that new entries are just added to the end of it (as KDM does).

You could attach it if you can't make heads or tails out of it.

---

### Post by byline on 2009-11-25
> **Zorael said:**
> (Just googling for suggestions right now, as I'm using KDM.)

There should be a directory: **/var/log/gdm**. Are there any .log files in it? Perhaps "**:0.log**"? Are there several files, or is it just one huge one?
OK, I think I just must not know where to look. I type that code in the Terminal; nothing. I look through all the pull-down menus; same thing. I even tried doing a search by typing that code; still nothing. My inexperience is showing!

I realized after I posted my initial reply that I really posted it in the wrong thread. Even though I'm experiencing a similar situation, I'm using Ubuntu Karmic Koala (not Kubuntu). Should I start a new thread? Sorry, I'm sure this is a typical newbie question!

---

### Post by jwshale on 2009-11-30
I have had several random X restarts recently...

I just checked the suggested log files and the relevant bit seems to be:

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: /lib/tls/i686/cmov/libc.so.6 [0x5dc568]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

from the kdm log, although the Xorg log gives the same error.

Any ideas?

---

### Post by Zorael on 2009-11-30
> **byline said:**
> OK, I think I just must not know where to look. I type that code in the Terminal; nothing. I look through all the pull-down menus; same thing. I even tried doing a search by typing that code; still nothing. My inexperience is showing!
**/var/log/gdm** is a path; a directory. Much like your home directory is probably **/home/username**. Inside it there should be log files of some sort (likely ending in **.log**), that you can open in a text editor.

> **jwshale said:**
> I have had several random X restarts recently...

I just checked the suggested log files and the relevant bit seems to be:

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: /lib/tls/i686/cmov/libc.so.6 [0x5dc568]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

from the kdm log, although the Xorg log gives the same error.

Any ideas?
No idea, that sounds like something that should be reported as a bug. As always, unreported bugs can only be fixed by accident.

---

### Post by byline on 2009-12-03
> **Zorael said:**
> **/var/log/gdm** is a path; a directory. Much like your home directory is probably **/home/username**. Inside it there should be log files of some sort (likely ending in **.log**), that you can open in a text editor.
OK, I tried that before. But when I type in **/var/log/gdm** in the File Browser's Location field, I get the following message: The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "gdm".

---

