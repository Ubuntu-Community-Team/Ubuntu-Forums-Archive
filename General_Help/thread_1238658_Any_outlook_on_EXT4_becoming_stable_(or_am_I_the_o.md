---
title: "Any outlook on EXT4 becoming stable (or am I the only one with problems) ?"
date: 2009-08-12
forum: General Help
---

### Post by RavanH on 2009-08-12
[COLOR="Red"]EDIT: Since this thread evolved, the problem turned out to be specific to the Asus M2400N laptop Intel integrated graphics and ACPI and unrelated to EXT4. Turn to the latter pages of this thread for more...[/COLOR]

Hi all,

After my bad experiences with EXT4 on two machines (one 32bit and one 64bit) I am regretting the fact that I did not stick with EXT3 very much.

Ubuntu has now become even more unstable than I was used to under Windoze. Sure it is still much faster (with ext4 even bootu up is now comfortable) but the sudden freezes I am experiencing remind me of my MS days in a nightmarish manner :evil:

So my question are these:

Are these sudden system freezes a known issue in EXT4 or is there something else going wrong on my two machines? 

If the former, should I stick with this unstable setup and hang on a little longer while stable ext4 is just around the bend or am I better of moving back to EXT3 ? 

If the latter, can anyone advise me how to go about this. Should I do a backup and make a fresh install or is there a shorter route?

Thanks for any advice,
Allard

---

### Post by alastair on 2009-08-12
Not sure. I think and expect the problems you have are elsewhere - and not an ext4 issue. The reason I say this is that ext4 is pretty active just now and a lot of people are watching it (and installing it). Unless trouble is surfacing on other lists (linux filesystems, kernel etc.), ext4 is probably OK. I haven't checked though.

So ... sudden freezes etc. ... need more information.

- Any pattern?
- Any logs? (/var/log/syslog etc.)
- What happens etc.?

---

### Post by RavanH on 2009-08-13
> **alastair said:**
> Not sure. I think and expect the problems you have are elsewhere - and not an ext4 issue. The reason I say this is that ext4 is pretty active just now and a lot of people are watching it (and installing it). Unless trouble is surfacing on other lists (linux filesystems, kernel etc.), ext4 is probably OK. I haven't checked though.

So ... sudden freezes etc. ... need more information.

- Any pattern?
- Any logs? (/var/log/syslog etc.)
- What happens etc.?

Thanks, alastair, for your thoughts...

No patterns. No way of invoking a freeze at all. Sometimes it happens on disk-intensive operations (like an update, with incomplete packages as a result) other times just when scrolling down a webpage or document... 

I will take a look at the logs after the first following freeze. Can I come back to you with that?

It happens on both my 32bit system and my 64bit laptop and it started after migrating them both to Ext4. After that, I reïnstalled Jaunty on both machines (recreating / partitions as EXT3 on one and EXT4 on the other and leaving /home partition as EXT4 on both) but with the same result.

I would be very happy to find out what is causing this because returning to WinXP is not what I want to do... Going back to Ubuntu 8.10 is an option but then I will have to get all my /home data copied to a Ext3 partition and I have no idea how to go about that.

---

### Post by oldos2er on 2009-08-13
Which kernel are you running? I experienced 3 or 4 random hard freezes after first installing 9.04, but with the newer kernels 2.6.28-13 and 2.6.28-14, those freezes no longer occur. Every partition on my system is using ext4, and has been for several months.

---

### Post by Arup on 2009-08-13
ext4 is now common in Fedora, sidux and other latest releases, I guess if it was that bad, none of these distros would take a big chance like this.

---

### Post by ronaldprettyman on 2009-08-13
> **Arup said:**
> ext4 is now common in Fedora, sidux and other latest releases, I guess if it was that bad, none of these distros would take a big chance like this.

Fedora is a testing distrubtion to show case future technology for RedHat Linux. Fedora is by now means to be considered by any stretch of the word. Stable.

ext4 is still fairly new. What could you possibly require from ext4 that isn't in ext3?

> **RavanH said:**
> Hi all,

After my bad experiences with EXT4 on two machines (one 32bit and one 64bit) I am regretting the fact that I did not stick with EXT3 very much.

Ubuntu has now become even more unstable than I was used to under Windoze. Sure it is still much faster (with ext4 even bootu up is now comfortable) but the sudden freezes I am experiencing remind me of my MS days in a nightmarish manner :evil:

So my question are these:

Are these sudden system freezes a known issue in EXT4 or is there something else going wrong on my two machines? 

If the former, should I stick with this unstable setup and hang on a little longer while stable ext4 is just around the bend or am I better of moving back to EXT3 ? 

If the latter, can anyone advise me how to go about this. Should I do a backup and make a fresh install or is there a shorter route?

Thanks for any advice,
Allard

Its quite possible something specific to your system is causing this bug. Submit a bug report to the ext4 team for investigation.



KISS, if you don't know what your doing, don't experiment with new technology on your main pc. Pick up a second one. I mean really, you can pick up a dell for 25 bucks on craigslist. hardware recyclers are also a good source for dirt cheap system for experimenting on.

Don't complicate matters beyond what is required. At least on your main pc's ;-).

---

### Post by RavanH on 2009-08-13
> **oldos2er said:**
> Which kernel are you running? I experienced 3 or 4 random hard freezes after first installing 9.04, but with the newer kernels 2.6.28-13 and 2.6.28-14, those freezes no longer occur. Every partition on my system is using ext4, and has been for several months.

I am using the latest from Ubuntu repo: 2.6.28-14

This problem was around during -11 -13 and still is with -14...

---

### Post by RavanH on 2009-08-13
Just now had three hard freezes. One around 19:15:30, one around 19:20:50 and one around 19:43:00.

Syslog reports:

```
...Aug 13 19:12:50 asus avahi-daemon[2715]: Registering new address record for 192.168.1.20 on eth1.IPv4.
Aug 13 19:12:50 asus dhclient: bound to 192.168.1.20 -- renewal in 35238 seconds.
Aug 13 19:12:53 asus kernel: [  347.540245] eth1: no IPv6 routers present
Aug 13 19:15:43 asus syslogd 1.5.0#5ubuntu3: restart.
Aug 13 19:15:43 asus kernel: Inspecting /boot/System.map-2.6.28-14-generic
Aug 13 19:15:43 asus kernel: Cannot find map file.
Aug 13 19:15:44 asus kernel: Loaded 55776 symbols from 56 modules.
Aug 13 19:15:44 asus kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
...
```

```
...Aug 13 19:17:01 asus /USR/SBIN/CRON[3494]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 13 19:20:02 asus /USR/SBIN/CRON[4107]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 13 19:21:22 asus syslogd 1.5.0#5ubuntu3: restart.
Aug 13 19:21:22 asus kernel: Inspecting /boot/System.map-2.6.28-14-generic
Aug 13 19:21:22 asus kernel: Cannot find map file.
Aug 13 19:21:22 asus kernel: Loaded 55776 symbols from 56 modules.
Aug 13 19:21:22 asus kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
...
```

```
...Aug 13 19:40:40 asus acpid: client 2711[0:0] has disconnected 
Aug 13 19:40:40 asus acpid: client connected from 4826[0:0] 
Aug 13 19:40:41 asus kernel: [ 1185.002023] [drm:i915_setparam] *ERROR* unknown parameter 4
Aug 13 19:40:41 asus kernel: [ 1185.002076] [drm:i915_getparam] *ERROR* Unknown parameter 6
Aug 13 19:40:42 asus kernel: [ 1185.966226] [drm:i915_getparam] *ERROR* Unknown parameter 6
Aug 13 19:43:26 asus syslogd 1.5.0#5ubuntu3: restart.
Aug 13 19:43:27 asus kernel: Inspecting /boot/System.map-2.6.28-14-generic
Aug 13 19:43:27 asus kernel: Cannot find map file.
Aug 13 19:43:27 asus kernel: Loaded 55776 symbols from 56 modules.
Aug 13 19:43:27 asus kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
...
```

Which says nothing to me. Should I paste the complete syslog or can other logs tell more? (short and to the point before the next freeze,sorry)

EDIT: (trying to edit this post for more info, i had another freeze) this is all from my 32bit system.

EDIT 2 (after another freeze, it has never been this bad) some lines in syslog that come back each boot draw my attention (but might be totally unrelated):
> ... asus kernel: [    0.660076] weird, boot CPU (#0) not listedby the BIOS.
> ... asus kernel: [    0.728865] HPET not enabled in BIOS. You might try hpet=force boot option
> ... asus kernel: [    3.912494] Marking TSC unstable due to TSC halts in idle
> ... asus kernel: [    7.328023] Clocksource tsc unstable (delta = -274749806 ns)

EDIT 3:and another wierd one:
> ... asus console-kit-daemon[2520]: WARNING: Couldn't read /proc/2519/environ: Failed to open file '/proc/2519/environ': No such file or directory

---

### Post by alastair on 2009-08-13
> **ronaldprettyman said:**
> Fedora is a testing distrubtion to show case future technology for RedHat Linux. Fedora is by now means to be considered by any stretch of the word. Stable.

Fedora can be a bit bumpy - but so can Ubuntu :-)

> **ronaldprettyman said:**
> ext4 is still fairly new. What could you possibly require from ext4 that isn't in ext3?

For me - fsck times are a draw. I'm not using it yet because I'm LTS and Debian Stable. But ext4 is faster for I/O and much faster when doing a volume check. This makes a big difference if you're checking a 5 or 10 TB filesystem!

---

### Post by RavanH on 2009-09-08
ok, so if it could not be ext4, then what? i have searched further but without any hints from any log files, i had to resort to the "just try anything" method... 

one thing i tried was turning of acpi by setting **acpi=off** as kernel boot option in my /boot/grub/menu.lst which seemed to stop the freezes but left me with somewhat crippled system operation. then i read somewhere that **apic** or **lapic** (which seems to be something meant for multiple CPU systems) can sometimes cause odd hangs on single CPU machines... so i replaced the acpi=off option with **noapic nolapic** and...

after three days of *normal* operation, i have not gotten any freezes :)

back in the days of feisty (or was it even before) i had to add these options to even be able to boot on my ASUS M2400N laptop at all. then one sunny dist-upgrade it appeared to be no more problem to leave apic/lapic on but now with jaunty apic/lapic need to be switched off again...  

now i wonder:
1. what the downside is of turning apic and lapic off on a single CPU system (if at all)
2. could apic and/or lapic indeed be the cause of these hangs
3. why would they be active on a single CPU system, if known to be problematic anyway?
4. is this jaunty specific (gutsy gave no problems) or can it somehow be related to migrating to ext4 after all, since i started to have these hangs only 

thanks!

---

### Post by P4man on 2009-09-08
> **RavanH said:**
> ok, so if it could not be ext4, then what? i have searched further but without any hints from any log files, i had to resort to the "just try anything" method... 

one thing i tried was turning of acpi by setting **acpi=off** as kernel boot option in my /boot/grub/menu.lst which seemed to stop the freezes but left me with somewhat crippled system operation. then i read somewhere that **apic** or **lapic** (which seems to be something meant for multiple CPU systems) can sometimes cause odd hangs on single CPU machines... so i replaced the acpi=off option with **noapic nolapic** and...

after three days of *normal* operation, i have not gotten any freezes :)

back in the days of feisty (or was it even before) i had to add these options to even be able to boot on my ASUS M2400N laptop at all. then one sunny dist-upgrade it appeared to be no more problem to leave apic/lapic on but now with jaunty apic/lapic need to be switched off again...  

now i wonder:
1. what the downside is of turning apic and lapic off on a single CPU system (if at all)
2. could apic and/or lapic indeed be the cause of these hangs
3. why would they be active on a single CPU system, if known to be problematic anyway?
4. is this jaunty specific (gutsy gave no problems) or can it somehow be related to migrating to ext4 after all, since i started to have these hangs only 

thanks!

I wish I had seen this thread earlier, my first guess would have been to play with those ACPI switches.

1. Nothing major. Under heavy I/O and cpu load, you would get slightly better performance with (l)apic if you have > 1 CPU. This might be true under server loads or perhaps with virtualization, but i doubt you'd ever notice it.

2. Yes, absolutely. 

3. Good question. I suppose because it is faster, and because on a properly implemented BIOS, it should work.

4. Its kernel specific, so I guess, yes, its related to jaunty indirectly. It has nothing to do with Ext4 though.

You might want to file a bug report, and give your hardware and bios details and state it needs noapic nolapic to work reliably. Then they can set that as default in the kernel for your bios.

---

### Post by RavanH on 2009-09-09
thanks p4man, for your elaborate answer (and yes, i wish you had seen this thread earlier too ;) )

about filing a bugreport: i will take a look into doing that but do not really know where to start. normally, apport does most of the work and i only have to find a good duplicate of what happened. in this case however, apport does not kick in and there is absolutely NOTHING to find in the syslog except the fact that a new boot is logged without a proper shutdown before it... as if the system was switched off by  just unplugging the AC power.

so if you have some pointers for me on where to start with bugreporting this, i'd be very grateful.

thanks again!

---

### Post by RavanH on 2009-09-16
Alas, the lock-ups are still occurring :(

With kernel boot options noapic nolapic the hangs seemed to be solved for a while but, no... They are back!

I have run a complete memory check cycle and disk checks reveal no problems. I am at a loss and about to chuck the laptop out the window (were it not too dangerous for pedestrians outside)...

The only thing that I noticed is that the lock-ups seem to occur mostly (not always) when I am scrolling a window or frame. For example when scrolling through a open document or when scrolling through a text frame (like the one this text is typed in) inside my browser window.

Also weird is the fact that the computer seems to be alive (mouse pointer still moves and sometimes there is disk activity) but accepts NO input like mouse-clicks or typing. The only keyboard input that still works is Alt+SysRq+B which results in the normal hard reboot.

And (to repeat myself) the problems started after installing Jaunty with ext4...

Anybody ANY other idea?

---

### Post by gbrethen on 2009-09-16
Could this have anything to do with the kernel not finding the system.map?  I seem to have that same error in my var/log/messeges file and I get freezes when trying to log out.

Any thoughts?

---

### Post by RavanH on 2009-09-16
> **gbrethen said:**
> Could this have anything to do with the kernel not finding the system.map?  I seem to have that same error in my var/log/messeges file and I get freezes when trying to log out.

Any thoughts?

I have that same message on another laptop but without any freezes so I would be surprised if it is related... but I do not know for sure.

---

### Post by RavanH on 2009-11-04
OK, old thread but still relevant :(

After a long wait for that magic update that would solve the problem, which never came, I decided to go for an upgrade by fresh install (but keeping my existing /home partition) with Karmic. I tried Ubuntu, Xubuntu and Kubuntu but all resulted in sooooo much lockups that I could hardly ever get past the GDM/KDM login. I have never even seen a fully loaded desktop!

Except... when I added **acpi=off** as a boot option in GRUB2... But without acpi, my laptop is no laptop anymore :( 

So that was enough. I finally decided to do that dreaded backup of my home partition and revert to Ubuntu 8.10. Now I have a stable system again with acpi support. No speed gains like sreadahead and ext4 :( but a stable desktop that just works is worth so much more!

Sadly, this seemed to have been the only solution for my Asus M2400N laptop. Unless someone out there has one final suggestion??

---

### Post by P4man on 2009-11-04
that acpi=off solves it is telling I guess, although disabling acpi changes a LOT of things.  Anyway have you updated your bios?

If you got the latest bios and noapic and nolapic dont do it, there are quite a few other kernel options you could try. Some of the more useful ones are listed here:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)
If you want even more to play with, eat your heart out here:
[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

(btw, when the issue returned, are you sure you didnt get a kernel upgrade which disabled the noapic and nolapic settings in grub?)

I would also be inclined to blame a videodriver/kernel issue (onboard intel?) especially in combination with desktop effects, but I dont see how disabling acpi would solve that, so I guess not.

---

### Post by P4man on 2009-11-04
Some googling reveals some more info:
acpi trouble as far back as 2005:
[http://ubuntuforums.org/showthread.php?t=83976](http://ubuntuforums.org/showthread.php?t=83976)
Then solved through bios update

Freezes on karmic (beta!) due to intel video (with workarounds):
[http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n)

Not sure if those still apply, but worth a try. Although that user also needed to disable acpi and set nolapic.. so,,

---

### Post by RavanH on 2009-11-05
> **P4man said:**
> Some googling reveals some more info:
acpi trouble as far back as 2005:
[http://ubuntuforums.org/showthread.php?t=83976](http://ubuntuforums.org/showthread.php?t=83976)
Then solved through bios update

Freezes on karmic (beta!) due to intel video (with workarounds):
[http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n)

Not sure if those still apply, but worth a try. Although that user also needed to disable acpi and set nolapic.. so,,

Wow! Thanks P4man, for thinking along and coming up with so many suggestions :) I think that article on [Ubuntu karmic freeze on Asus M2n]("http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n") describes exactly what was going on on my Asus M2400N: apparently not real freezes (I noticed some disk activity after freezes and the mouse pointer could still move around), just a display/keyboard input freeze... 

You gave me hope on getting Ubuntu 9.10 to work again and I'll surely be testing with this! Woooooot! 

(will be back with results)

---

### Post by P4man on 2009-11-05
> **RavanH said:**
> 

You gave me hope on getting Ubuntu 9.10 to work again and I'll surely be testing with this! Woooooot! 



before you get over-excited, he had to disable ACPI as well to make it boot.

---

### Post by RavanH on 2009-11-05
> **P4man said:**
> before you get over-excited, he had to disable ACPI as well to make it boot.

:D You're right, no guarantees on satisfaction given ;)

What i understand from quickly scanning through the article is that he installed with acpi=off and nolapic (and first boot) but finally only leaves nolapic as a boot switch. Turning acpi off permanently breaks sound (above lots of other things obviously), which i had noticed too...

---

### Post by sliketymo on 2009-11-05
> **RavanH said:**
> :D You're right, no guarantees on satisfaction given ;)

What i understand from quickly scanning through the article is that he installed with acpi=off and nolapic (and first boot) but finally only leaves nolapic as a boot switch. Turning acpi off permanently breaks sound (above lots of other things obviously), which i had noticed too...
 
Your problems may not necessarily be so quickly blamed on ext4.I have been using it for quite some time with no apparent problems.Other possibilities include your graphics,what applications your running when these events occur,the amount of RAM,and free space you have available,etc.

---

### Post by P4man on 2009-11-05
> **sliketymo said:**
> Your problems may not necessarily be so quickly blamed on ext4.I have been using it for quite some time with no apparent problems.Other possibilities include your graphics,what applications your running when these events occur,the amount of RAM,and free space you have available,etc.

I think by now its clear his problems stem primarily from bios/acpi incompatibility which he may or may not be able to work around. But yeah, perhaps changing the post title to reflect that would be a good idea.

---

### Post by RavanH on 2009-11-05
> **sliketymo said:**
> Your problems may not necessarily be so quickly blamed on ext4.I have been using it for quite some time with no apparent problems.Other possibilities include your graphics,what applications your running when these events occur,the amount of RAM,and free space you have available,etc.

you are right, sliketymo. i first assumed it had something to do with ext4 (hence the title of this thread, can i change that?) since the problems started after i upgraded to 9.04 and migrated from ext3 to ext4. but since then i found that when reïnstalling 9.04 (and 9.10) with only ext3 partitions results in the same problems. it must be something specific to this laptop as is also suggested by [http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n)

---

### Post by RavanH on 2009-11-05
> **P4man said:**
> I think by now its clear his problems stem primarily from bios/acpi incompatibility which he may or may not be able to work around. But yeah, perhaps changing the post title to reflect that would be a good idea.

done!

EDIT: have I? i changed the title of my first post but that does not seem to have changed the title of the thread... how can that be done?

---

### Post by chewit on 2009-11-05
I had freezes in 9.04 due to Ext4, kernel updates did improve the suituation in 9.04.

I can now say that there is no freezes in 9.10 due to ext4, yet....

---

### Post by RavanH on 2009-11-05
> **chewit said:**
> I had freezes in 9.04 due to Ext4, kernel updates did improve the suituation in 9.04.

I can now say that there is no freezes in 9.10 due to ext4, yet....

I have had those freezes on another laptop too and in the beginning confused them with the freezes on the Asus M2400N laptop. The only difference was that the freezes related to EXT4 (? which disappeared after that kernel update) were complete system freezes. With the Asus M2400N freeze, I could still move the mouse pointer and there was always still some disk activity visible/audible but mouse clicks (or keyboard input?) was no longer accepted.

---

### Post by P4man on 2009-11-05
> **RavanH said:**
>  I could still move the mouse pointer and there was always still some disk activity visible/audible but mouse clicks (or keyboard input?) was no longer accepted.

That happens when X freezes. First of all, if that ever happens do a clean shut down or reboot using reisub:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

As for troubleshooting X freezes have a look here:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by RavanH on 2009-11-05
UPDATE:

Thanks to P4man finding me the link and thanks to Cyril writing a workaround on [http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n) I can now log into Karmic and see a full working Desktop. No more freezes so far! :)

The workaround comprises of three parts:
1. installation and first time login with acpi=off
2. setting boot switches nolapic nomodeset in GRUB2 (different for legacy GRUB)
3. forcing the system to use the vesa driver

This seems to have done the trick. This only means there are no Desktop Effects in Gnome anymore but since I prefer XFCE (where transparency can be enabled just fine) on this older laptop, that is not a problem :)

Anyone looking for the same fix: Read the full post on [http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n](http://blog.cyril-ravat.fr/post/2009/10/25/Ubuntu-karmic-freeze-on-Asus-M2n) and leave a comment there if it works for you too!

---

### Post by myii on 2009-11-05
I know you've marked this thread as solved but maybe my experiences could be useful:

[LIST=1]
[*]Have been using Ubuntu since 5.10.  The experience had continually improved with each release.  8.10 was the high point.
[*]Then I upgraded to Jaunty ... oh dear.  Freezes galore.  Similar to many other users (just check out Launchpad): screen freezes where only the mouse pointer is still active (clock stops, system monitor freezes, etc.)  Attempting to kill X gets nowhere but REISUB works fine.  Can also ssh to the frozen computer but not very much else.
[*]From spending countless hours scouring the net, found various workarounds/solutions.  Have Ubuntu installed on 2 PCs + my main laptop, all with Intel graphics.  Finally found configurations that worked for both desktops but I've endured many frustrating freezes with my laptop.  I understand how one feels like chucking one's laptop out of the window, as was mentioned earlier in this thread.
[*]OK.  Main point I'd like to make is that asides from fudging around with xorg.conf (great in Jaunty, not quite clear how to do it in Karmic), **the best results I've got is from finding the best combination of kernel + intel video drivers**.
[*]Never found the optimal configuration for my laptop with Jaunty, so jumped at the opportunity to install Karmic - ho ho ho!  Just like many others, froze at the login screen... second boot, froze while logging in.  Felt the blood flooding to my head and almost let my laptop have it.
[*]More searching on the net and found that some had achieved stability by using the 2.6.31-12 kernel (Note: Karmic shipped with 2.6.31-14!)  However, I've found stability with the former but freezes with the latter!
[*]... Stability meaning no more freezes over the last week (but still some strange behaviour being exhibited).  3D acceleration doesn't work but otherwise OK.
[*]By the way, I've had dual-boot (WinXP) setup on my laptop since the beginning.  No (graphical) problems in WinXP all this time, thus ruling out problems with my hardware.
[/LIST]

If anyone is interested in more details, I've tried to keep track of what has and hasn't worked over time.

Now **what I'd like to know** is the best way to get in touch with *those* that can actually do something about this.  Having followed Launchpad, it seems that you'd have to wait a month or two for any sort of resolution.  Apologies if I sound a bit grumpy but it does begin to get you down when such a major problem persists for over half a year ...

---

### Post by phillw on 2009-11-05
> **myii said:**
> I know you've marked this thread as solved but maybe my experiences could be useful:

[LIST=1]
[*]Have been using Ubuntu since 5.10.  The experience had continually improved with each release.  8.10 was the high point.
[*]Then I upgraded to Jaunty ... oh dear.  Freezes galore.  Similar to many other users (just check out Launchpad): screen freezes where only the mouse pointer is still active (clock stops, system monitor freezes, etc.)  Attempting to kill X gets nowhere but REISUB works fine.  Can also ssh to the frozen computer but not very much else.
[*]From spending countless hours scouring the net, found various workarounds/solutions.  Have Ubuntu installed on 2 PCs + my main laptop, all with Intel graphics.  Finally found configurations that worked for both desktops but I've endured many frustrating freezes with my laptop.  I understand how one feels like chucking one's laptop out of the window, as was mentioned earlier in this thread.
[*]OK.  Main point I'd like to make is that asides from fudging around with xorg.conf (great in Jaunty, not quite clear how to do it in Karmic), **the best results I've got is from finding the best combination of kernel + intel video drivers**.
[*]Never found the optimal configuration for my laptop with Jaunty, so jumped at the opportunity to install Karmic - ho ho ho!  Just like many others, froze at the login screen... second boot, froze while logging in.  Felt the blood flooding to my head and almost let my laptop have it.
[*]More searching on the net and found that some had achieved stability by using the 2.6.31-12 kernel (Note: Karmic shipped with 2.6.31-14!)  However, I've found stability with the former but freezes with the latter!
[*]... Stability meaning no more freezes over the last week (but still some strange behaviour being exhibited).  3D acceleration doesn't work but otherwise OK.
[*]By the way, I've had dual-boot (WinXP) setup on my laptop since the beginning.  No (graphical) problems in WinXP all this time, thus ruling out problems with my hardware.
[/LIST]

If anyone is interested in more details, I've tried to keep track of what has and hasn't worked over time.

Now **what I'd like to know** is the best way to get in touch with *those* that can actually do something about this.  Having followed Launchpad, it seems that you'd have to wait a month or two for any sort of resolution.  Apologies if I sound a bit grumpy but it does begin to get you down when such a major problem persists for over half a year ...


I think you should try the solution in this thread - variant of it should get you up & running 

Phill.

---

### Post by myii on 2009-11-06
> **phillw said:**
> I think you should try the solution in this thread - variant of it should get you up & running 

Phill.
I'm already up and running... just using a different way to do it than mentioned in this thread.  It's my fault that I wrote such a long essay above!  In point 6, I mentioned that freezing has been absent since simply installing kernel 2.6.31-12.  Maybe this would be helpful for others, rather than having to do all of the other steps mentioned above.

Since my last post, I've also tried kernels 2.6.31-13 and the latest release candidate (2.6.32-020632rc6).  With the former, I get the same freezes as with 2.6.31-14 (Karmic default).  With the latter, the system crashes with a blank screen a few seconds after booting up!

Thanks anyway.

---

### Post by RavanH on 2009-11-06
> **myii said:**
> I know you've marked this thread as solved but maybe my experiences could be useful:

[LIST=1]
[*]Have been using Ubuntu since 5.10.  The experience had continually improved with each release.  8.10 was the high point.
[*]Then I upgraded to Jaunty ... oh dear.  Freezes galore.  Similar to many other users (just check out Launchpad): screen freezes where only the mouse pointer is still active (clock stops, system monitor freezes, etc.)  Attempting to kill X gets nowhere but REISUB works fine.  Can also ssh to the frozen computer but not very much else.
[*]From spending countless hours scouring the net, found various workarounds/solutions.  Have Ubuntu installed on 2 PCs + my main laptop, all with Intel graphics.  Finally found configurations that worked for both desktops but I've endured many frustrating freezes with my laptop.  I understand how one feels like chucking one's laptop out of the window, as was mentioned earlier in this thread.
[*]OK.  Main point I'd like to make is that asides from fudging around with xorg.conf (great in Jaunty, not quite clear how to do it in Karmic), **the best results I've got is from finding the best combination of kernel + intel video drivers**.
[*]Never found the optimal configuration for my laptop with Jaunty, so jumped at the opportunity to install Karmic - ho ho ho!  Just like many others, froze at the login screen... second boot, froze while logging in.  Felt the blood flooding to my head and almost let my laptop have it.
[*]More searching on the net and found that some had achieved stability by using the 2.6.31-12 kernel (Note: Karmic shipped with 2.6.31-14!)  However, I've found stability with the former but freezes with the latter!
[*]... Stability meaning no more freezes over the last week (but still some strange behaviour being exhibited).  3D acceleration doesn't work but otherwise OK.
[*]By the way, I've had dual-boot (WinXP) setup on my laptop since the beginning.  No (graphical) problems in WinXP all this time, thus ruling out problems with my hardware.
[/LIST]

If anyone is interested in more details, I've tried to keep track of what has and hasn't worked over time.

Now **what I'd like to know** is the best way to get in touch with *those* that can actually do something about this.  Having followed Launchpad, it seems that you'd have to wait a month or two for any sort of resolution.  Apologies if I sound a bit grumpy but it does begin to get you down when such a major problem persists for over half a year ...

myii, although i do not want to make this a 'complain thread', i full-heartedly agree with you here. it is just too frustrating that this problem doesn't get nailed. 

so your solution was to get an older kernel with the regular intel drivers that does not seem to be affected by this problem while Cyril's solution was to use the latest kernel with vesa driver. both solutions seem to work while both lacking 3D... interesting.

i wonder if the problem could be narrowed down to either the acceleration method, dri or opengl like is suggested on [https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Narrow%20Subsystem%20it%20Occurs%20in](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Narrow%20Subsystem%20it%20Occurs%20in) . have you tested with these switches already? apparently, xorg.conf (if created) still works in karmic...

---

### Post by P4man on 2009-11-06
> **myii said:**
> 
Now **what I'd like to know** is the best way to get in touch with *those* that can actually do something about this.  Having followed Launchpad, it seems that you'd have to wait a month or two for any sort of resolution.  A

The best way is launchpad. File bugs, but do it properly, using methods described here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

As for the 2 month waiting, I guess thats to be expected. You can perhaps avoid it by participating in alpha and beta tests and submitting your bugs and testing patches before the release. There is a much better chance of solutions being offered while ubuntu is still in alpha/beta than after release.

Not that this guarantees anything, having submitted bugs for karmic alpha (no boot on nvidia with 2 monitors connected using nv drivers) that still havent even been triaged and are still very much in the current version, but at least its worth trying... 

id say make a partition and start testing 10.04 and perhaps that will be the perfect release for you :)

---

### Post by myii on 2009-11-10
Appreciate your responses.  Sorry for the delay, had to change service providers for my mobile broadband.

> **RavanH said:**
> i wonder if the problem could be narrowed down to either the acceleration method, dri or opengl like is suggested on [https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Narrow%20Subsystem%20it%20Occurs%20in](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Narrow%20Subsystem%20it%20Occurs%20in) . have you tested with these switches already? apparently, xorg.conf (if created) still works in karmic...

Had already tried playing about with xorg.conf before my first post.  Seemed unresponsive to settings I had used prior to 9.10.  Didn't get around to trying those switches ...

> **P4man said:**
> As for the 2 month waiting, I guess thats to be expected. You can perhaps avoid it by participating in alpha and beta tests and submitting your bugs and testing patches before the release. There is a much better chance of solutions being offered while ubuntu is still in alpha/beta than after release.

Interesting proposal, hadn't really thought about that.

> **P4man said:**
> Not that this guarantees anything, having submitted bugs for karmic alpha (no boot on nvidia with 2 monitors connected using nv drivers) that still havent even been triaged and are still very much in the current version, but at least its worth trying...

That's surely the ideal way but perhaps not on one's main laptop...

> **P4man said:**
> id say make a partition and start testing 10.04 and perhaps that will be the perfect release for you :)

Overall, that's good advice.  Especially since 10.04's an LTS.

Perhaps this isn't the right thread to mention this but it's pretty funny how my overall experience with Ubuntu has been.  At the beginning, I was inviting all and sundry to use it.  But being the main computer teacher at my school, I began to realise that I would become the main reference point for solving Linux problems.  Not easy dealing with 100+ students when you can't even solve some of your own issues!

Once my laptop started freezing up with Jaunty, I pretty much hid my Ubuntu use from my students, in order not to give them a bad impression.  Good thing the summer holidays came along pretty soon after!  Once school started, I was holding out for 9.10.  I was manually refreshing the download page all day... and then, the disappointment when the freezing had become worse!

I'd kept a CloneZilla image of Intrepid just before I installed Jaunty.  For now, I've had to take a step back.  It's nice to have everything working again.

I know why I use Linux and so I understand that you've got to go through situations like this sometimes.  I come from a technical background and I'm pretty good at researching solutions by myself.

I just feel a little ashamed that after my experiences, I can't find it in myself to encourage others to join our community.  Kinda feel a bit hypocritical!

I can't quite put my finger on it, but after I had used Windows for 4 years, I was pretty much a power user.  Yet after 4 years of Ubuntu, I still feel like a noob sometimes!  Perhaps it's because it is moving so rapidly ...

Hey guys, sorry for going on like this!  I've lived in silence for all of these years (just notice my bean count).  I guess this was the first major problem that really had me stumped.

I hope y'all fare better than I did!  BTW, have compiz running again is fan-tas-tic!

---

### Post by RavanH on 2009-11-11
> **myii said:**
> Had already tried playing about with xorg.conf before my first post.  Seemed unresponsive to settings I had used prior to 9.10.  Didn't get around to trying those switches ...

I have tried anything I can think of in xorg.conf without any succes apart from freezes occurring only after login instead of even before. The only thing that I have not tried is compiling the official intel driver from [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=865&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=865&lang=eng) to see if that is any different from the Ubuntu one (but I suppose not)...

So for me too, it is either going back to 8.10 or sticking to the vesa driver in 9.10. Another suggestion to use 9.10 but reverting the kernel and related drivers seems impractical to me. Afraid of loosing ext4 support with that.

I share your disappointment. I have one machine with ATI and one with Intel graphics. ATI has been a huge problem in the beginning but became perfect after a few years with the fglrx driver. But since Intrepid or Hardy (can't remember) I had to go back to the slow open source driver because AMD decided not to support my (widely used) Radeon Xpress 200M anymore. All that time, the intel graphics on the other machine had been doing fine but not anymore... Now I have two machines running under par ;(

However, I can recommend Xubuntu 9.10 with the vesa driver. With XFCE, you get at least transparency and shading (but no other fancy desktop effects) and it is stable with the **nolapic nomodeset** boot options. Other benefit is overall low memory footprint and higher responsiveness of your laptop. Especially with Ext4 and sreadahead. Maybe you will be inclined to recommend it to your students again ;)

---

### Post by Primefalcon on 2009-11-11
I'm still using ext3 myself for several reasons one is compatibility and when I did try ext4 I had a bad experience so went back to ext3 which eliminated my issues....

For now I'm going to hold off on ext4 until 10.10 comes out which will be the next LTS version, it should give the bugs that are existent in ext4 to be quashed.

apparently its stable in karmic (I'm using karmic but still using ext3, I'll wait), but in 9.04 and earlier well it just can't handle it

---

