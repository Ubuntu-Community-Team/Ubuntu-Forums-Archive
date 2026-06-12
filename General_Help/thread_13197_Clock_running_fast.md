---
title: "Clock running fast"
date: 2005-01-29
forum: General Help
---

### Post by Wombley on 2005-01-29
Hello everyone,

I've had Warty installed on my computer for quite a while now, and the time has always been running fast. On starting the computer Ubuntu synchronizes with the NTP server, and the time is set right, however over time when the computer is left switched on the time slowly goes fast. Since I am in the habit of leaving the computer on for weeks, this problem grows quite large, with the clock being over an hour out by the end of a week. The motherboard was new when I installed Ubuntu, so I dont think it's a CMOS clock problem, and I can't find anything on the forums about any similar problems. Any ideas on what this could be?

---

### Post by TravisNewman on 2005-01-29
*blinks* Over an hour? My god. I've only seen that happen on very old hardware, and it wasn't an hour every week. Have you ever had Windows installed on this machine, and if so, have you ever had these problems there? The thing is, Windows may have been syncing the clock much more often than Ubuntu, so it's hard to tell if it's a software or hardware issue.

---

### Post by Wombley on 2005-01-29
I've never had Windows on this machine, and although Mandrake (10.0 I think) is installed I haven't used it since I started using Ubuntu. As I said, it's a new motherboard (a MSI K7N2 Delta, Nforce2 based), so I'm pretty sure it isn't the CMOS battery.

---

### Post by Jad on 2005-01-30
So you are in the future now? Can you tell about Ubuntu Marsy? which release on  2010?
what about Microsoft, they still make liven?

---

### Post by rosslaird on 2005-02-11
Did you ever get this worked out?
My clock is also running fast, and every day I have to run;

sudo ntpdate -b time.nrc.ca

It did not do this before, in Debian.

---

### Post by rosslaird on 2005-02-11
Update:

making progress. I think the problem is ntpdate (at least on my machine):

> ntpdate sets the system clock once and mostly in a brute way. As real clocks drift, you need periodic corrections. Basically you can run ntpdate in a cron job hourly or daily, but your machine won't be an NTP server then.

I'm reading [here](http://www.ntp.org/ntpfaq/NTP-s-config.htm).

Update 2:

I ran ntpq -p as root (as a diagnostic). "Connection refused."
I ran apt-get install ntp-simple (already most recent version).
I ran dpkg-reconfigure ntp-simple. 
(worked, but with an odd error message: "*art-stop-daemon: warning: failed to kill 6586: No such process")
I ran ntpq -p again, and now it seems to be working (at least ntp seems to be working; we'll see how it keeps the clock).

Apparently ntpdate only syncs the clock at boot, or upon command. The ntp daemon ntpd is required for consistent sync (but it was installed: both ntp and ntp-simple; they just weren't working, and actually I still don't know why... strange problem).

Ross

---

### Post by Wombley on 2005-03-05
[QUOTE=rosslaird]Update:

making progress. I think the problem is ntpdate (at least on my machine):



I'm reading [here](http://www.ntp.org/ntpfaq/NTP-s-config.htm).

Update 2:

I ran ntpq -p as root (as a diagnostic). "Connection refused."
I ran apt-get install ntp-simple (already most recent version).
I ran dpkg-reconfigure ntp-simple. 
(worked, but with an odd error message: "*art-stop-daemon: warning: failed to kill 6586: No such process")
I ran ntpq -p again, and now it seems to be working (at least ntp seems to be working; we'll see how it keeps the clock).

Apparently ntpdate only syncs the clock at boot, or upon command. The ntp daemon ntpd is required for consistent sync (but it was installed: both ntp and ntp-simple; they just weren't working, and actually I still don't know why... strange problem).

Ross[/QUOTE]
 Sorry for taking so long to respond, haven't checked the forums lately. Anyway, thanks for the pointers for this. I still think it's some bug causing this, normal system drift shouldn't cause hours of difference, but hopefully this should at least make the problem not noticable. I think you meant to say dpkg-reconfigure ntp-server - this is the one that seems to set it up. The error message is caused (I think) by it trying to restart the server when the server isn't running, therefore it tries to kill a nonexistant process. Also I have an idea that the reason ntp-server didn't work even when installed was that /etc/ntp.conf wasnt created, but I didn't think of this until after running dpkg-reconfigure so I can't test it. It *is* a strange problem, but hopefully this will work, and thanks again!

Edit: Still seems not to work, even with ntp apparently working fine I'm still gaining quite a few minutes a day. I'm completely lost now, so I'll just put ntpdate in a cron job do it, unless anyone has any other ideas?

---

### Post by gmc on 2005-05-10
Interesting! I too have a system (desktop) that is showing similar symptoms however my clock drift is very pronounced. I appear to be running fast by about 1 second every 90 seconds. This started a few weeks ago. The most unusual thing about this problem is:

(1) I have two servers that began showing the cmos clock running fast, though not quite as bad as the desktop.

(2) The problem with these the server systems went away, when I reinstalled hoary. (not that I'm suggesting it's problem in hoary).

(3) All three computers are using ASUS A7N8X motherboards (nForce2 chipsets).

I've just reinstalled hoary on my desktop system but the problem persists. All three systems run 24/7. I'm at a complete lost as to explain what is causing this problem. I've tinkered with the CMOS settings on one of the servers and the desktop system, I'm not over clocking any of the systems, none of the system need their cmos settings corrected if they are powered down for any length of time. Anyone have any ideas? 

G.

---

### Post by gmc on 2005-05-10
I might be onto something here. If you search google with "ntpd 2.6.10" - there seems to be some sort of problem with the kernel with regards to time keeping. This would also make sense, as I previously reported, the problem went away after reinstalling Ubuntu. The servers are using a 2.6.8 kernel, were as my desktop system is running the current 2.6.10 kernel. I'll keep digging...

G.

---

### Post by gmc on 2005-05-10
BINGO! I have confirmed it. There is a problem with the 2.6.10 kernel and keeping proper time. There's a (bit dated) discussion about the problem on kerneltrap.org ([http://kerneltrap.org/node/4872#comment-129554)](http://kerneltrap.org/node/4872#comment-129554)).

After rebooting my desktop system back to 2.6.8 kernel from warty, the time problem goes away. 

G.

---

### Post by Wombley on 2005-05-11
[QUOTE=gmc]BINGO! I have confirmed it. There is a problem with the 2.6.10 kernel and keeping proper time. There's a (bit dated) discussion about the problem on kerneltrap.org ([http://kerneltrap.org/node/4872#comment-129554)](http://kerneltrap.org/node/4872#comment-129554)).

After rebooting my desktop system back to 2.6.8 kernel from warty, the time problem goes away. 

G.[/QUOTE]

I had this problem on Warty to begin with, but it could be the source of the problem, and I think it did get worse upgrading to Hoary. Going back to 2.6.8 isn't really an option for me (for various kernel-module related reasons), so I'll keep looking (although it seems from this to be NForce2 chipsets that are affected). Glad you got it fixed at least!

---

### Post by zue on 2005-06-21
/bump

I wanted to resurrect this thread because I'm having the same problem with Hoary installed, but it's even more pronounced.  My system clock is actually running, get this, more than twice as fast as it should be.  I'm gaining more than an hour every hour!  I checked the hardware clock with hwclock --show and it looks like it's running normal speed.  I never had warty installed, but when I pop in the live cd I have the same problem.

Has anyone found a fix for this?  Synching the clock periodically with a server is obviously not an option for me.  With this kind of dicrepancy, it would have to synch continously.

---

### Post by Wombley on 2005-06-21
You may want to have a look here: [http://fedoraforum.org/forum/showthread.php?t=51012](http://fedoraforum.org/forum/showthread.php?t=51012)

Trying a couple of things myself right now, but due to actually having to wait to see if it works it's a bit slow going...

---

### Post by zue on 2005-06-21
[QUOTE=Wombley]You may want to have a look here: [http://fedoraforum.org/forum/showthread.php?t=51012](http://fedoraforum.org/forum/showthread.php?t=51012)

Trying a couple of things myself right now, but due to actually having to wait to see if it works it's a bit slow going...[/QUOTE]


Well, I tried editing /boot/grub/menu.lst ...no go.   :-?   The code now looks like:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro console=tty0 no_timer_check

(I added the no_timer_check)

then I rebooted and ran grub-update, but the clock is still zooming away at > twice normal speed.

Did I maybe miss something?  Should I put the no_timer_check option somewhere else?

Zue

---

### Post by twistymcgee on 2005-07-01
I am also experiencing the problem.  I'm running Hoary with 2.6.10 kernel on MSI K7N2 MS-6570 motherboard which uses the nVidia chipset.  I get about 30 minutes ahead after a couple of days.  Since no one can figure out a fix I'll just go with a cron job for now.

---

### Post by cynagen on 2005-07-03
I just did a search on Google for this very same issue and got here to you guys...

Here's the thing... I'm running an MSI K7N2 Delta-L just like one of the other guys that's posted here before... now here's the difference... I run Windows AND Linux on this system...

Windows 98 (For legacy gaming [Doom, Duke, Red Alert])
Windows XP (Default OS)
Slackware 10.0 (Secondary OS/Primary Linux OS)

MY CLOCK RUNS FAST! I was looking for a fix... mine is really bad... for every 30 minutes... my computer logs 35, every hour is 1:10~1:12... I don't think it's a software issue... I think it's a clock and power issue. I recently looked at SpeedFan and noticed my CMOS battery output running a bit high, and it only puts out what's there or what's being charged. I've seen it run unusually high... and sometimes just a pinch high. The battery is suppost to run at 3.00v, and as i'm typing this up, it's running at 3.01, and when I checked, it was only about 3 minutes fast after resetting it hours ago. *points at the nVidia chipset* It's got to be something with the chipset, something's not withholding power properly and it's speeding up the clock. I've had the battery run low, below 3.00v before... I think it was at 2.65v one time I checked, and the clock was fine... It's just that once it hits and passes peak, it seems to let the clock speed up without remorse or care... Makes everyone's life hell... (16 minutes later) I checked the power output 3.01v and it was 2 minutes fast... This is not cool and i'm going to have to call nVidia and ask them if they know about this flaw. And if they have a BIOS patch to stop that from happening.

---

### Post by wembly6 on 2005-10-15
I am having exactly the same problem on my MSI K7N2 Delta-L. I am dual booting Win2k and Ubuntu, and the clock is gaining about 10 mins an hour. I have had a quick search around on the forums, and can't seem to find an answer. I am a bit of a linux newbie, so don't want to start messing with things I don't understand.
Does anyone have an answer how to solve this problem?

---

### Post by Wombley on 2005-10-16
[QUOTE=wembly6]I am having exactly the same problem on my MSI K7N2 Delta-L. I am dual booting Win2k and Ubuntu, and the clock is gaining about 10 mins an hour. I have had a quick search around on the forums, and can't seem to find an answer. I am a bit of a linux newbie, so don't want to start messing with things I don't understand.
Does anyone have an answer how to solve this problem?[/QUOTE]

I've found the noapic kernel option gets it down to about 15 seconds a day, which is far more acceptable. To see if this works, when you get to the menu asking what kernel to boot at bootup, press e, go down to the kernel line, press e again, go to the end and type "noapic" at the end, then follow the instructions to boot. If this fixes it, you can set this option in grub so it applies for every bootup - I'd have to look up how to do this though. I don't think the no_timer_check option is implemented in Hoary's kernel - may be in Breezy, but I haven't installed that yet.

---

### Post by iMerlin on 2005-10-27
I'm having the same problems on my new laptop (MSI Megabook, ATI chipset).

First noticed this when VLC started playing all my movies a bit too fast. Then when I make the system clock show seconds these are no normal seconds.

It appears that 1 second = 1.5 second on my system. Which might get me quicker home from work but doesn't suit me very well. NTP sync doesn't solve this because it's too skeewy.

The BIOS clock is normal and so is the Windows clock (dual boot).

Any thoughts?

---

### Post by Slalomsk8er on 2005-11-27
I hope this helps to fix your nforce2 clock drifts: [http://www.ussg.iu.edu/hypermail/linux/kernel/0410.1/1505.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0410.1/1505.html) 

I fixed my shuttle sn42g2 and my asus A7N8X with this BIOS setting.

---

### Post by iMerlin on 2005-11-28
FYI

What fixed my problem was adding 'noapictimer' to my boot options.

Running 32bit Ubuntu on AMD Turion.

---

