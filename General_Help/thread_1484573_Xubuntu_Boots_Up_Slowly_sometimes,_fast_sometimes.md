---
title: "Xubuntu Boots Up Slowly sometimes, fast sometimes"
date: 2010-05-15
forum: General Help
---

### Post by isaacd on 2010-05-15
[U]**[EDIT]** I should have called this: xubuntu boots up and runs slowly sometimes, quickly sometimes

The problem:[/U] after I boot the computer up, sometimes is runs incredibly slowly, and other times it runs at normal speed. The pattern I have noticed so far is that when I boot it up for the first time in a while (for instance, after a couple days), it runs incredibly slowly, so slow that when I try to move the pointer around with the mouse, it lags. Once I shut it down, and boot back up again, it runs at a normal speed.

_The context of the problem:_ I have just (less than a week ago) installed xubuntu on a machine to replace a broken windows 2000 system that was broken due to a virus. On the installation, I decided to completely get rid of the windows 2000 partition so that it was all xubuntu. When I was installing from the live CD, it also ran extremely slow.

_The System:_
Xubuntu version: 10.04 LTS
Username: musicdirector
Password: *****************
Architecture: Intel i386*
Processor: AMD Athlon(tm) XP 2200+
Processor Speed: I think it is 1800 MHz, although I am not sure.

*I did not download the 64 bit installer (AMD64) even though the processor is an AMD. I do not think that the "AMD Athlon(tm) XP 2200+" is 64 bit, but I don't know.

The computer is on a windows network (I belive it is the only linux computer). The internet connection is "Auto eth0".

_Attachments:_
Attached are two screenshots. 

The screenshot named slow.jpg shows all of the processes that were running (according to the system monitor) and their other stats (like CPU usage, Memory usage) about 2 minutes after boot up. The screenshot slow.png was taken on one of the "slow" bootups.

The screenshot named fast_to_slow_comparison.jpg shows all of the processes that were running about a minute after the fast boot up with their stats *and *it has an added column to show how much memory (RAM) the same process used during the "slow" boot up. It also has some statistics written (total memory and swap usage). The 30% was not the RAM usage after on minute, but after 30+ minutes. After one minute, the RAM usage was about 50%-60% (there is a note of this in the image itself also).

The exact same processes were running during the "slow" and "normal speed/fast" bootup. I did have the home folder open during the "fast to slow comparison," but it did not add another process because there was also a thunar process during the "slow" screenshot.

One strange thing I noticed was that during the "normal speed/fast" bootup, all but two of the processes were using *more *RAM than they used in the "slow" bootup.

If you have any further questions or any advice, let me know.

Thanks in advance.
     Isaac.

---

### Post by XubuRoxMySox on 2010-05-16
It looks like you have insufficient RAM for Xubuntu. Not that it needs much - my Xubuntu Lucid runs sweet and very fast on a mere 512 of RAM, but from the screenshots it looks as though you have less than half of that. Lots of swapping going on, which is why it's so slow.

Adding some RAM I think is the best way to go, but if that isn't possible, try a distro like Puppy Linux. _L_ubuntu might perform better on your hardware than Xubuntu (I found it far too buggy on mine and I like Xfce *much* better). It's definitely less resource hungry and you may have better luck with it than I have.

Hoping this helps a little,
Robin

---

### Post by isaacd on 2010-05-16
I thought this at first too, but I am reluctant to go this way because there are times when it runs just fine (even though it uses a little swap). I think that something is eating up RAM on that first slow boot that is not there on the second fast boot. If it were slow every time, then I might get more ram, but it is not.

Xubuntu is supposed to be able to run with 192 or even 128 megabytes of ram, though they "strongly recomend" 256. I have 213.2.

So what I am looking to do is find out what is eating up ram on the "slow" boots but not the fast ones. Whatever is eating up ram is not shown in the system monitor. Here are some possibilities:

[LIST]
[*]a process not shown in the system monitor (perhaps executed by root)
[*]I kind of wonder if the computer is just not recognizing all the ram (I doubt this in favor of the first option)
[/LIST]
So the question is: what kind of process does root run that only runs after you boot the computer up for the first time that day, and not when you boot it up a second or third (4th 5th etc.) time thereafter?

Thanks.
Isaac.

---

### Post by isaacd on 2010-05-16
_**Update**_

Today (Sunday morning, 5-16-2010) I booted it up for the first time that day, and it booted up fast. I don't know why it didn't boot up slow first (although if this keeps up, I'll be glad).

---

### Post by isaacd on 2010-05-16
[U][B]Update
[/B][/U]On the second boot up on Sunday morning 5-16-10, the computer booted up slowly. The third boot up was fast. So the order was: 1 - fast 2 - slow 3 - fast. I think that it does not have anything to do with the first boot up of the day.

So I opened system monitor as root (sudo gnome-system-monitor) and I did notice a *large* difference in the processes that root was  running during the slow and fast boot up. The slow and fast screenshots of the system monitor are attached. Again, there are more processes running on the fast boot up than slow boot up. One possible explination for this is that the slow screenshot was taken perhaps 3-4 minutes after booting up (because it takes a long time to get system monitor open) wheras the faste screenshot was taken about 1 minute after booting up (because things work faster).

One thing I noticed when I opend system monitor from the teminal as root on both slow and fast boots is that it said:

**(gnome-system-monitor:1604): WARNING **: SELinux was found but is not enabled

I don't know if this means anything.

Thanks.
Isaac.

PS: to clarify, even though I say slow and fast boot up, it really has to do with how the computer runs *after* having booted up, as well as during the boot process.

---

### Post by XubuRoxMySox on 2010-05-16
Maybe some daemons (not Ferengi ship captains, not evil spirits... little "sentinel" programs that run in the background to monitor other processes. They're called "daemons") like a printer daemon, or an antivirus daemon (if you've installed ClamAv or something), stuff like that. Perhaps if some daemons are showing up in your list that you don't use or need, you can get rid of them (bluetooth maybe, or a printer daemon on a computer that isn't connected to a printer, etc.).

I have no scientific basis for this, but I get the feeling that my Xubuntu "learns" from each session and improves a little over time. Maybe it's just updates, but perhaps yours will get better over a few days' time too. 

Let us know,
Robin

---

### Post by isaacd on 2010-05-16
I've tried turning booting it up many times today, and the only time it was slow was on the second time today (once out of about ten times). That slow bootup is the same one that I refferenced in comment 5. So who knows, maybe it solved the problem on its own, but I am not going to mark this solved yet, as I would like to try it 24+ hours from now and see what happens.

Isaac.

P.S. I do not have access to this computer after today untill this coming thursday the 20th, so you probably won't hear back from me untill then, or later.

---

### Post by michy99 on 2010-05-16
Sounds like you are having the same problem I had with ureadahead. On the boot-ups where it is re-profiling, everything is slow as molasses. This only happens the next boot after some updates (not all of them.) I solved this by```
sudo apt-get remove ureadahead
``` and everything is good now. I am running standard Ubuntu (Gnome) on 256 meg, so memory is not your problem.

---

### Post by isaacd on 2010-05-19
I tried that in synaptic and it told me that it also would remove "ubuntu-minimal." I looked at the description in synaptic of ubuntu-minimal and this is what it said:

This package depends on all of the packages in the Ubuntu minimal system,
that is a functional command-line system with the following capabilities:

 - Boot
 - Detect hardware
 - Connect to a network
 - Install packages
 - Perform basic diagnostics

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

Is this something I need to worry about?

---

### Post by Praxicoide on 2010-05-19
It's just a metapackage. It isn't a program in itself but only serves to install a number of softwares with just one package.

So for example you have xubuntu-desktop, which is just a list of applications that are installed in a default xubuntu install.

If you remove one of the packages in the metapackage, this is uninstalled as well, but it just means that you don't have the "default" set of programs.

So don't worry about it.

---

### Post by isaacd on 2010-05-19
I removed ureadahead and then subsequently installed some updates. I then restarted the computer. Upon booting up, I saw something about not being able to read ahead (ureadahead) but then I booted it up and logged in and it worked fine. I susspect that this was one of the upgrades that would have used ureadahead, so I think that it worked.

Thanks!

Isaac.

---

