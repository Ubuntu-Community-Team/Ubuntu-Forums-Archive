---
title: "Ubuntu not taking DST (Daylight Saving Time) into account."
date: 2006-03-26
forum: General Help
---

### Post by bernardfrancois on 2006-03-26
Hi,

Lol, nobody posted in this forum before, while this site is soooo busy. Anyway, this is the place I thought my post should be. Now to the topic:

I noticed my clock didn't change after this night. In Belgium and most other European countries, the clock changes twice a year (one hour back when winter ends, one hour later when winter starts). This is called Daylight Saving Time (DST) or Summer Time. For more information, read the [ page on wikipedia](http://en.wikipedia.org/wiki/Daylight_saving_time).

Belgium is not an exception, and outside Europe there are other countries using DST.

My computer has Ubuntu as it's only operating system.
If I open *Time and Date Settings* (under System > Administration > Time and Date) I can see that I set my time zone properly: **Time zone: Europe/Brussels**.

I'm not asking for anyone to tell me how I can change my system clock myself. I'm not asking for advice on how to configure a time server. What I want is the operating system to change the time automatically to DST when needed, without being helped by a time server.

---

### Post by Alex[RM-UK] on 2006-03-26
Don't the clocks go forward tonight? That could be why your system clock did not update, wait untill tomorrow then it should.

---

### Post by bernardfrancois on 2006-03-26
The time change already took place last night at 2:00 (about 10.5 hours ago).

If you say 'tonight' I don't have a clue what you mean since you're probably in another time zone. Here in Belgium the time already changed, but Ubuntu didn't change anything.

---

### Post by Gallows on 2006-03-26
Just to add to this I had to manually move the time on Ubuntu Dapper to take into account of the UK / BST time change today 26/03/2006.  I too assumed that DST changes would be handled automagically but maybe it's just becuase I've not selcted a DST option in the time-admin "Date and Time Settings" appelet?

---

### Post by 0xBulbizarre on 2006-03-26
Exactly the same problem here (switzerland) with /etc/localtime set correctly.

I found that in /etc/default/rcS the line
```
UTC=no
```
was wrong, my hardware clock is set (by ntp) to GMT. So I had to change /etc/default/rcS to
```
UTC=yes
```

Maybe you just need to reboot to apply the change, I don't know. What I did was:
```

sudo /etc/init.d/ntp-server stop
sudo ntpdate pool.ntp.org
sudo /etc/init.d/hwclock.sh restart
sudo /etc/init.d/ntp-server start

```

And I just hope that everything about DST will be going well in 6 months ...

---

### Post by bernardfrancois on 2006-03-26
[QUOTE=0xBulbizarre]And I just hope that everything about DST will be going well in 6 months ...[/QUOTE]

I don't think that will make a difference. But I will try it. You don't need to wait for 6 months, just change your clock to March 25, 23:55 or something like that, and you will see if it helped after waiting a few minutes...

---

### Post by lorenzo on 2006-03-27
I have the same problem (in Italy). My clock this morning is one hour back.... Is there a configuration parameter to make ubuntu take into account Daylight Saving Time?

Lorenzo

Update:
It seems that time information is retrieved from the file (in my case):

/usr/share/zoneinfo/Europe/Rome

In it there's only the string "TZif"......

I have found two commands:

tzconfig
tzselect

...but nothing changes. So I suppose the "TZ" database is missing or not working properly.

Does anyone have a clearer idea on what "TZ" is and how does it work?

---

### Post by 0xBulbizarre on 2006-03-27
[QUOTE=lorenzo]I have the same problem (in Italy). My clock this morning is one hour back.... Is there a configuration parameter to make ubuntu take into account Daylight Saving Time?

Lorenzo[/QUOTE]

Did you read my post above ? It seems you didn't ... too bad it contains the solution you just need ;)

---

### Post by 0xBulbizarre on 2006-03-27
[QUOTE=bernardfrancois]I don't think that will make a difference. But I will try it. You don't need to wait for 6 months, just change your clock to March 25, 23:55 or something like that, and you will see if it helped after waiting a few minutes...[/QUOTE]

It does make a difference! One of the computers here at work had this "UTC" line of /etc/default/rcS set to yes, and the clock perfectly updated to new daylight saving time.

Do you want to know why ?
---> read about hwclock
---> read /etc/init.d/hwclock.sh script (especially where it sources /etc/default/rcS)
---> realize that your hardware clock is set to GMT...

---

### Post by nocturn on 2006-03-27
[QUOTE=bernardfrancois]
I'm not asking for anyone to tell me how I can change my system clock myself. I'm not asking for advice on how to configure a time server. What I want is the operating system to change the time automatically to DST when needed, without being helped by a time server.[/QUOTE]

Strange... Actually, mine changed fine this weekend (also from Belgium).

Is your hardware clock set to UTC?

What do you get when you type date in a terminal?

---

### Post by nocturn on 2006-03-27
Some explanation maybe.

Linux keeps it's internal time in UTC, the displayed time is always calculated from that.

So, when the time changed this weekend, my clock didn't jump anywhere, but my system went from the CET timezone (UTC+0100) to CEST (CET with DST, UTC+0200).

Those who did not have this happen can check if their hwclock is set to UTC, you need to disable this to get dual boot with windows right.

---

### Post by bernardfrancois on 2006-03-27
```

:-) grep UTC /etc/default/rcS
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
:-) date
Mon Mar 27 18:56:50 CEST 2006

```

Note that it's on Ubuntu 5.04 and that it is the only operating system on my computer.

---

### Post by imagine on 2006-03-27
Linux knows two clocks: The hardware clock (BIOS clock) and the local time. Linux only works with its local time and never touches the hardware clock, except when you explicitly tell it to do so (by using hwclock --systohc).

So, in a perfect world (tm) the hardware clock would be set to UTC (also known as GMT), the Linux system would know the location where it is and based on this information calculates the correct local time, including daylight saving time and all other weird changes.

Everybody who dualboots Linux and Windows on the same machine does *not* live in this perfect world, because Windows doesn't know what UTC or a calculated local time is. When you change the clock in Windows, Windows changes the BIOS clock and thereby also affects Linux.
Because of that, the option exists to set up the Linux system to work as Windows does: Just look up the BIOS time and use that. In that case Linux won't change the BIOS clock to the daylight saving time either, because it cannot know if Windows already did that.
So the solution is to boot Windows once to change the time. If you don't have Windows on that machine, then set your BIOS clock to UTC and let Linux handle the rest.

---

### Post by bernardfrancois on 2006-03-28
In that case, Ubuntu should have changed my hardware clock (just as Windows does).

I guess that the UTC=no option is only for compatibility with Windows in dual boot (otherwise, it would have changed the hardware clock). When someone installs Ubuntu, the appropriate question to ask is not 'is your system clock set to GMT', the question should be: 'do you want to use Ubuntu along with Windows in a dual-boot setup?'.

---

### Post by lorenzo on 2006-03-28
That's why in a previous release I had clock going back & forth every time I changed from windows to linux!!!!!!

Knowing that.... I prefer to change the clock every 6 months instead of every day...... (unfortunately I need dual boot on my laptop....).

Thank you all.
Lorenzo

---

### Post by nocturn on 2006-03-29
[QUOTE=bernardfrancois]```

:-) grep UTC /etc/default/rcS
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
:-) date
Mon Mar 27 18:56:50 CEST 2006

```

Note that it's on Ubuntu 5.04 and that it is the only operating system on my computer.[/QUOTE]

I think this was asked during the install procedure.

My server, Ubuntu 5.04 has this setting to yes, as do my Breezy machines.

---

### Post by nocturn on 2006-03-29
[QUOTE=bernardfrancois]```

Mon Mar 27 18:56:50 CEST 2006

```
[/QUOTE]

It's in the correct timezone though, CEST is the DST zone for your location.

---

### Post by bernardfrancois on 2006-03-29
[QUOTE=nocturn]It's in the correct timezone though, CEST is the DST zone for your location.[/QUOTE]

Since it's the correct time zone, Ubuntu should adjust my system clock, wheter it's using the hardware clock directly or indirectly.

But this will cause troubles for people who combine Ubuntu with Windows. Therefore, I suggest that the installation procedure should ask '*do you want to use the hardware clock for compatibility with M$ Windows?*' instead of what is asked now when the UTC option is set.

Somehow this is still a bad solution, since then you'll have to wait for windows to set the DST... I guess a good solution for this doesn't exist in a dual boot configuration (appart from using a time server for both OSs). But now other people (like me) are also bugged with it (if they didn't set the UTC option correctly... which is likely since there's no good explanation about it during the installation process).

---

### Post by blastus on 2006-04-02
I'm using Kubuntu and none of the info in this forum has fixed my clock. I tried changing UTC=yes in /etc/default/rcS and rebooted but it did nothing. Furthermore, I can't even manually adjust the time in the clock applet because the "Adjust Date and Time..." option does absolutely nothing. As soon as I click on it, it asks for me for my password, which I type in, and then the dialog goes away and NOTHING happens.

> Exactly the same problem here (switzerland) with /etc/localtime set correctly.

I found that in /etc/default/rcS the line
Code:

UTC=no

was wrong, my hardware clock is set (by ntp) to GMT. So I had to change /etc/default/rcS to
Code:

UTC=yes


Maybe you just need to reboot to apply the change, I don't know. What I did was:
Code:

sudo /etc/init.d/ntp-server stop sudo ntpdate pool.ntp.org sudo /etc/init.d/hwclock.sh restart sudo /etc/init.d/ntp-server start


And I just hope that everything about DST will be going well in 6 months ...

This doesn't work for me. 

```
sudo /etc/init.d/ntp-server stop
```

sudo: /etc/init.d/ntp-server: command not found

```
sudo ntpdate pool.ntp.org
```

 2 Apr 08:07:02 ntpdate[8900]: sendto(shell.petertodd.ca): Operation not permitted
 2 Apr 08:07:02 ntpdate[8900]: sendto(pi.codefab.com): Operation not permitted
 2 Apr 08:07:02 ntpdate[8900]: sendto(203.191.164.162): Operation not permitted
 2 Apr 08:07:02 ntpdate[8900]: sendto(ntp2.sil.at): Operation not permitted
 2 Apr 08:07:02 ntpdate[8900]: sendto(mabuse.homeip.net): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(shell.petertodd.ca): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(206.57.44.149): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(pi.codefab.com): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(216.52.237.153): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(203.191.164.162): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(snm.sd.dreamhost.com): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(ntp2.sil.at): Operation not permitted
 2 Apr 08:07:03 ntpdate[8900]: sendto(ns2.national-net.com): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(mabuse.homeip.net): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(ns1.exa-networks.co.uk): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(shell.petertodd.ca): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(206.57.44.149): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(ns.pf.uni-c.dk): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(pi.codefab.com): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(216.52.237.153): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(roma.coe.ufrj.br): Operation not permitted
 2 Apr 08:07:04 ntpdate[8900]: sendto(203.191.164.162): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(snm.sd.dreamhost.com): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(cazza.aceonline.com.au): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(ntp2.sil.at): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(ns2.national-net.com): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(mabuse.homeip.net): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(ns1.exa-networks.co.uk): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(shell.petertodd.ca): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(206.57.44.149): Operation not permitted
 2 Apr 08:07:05 ntpdate[8900]: sendto(ns.pf.uni-c.dk): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(pi.codefab.com): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(216.52.237.153): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(roma.coe.ufrj.br): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(203.191.164.162): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(snm.sd.dreamhost.com): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(cazza.aceonline.com.au): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(ntp2.sil.at): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(ns2.national-net.com): Operation not permitted
 2 Apr 08:07:06 ntpdate[8900]: sendto(mabuse.homeip.net): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(ns1.exa-networks.co.uk): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(206.57.44.149): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(ns.pf.uni-c.dk): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(216.52.237.153): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(roma.coe.ufrj.br): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(snm.sd.dreamhost.com): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(cazza.aceonline.com.au): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(ns2.national-net.com): Operation not permitted
 2 Apr 08:07:07 ntpdate[8900]: sendto(ns1.exa-networks.co.uk): Operation not permitted
 2 Apr 08:07:08 ntpdate[8900]: sendto(ns.pf.uni-c.dk): Operation not permitted
 2 Apr 08:07:08 ntpdate[8900]: sendto(roma.coe.ufrj.br): Operation not permitted
 2 Apr 08:07:08 ntpdate[8900]: sendto(cazza.aceonline.com.au): Operation not permitted
 2 Apr 08:07:09 ntpdate[8900]: no server suitable for synchronization found

```
sudo /etc/init.d/hwclock.sh restart
```

This command actually appears to do something:
* Saving the system clock... [ ok ]

```
sudo /etc/init.d/ntp-server start
```

sudo: /etc/init.d/ntp-server: command not found

This is really irritating, not only does Kubuntu not adjust for Daylight Savings Time, but I can't even manually adjust the damn time. :mad:  Is there any way possible to change the time in Breezy Kubuntu or should I just forget about it and just upgrade to Dapper Kubuntu?

---

### Post by pilpi on 2006-04-19
> I'm using Kubuntu and none of the info in this forum has fixed my clock. I tried changing UTC=yes in /etc/default/rcS and rebooted but it did nothing. Furthermore, I can't even manually adjust the time in the clock applet because the "Adjust Date and Time..." option does absolutely nothing. As soon as I click on it, it asks for me for my password, which I type in, and then the dialog goes away and NOTHING happens.

Seems that your /etc/sudoers file doesn't have your username , which seems to result from a bug in ubuntu installer. That's why "Adjust Date and Time..." doesn't do anything - your user doesn't have the rights to become root.

Do 'su' to become root (hope you have that password) or reboot to select the recovery console from the boot menu. Edit /etc/sudoers. Add the following to the end, substituting "[username]" with the username you wish to give permission to become root with sudo.

More info about the Ubuntu way of getting root rights: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

[username]    ALL=(ALL) ALL

---

### Post by NigelHarrison on 2007-10-28
I know this is a long time after this thread dried up, but I note that (on Gutsy at least) the ntp server script is called just ntp, not ntp-server.

Hope that helps

Nigel

---

### Post by dadaftsplat on 2007-11-06
Hi, I tried the fix below, and I got the following error.

XX@XX:$ sudo /etc/init.d/ ntp stop
* Stopping NTP server ntpd
XX@XXX $sudo /etc/init.d/ntpdate pool.ntp.org
6 Nov 10:54:57 ntpdate[6143]:no server suitable for synchronization found

Any help?

Aaron

---

### Post by NigelHarrison on 2007-11-13
dadaftsplat:

I just tried:

sudo /etc/init.d/ntp stop
* Stopping NTP server ntpd
sudo nto pool.ntp.org
13 Nov 22:19:08: ntpdate[19727]: step time server 192.33.96.102 offset 8.000922 sec

It seemed to  work as expected.

Nigel

---

### Post by himikeb on 2008-03-10
I'm in the Los Angeles PST time zone and everything has been fine.
I would swear that yesterday (March 9th, first day of DST), my Ubuntu Gutsy system showed the correct Time.  But today, March 10th, the first day after DST started, my Ubuntu computer is back on PST (1 hour slow).
Is it me or are others seeing this?  Also, in the time-admin control applet, there is no option to enable Daylight Savings?

---

### Post by himikeb on 2008-03-10
Nevermind - The setting in rcS was set to NO.  Changing that to yes fixed it.

But still, what happened to the "Adjust for Daylight Savings time" option?  Or is it that I still use windows  (at work, not worthy of uppercase) from time to time??

---

### Post by UphillSkier on 2008-03-12
> **himikeb said:**
> Nevermind - The setting in rcS was set to NO.  Changing that to yes fixed it.

But still, what happened to the "Adjust for Daylight Savings time" option?  Or is it that I still use windows  (at work, not worthy of uppercase) from time to time??

himikeb, can you tell me what you mean by the rcS setting?  I am having the same problem (i.e. clock still shows eastern standard time when I should be on daylight.) and tzdata seems ok:

xxx@xxx~$ sudo zdump -v /etc/localtime |grep 2008
[sudo] password for mullera:
[sudo] password for xxx
/etc/localtime  Sun Mar  9 06:59:59 2008 UTC = Sun Mar  9 01:59:59 2008 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar  9 07:00:00 2008 UTC = Sun Mar  9 03:00:00 2008 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  2 05:59:59 2008 UTC = Sun Nov  2 01:59:59 2008 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  2 06:00:00 2008 UTC = Sun Nov  2 01:00:00 2008 EST isdst=0 gmtoff=-18000


thanks for any help

---

### Post by gfunkdave on 2008-03-13
@Uphill-

I just had the same problem. Following the instructions outlined in this thread fixed it (specifically in post #5)

Specifically (commands from post #5 modified for ubuntu):

-Set the UTC line in /etc/default/rcS to YES
-sudo /etc/init.d/ntp stop
-sudo ntpdate pool.ntp.org
-sudo /etc/init.d/hwclock.sh restart
-sudo /etc/init.d/ntp start

The third command informed me my clock was off by about an hour, and now all's well.

---

### Post by IceaTronic on 2008-03-29
I seem to be having the opposite issue here with my 7.1 install. 

Here in australia, the DST got pushed back a week, so effectively making it a week longer. One of my other boxes has adjusted fine and not moved back an hour, but the one in question has. Ive tried all the suggestions here and none of them seem to be working. Apparently tzdata is correct and functional and as such, it SHOULD be still ont he same time zone it was 24 hours ago?

Does any one have any ideas?

---

### Post by ario on 2008-03-29
I didn't find any Graphical User interface in Ubuntu Operating system Like a simple Check box and a little text that says: "Enable adjust for daylight saving time (DST)"
I looks like programmers forget to add this to linux. 
If anyone know how to enable this damn option I will appreciate it a lot!
Thanks.

---

### Post by IceaTronic on 2008-03-29
Im not running a GUia nd as such dont have the luxuries of point and click like you guys do.

Any help would be greatly appreciated!

Cheers,

IceaTronic

---

### Post by dmitrijledkov on 2008-03-31
I did this and now when i type date in the terminal I get correct time but gnome applet still shows -1 hour.

:mad:

Thanks a lot though =D

---

### Post by simonro on 2008-04-01
There may be more than one problem here but I think there is an amount of confusion about what is really going on. I checked the time on my gutsy laptop and sure enough the time appears to have not updated following the +1 hour change last Sunday (I don't use this laptop every day!). I struggled for a while looking for settings and configs that I could change to no avail. I even tried the earlier suggestions in this post which made no difference for me.

Then I had a blinding flash of inspiration... The displayed clock on the top right of my screen showing the time - I right clicked and selected "Preferences" and saw a check box for "Use UTC". Now I had seen this before but interpreted it as "Use UTC for time input" which of course I would like. 

The flash of inspiration was that these are actually **display** options. So I unchecked the option as for a display option I don't want to see UTC, I want to see (in my case) GMT/BST. _Unchecking the "Use UTC" has the desired effect for me_. The time is now correct and is synch'd to internet time via ntp. Perfect.

Just in case you are wondering I changed the date to November 1st (manually) and sync'd and it changed the time -1 hour (as expected).

HTH!

---

### Post by athianos on 2008-04-01
Just to get some key words in here.

Your solution to the clock change BST GMT time zone problem is perfect!
Right Click Time, Preferences, uncheck 'use UTC'. Instantly my time is correct. Not one hour behind as before.
March 2008 for a definitive solution is a long time - this is quite a thread!
Thanks guys, 

Kudos to simonro!

A

---

### Post by forger on 2008-04-08
You can fix this problem by enabling ntp through system > administration > time and date
I recommend to uncheck the .ubuntu.com ntp and then use only these two servers:
```
time.nist.gov 
ntp.nasa.gov
```


If you want a notification to popup just like in windows support this idea: [http://brainstorm.ubuntu.com/idea/4978/](http://brainstorm.ubuntu.com/idea/4978/)

---

### Post by Slick.N on 2008-07-15
I don't see an option to use UTC in my time/date applet (Hardy Ubuntu). Where is it?

If I could find it, I would like to uncheck it, since my system has the time set correctly but insists on displaying UTC. File time stamps are correctly displaying (for me) British Summer Time.

Thanks

---

