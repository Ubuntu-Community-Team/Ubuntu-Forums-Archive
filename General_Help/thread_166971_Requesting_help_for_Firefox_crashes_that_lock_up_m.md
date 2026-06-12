---
title: "Requesting help for Firefox crashes that lock up my Gnome desktop"
date: 2006-04-27
forum: General Help
---

### Post by bswilson on 2006-04-27
Friends, I have a problem and could use some guidance.

I'm running Ubuntu 5.10, with Firefox 1.5 installed via Automatix.  Every now and again, I'll be running Firefox heavily (e.g., switching through tabs, opening and closing tabs), and all of the sudden, my system freezes.

Now when I say *freezes*, what happens is the mouse no longer moves and keyboard input is not received.  But **more troublesome** is that I cannot switch to another session via Ctrl-F[1-7] at all, and I cannot restart my X session via Ctrl-Alt-Backspace.

The only thing I've been able to do to fix my situation is to actually press the reset button on my PC.  I am comfortable that I have no missing package dependancies, and I check my system for updates (and apply them) daily.

Overall, I have no idea where to look for data.  Can someone start by telling me where Firefox and Gnome errors are logged?  I've looked in */var/log/messages* and */var/log/syslog*, but nothing is jumping out at me...

Thanks in advance for your help!

---

### Post by schmidty on 2006-05-08
I am having the same problems too...crashes unexpectedly and locks up occassionally under Breezy. I noticed Mozilla does the same thing as well as Thunderbird. Where are the log files for these clients?!? Can we install them with a log file? I thought you could create an error log from the terminal like this;

firefox & 2>> ff_errors.log

Schmidty

---

### Post by dan4444 on 2006-05-09
I have the same problem, for the most part.

Specifically for me, at a time when I have at least a couple firefox windows open, all of a sudden my keyboard will completely stop responding and my mouse cursor will appear, but the only thing I can do with it is to move windows via a window's top title bar and subsequently bring new windows into view by clicking on them.

This seems to happen to me about once a day lately.

---

### Post by berzerke on 2006-05-10
Add someone else to the list of users having about the same issue. I'm using Kubuntu 5.10 and have been forced to mostly use Konqueror. Here's what I've discovered so far:

The firefox that comes via apt doesn't start at all for me. The latest one from mozilla.com (1.5.0.3) after a short time will lock up the system. Xorg starts using 100% of the available memory (and swap, so my HD starts thrashing like crazy), and Firefox uses almost 100% of my CPU. If I'm patient enough to kill Firefox, Xorg does not return to normal until I log out and back in.

I still have an old version (1.5) in my home directory and when I use that, I still get the 100% CPU usage after a short time, but at least Xorg behaves (it's been hovering around 20% for 5 days). So, I can conclude there is a memory leak in 1.5.0.3 under Ubuntu (maybe Linux in general; 1.5.0.3 seems fine under Windows).

Now as to why CPU usage shoots up, I don't know. I recently converted from Mandriva and I used the 1.5 version without incident, so something must be wrong in 5.10. But what?

---

### Post by pedalwrench on 2006-05-10
I am also having this problem.  I have the same install as everyone else in the thread.

Any help on this would be great...

---

### Post by bswilson on 2006-05-18
[SIZE="4"]Followup[/SIZE]

I **still** haven't been able to figure out of my problem is Firefox related, Gnome related, or Ubuntu related...  I'll keep digging.  Perhaps when Firefox 2.0 comes out, we'll have the issue addressed.

*Still* looking for help from anyone who can tell us where Firefox logs its error messages...

---

### Post by sciyoshi on 2006-05-18
I was getting the same thing a while ago, but I thought it was a kernel panic since nothing was responding... doesn't happen anymore though

---

### Post by schmidty on 2006-05-19
Hey...I may have somthing here!!! I was so tired of Firefox and Thunderbird crashing I decided to try out KDE. I downloaded it with Synaptic and tested it. I went back to Gnome and have been using Firefox and T-Bird now for several hours WITHOUT any crashes!!! I am not sure why but I was having trouble installing the xmms Debian package. I was able to get that fixed and intalled and since that time everything has been fine...not sure what I did right?!? Let me know if this helps anyone else out.

Schmidty

---

### Post by rcarring on 2006-05-19
I think it is that Gnome is very system heavy, and running a heavy app like Ff screws it up, that's why under KDE you get better results.

I am rapidly forming the opinion that FF sucks big time on Linux especially v 1.5.0.3 as it takes ages to load pages that in Mozilla 1.7.12 or 1.7.13 load almost instantly.

I admit I am a huge fan of Netscape having used it since version 2.0 in 1996.

---

### Post by schmidty on 2006-05-20
Well...no dice!!! FF crashed this morning twice in less than a half hour under Gnome. I didn't seem to have any probs with Kubuntu although I am going to run  default with Kubuntu from now on and see how it works. I'm also going to pull all of my extensions. The one extension I really want to keep is Pederick's web developer extension. If anyone is having random crashes and lockups in Breezy with FF 1.5.0.3 don't hesitate to speak up! I will try some other ideas and post them here soon...

Schmidty

---

### Post by pedalwrench on 2006-05-30
[QUOTE=pedalwrench]I am also having this problem.  I have the same install as everyone else in the thread.

Any help on this would be great...[/QUOTE]

Just an update...

I found that I was getting DMA errors on the drive that the OS was installed on.  I have since replaced the drive and have had no lockups for a while now.

So you may want to check out all logs and look for a drive not ready type error.

p

---

### Post by bswilson on 2006-06-02
Everyone has posted some good information, althought I don't think we have the 'smoking gun' yet...  Just an update from my side; I've upgraded to Dapper (6.06) and also upgraded Firefox to 1.5.0.4 which was just released (security fixes only, though).

I don't know if this will remedy the problem I was having on Breezy, but we'll see how it goes...

---

### Post by kainaw on 2006-11-06
Just a note: This is not only with Ubuntu.  I have the same problem on Fedora Core 5 and Fedora Core 6, both using KDE.  I suspected it was a bug in how KDE handles GTK apps because a similar issue happens with Gaim.  So, I now use Konqueror and Kopete.  Never have a lockup.  If I start Firefox or Gaim, I am certain to have a lockup sometime in the near future - even if I'm not actively using either one.  I want to find a way to log EVERYTHING from Firefox to try and solve this problem, but even running in debug mode, firefox doesn't print any error out before the keyboard-mouse-video-sound lockup.  As for the DMA errors.  I've gone through 3 harddrives now.  They are fine - no errors.  After a few Firefox lockups, they are full of errors.  I've run a Fedora Core 5 box for 3 months with identical hardware to my PC and did not install Firefox.  It has no errors and runs all day every day without trouble.  My PC continually locks up when I run Firefox.

---

