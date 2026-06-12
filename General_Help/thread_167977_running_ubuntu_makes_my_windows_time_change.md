---
title: "running ubuntu makes my windows time change"
date: 2006-04-29
forum: General Help
---

### Post by Gaia on 2006-04-29
Hi,

I've noticed that everytime i run ubuntu and then run windows, the time on my windows has changed.

Any reason why Ubuntu would mess up how my Windows tells the time?

Thanks.

---

### Post by kupajava on 2006-04-29
On install of Ubuntu you tell it wether or not your PC is running GMT in BIOS.  You must have told it that you are.  It now changes your PC BIOS time every time you start,  It doesnt do anything to Windows or Windows time, it is changing your PC's BIOS time.  It does this in the brown load-up screen before login where it says "setting PC BIOS time to ntp" or something else obvious like that.

---

### Post by garner_nc on 2006-04-29
If you go into System > Administration > Time and Date you can re-configure your Ubuntu system time. This should correct your time problem.

All the Best,
Doug White

---

### Post by souki on 2006-04-29
by default, windows use local time

my personnal opinion is that it's better to have the CMOS clock set to UTC and have the system clock adjusted to the meridian time and daylight saving

I don't know about recent release of windows but it was impossible to have the cmos clock utc, so, if this is still the case, you will have to set your cmos clock to local meridian time and set linux to interpret it as such

---

### Post by Gaia on 2006-04-30
Hi, thanks for the replies, so which setting do i change within the Time and Date Settings in Ubuntu and what should I set it as?

---

### Post by Irony on 2006-04-30
The following is from my notes;

My windows clock is always 1 hour behind, even though I change the BIOS, the BIOS is reset.

The file is /etc/default/rcS, and the syntax is yes/no.

There is no need to reboot after changing the value, it will be done when you exit linux the next time.

Linux's software clock is completely independent of the hardware clock, it just uses it to get the time on boot, and set the time to it on shutdown (to save it). If the variable UTC is yes then, it will add/subtract from the time to make it UTC time, if the variable is no, it will save the clock as is.

Windows on the other hand, takes the time directly from the hardware clock at all times (AFAIK). If the UTC value in linux is yes then, this will screw the clock up (get it out of sync).

[PHP]sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS[/PHP]

Change;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes[/PHP]

to;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no[/PHP]

---

