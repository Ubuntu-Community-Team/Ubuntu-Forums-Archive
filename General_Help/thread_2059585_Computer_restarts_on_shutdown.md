---
title: "Computer restarts on shutdown"
date: 2012-09-18
forum: General Help
---

### Post by MorrisseyJ on 2012-09-18
Hi,

I have a problem with my computer occasionally restarting on shutdown.

Sometimes when i shutdown it reboots. At the login screen, i can shutdown and it seems to always shut down properly from there.

I have read elsewhere that this might be a power setting in the BIOS, but i think not as i) it doesn't happen in windows (which i dual boot) and ii) it only happens some of the time and never if i shutdown straight from the login screen.

Its not a world-ending problem, but its a bit of a hassle if i am in a rush to go somewhere and want to shut my machine down and it decides to restart. 

This is all trying with shutdown from the cog in the top right of the panel.

I am running 12.04 (64bit) on a thinkpad x131e.

Any help would be appreciated.

---

### Post by dino99 on 2012-09-18
kind of trouble not easy to narrow down :(
maybe you can find something usefull logged either into xsession-errors or /var/log/

you can also remove "quiet splash" from /etc/default/grub then run : sudo update-grub. That way you will be able to see the shutdown comments.

---

### Post by MorrisseyJ on 2012-09-18
Hi Dino99, 

Thanks for getting back to me. 

Do you have any idea what sort of thing i might be looking for?

I should be able to shut down and if the machine restarts, check the time. I should then be able to scan the logs for activity at this time, no?

---

### Post by MorrisseyJ on 2012-10-03
Problem persists. 

Can anyone tell me how i look in the log files and what i might be looking out for?

Thanks,

---

### Post by Shellbak3 on 2012-10-04
I'm having the same problem on a clean 11.10 install.  

I had previously upgraded a 11.04 to 11.10, created a couple of users, a new group etc. and noticed some problems.  There was no icon to click to shutdown and then I couldn't change the screen settings for the users and shutdown didn't work from an alternate way from the GUI nor from terminal: it rebooted.  Shortly there after I could only boot to console with some repeated attempts at boot.    

I installed a clean version of 11.10 Tuesday, created a couple of users, etc. and today I'm in a reboot cycle when I attempt to shutdown.  

I really can't see attempting to set up this machine until the problem is fixed.  My machine is a PC104 32 bit.  I have another that was upgraded from 10.04 to 11.04 to 11.10 with no signs of trouble - yet.

---

### Post by apochry on 2012-10-04
You can shut is down with ```
sudo poweroff
```Not that it's a solution, but I would do that and wait for 12.10 in two weeks, since the issue is kind of nasty.

Regards,
 - Christo

---

### Post by MorrisseyJ on 2012-10-05
In syslog i found the following errors and warnings:

Errors:

> watchdog: error registering /dev/watchdog (err=-16). - This appears to be related to me, for some reason, having two watchdogs which operate on waking from suspend. Its easy to blacklist one of them. To me this seems like the most relevant  error to my reboot/restart problem.

> EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro- This is some kind of read-write error, the webpages about which i don't understand.

> <error> [1349387438.2745] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent
 MAC address (error 0)
 - This, it seems, has to do with my broadcom wirless chip, but i don't really know much more than that.

Warnings:

> dnsmasq[26261]: warning: no upstream servers configured- I am not sure what this is, it might have to do with my VPN

As i said, it looks like the watchdog error might be the one, but i don't know enough  about this stuff to have a sense. If anyone has any advice i'd appreciate it.

---

### Post by MorrisseyJ on 2012-10-07
Using: > sudo poweroff seems to shut things down properly. 

Does this mean that there might be a bug in the shutdown process via the cog? If so, how can i diagnose?

j

---

### Post by MorrisseyJ on 2012-10-11
Nope>  sudo poweroff doesn't seem to work, as it too sometimes results in a restart. 

Thoughts?

---

### Post by MorrisseyJ on 2012-10-29
Bump: Problem persists under 12.10.

---

### Post by xCAFEBABE on 2013-01-09
Facing same problem with 12.04 as you. You mention the VPN and I believe is something related with this (same scenario for me). I'll try to dig into it now.

---

### Post by MorrisseyJ on 2013-01-09
Great. 

Let me know how you get on or if there is any info that i can give you to help with diagnosis. 

I have recently tried turning off quiet splash in GRUB, in the hope that i would see any errors occurring there. While i don't know how to interpret a lot of that info i've not been able to see any recurring errors in there.

---

### Post by Selmi on 2013-02-10
same problem. i tried shutdown -h, shutdown -P and poweroff, its always the same

maybe its somehow related to intel chipset, i didn't had any problems on my old computer which used nvidia chipset and amd processor. when i installed ubuntu 12.10 64bit on new computer which is intel based then it started to behave like this...

---

### Post by MorrisseyJ on 2013-02-11
I also noticed one or two occasions when the machine decided to restart when shut down from the login screen - after restarting from a previous shutdown. 

If that starts to persist it could get rather irritating. 

I'd love to know how to find out what might be causing this.

---

### Post by balasupv on 2013-02-27
Same problem with Ubuntu 12.10 fresh install on Thinkpad T430u. I seem to remember that I was able to shutdown before installing powertop package and implementing suggestions of powertop by changing /etc/rc.local...but I may be imagining things!

---

### Post by MorrisseyJ on 2013-10-25
Problem persists under 13.04 and, now, 13.10.

During shutdown i get the following messages broadcast on my screen:
> 
Broadcast message from root@james-Thinkpad-x131e
(unknown at 22:11)

The system is going down for power off NOW!
acpid:exiting
Applying powersave settings...done.
Speech dispatcher disabled: edit /etc/default/speech-dispatcher

I see that a similar problem was solved here: [http://ubuntuforums.org/showthread.php?t=1631836](http://ubuntuforums.org/showthread.php?t=1631836), but that had to do with the wireless card. I was having problems with my wireless card (Broadcom BCM43228), causing random system freezes. I eventually solved this problem by installing a Intel Centrino card (some details here [http://ubuntuforums.org/showthread.php?t=2166195](http://ubuntuforums.org/showthread.php?t=2166195)). Notably the restart on shutdown issue has persisted across cards.

I thus think that this is not a wireless problem but something which, like the solution above, could be solved by similarly blacklisting some process that is broadcasting to the machine to make it reboot. 

The reboot on shutdown issue seems more likely to occur when i have, at some point during the use of my computer, put it to suspend by closing the lid (although this could be a specious relationship).

My BIOS are up to date. 

Any thoughts?

Thanks in advance. 

j

---

### Post by Selmi on 2013-10-25
my problem was solved in 13.10 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1121489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1121489))
it was caused by module alx which i had to use otherwise i had no networking
when i did 'sudo rmmod alx' before shutdown then shutdown workedas expected. if i didn't computer switched off and after few seconds switched on again

---

### Post by MorrisseyJ on 2013-10-25
Hi Selmi, 

Thanks for looking at this, but it seems that you had the alx issue fixed in the latest Saucy release. I am running Saucy and so can't work out why this would persist. 

j

---

### Post by MorrisseyJ on 2013-11-01
> sudo rmmod alx

gives:

> Error: Module alx is not currently loaded

So it can't be that. Anyone have any other ideas?

j

---

### Post by MorrisseyJ on 2014-04-03
My problem is well described here: [http://ubuntuforums.org/showthread.php?t=2175057](http://ubuntuforums.org/showthread.php?t=2175057)

The restart only happens if i have previsouly put the machine to suspend. Without that, there is no issue.

If anyone has any thoughts, i'd appreciate them.

---

### Post by rbmorse on 2014-04-03
This is just a long shot, but do you have any root-level cron jobs scheduled?

---

### Post by MorrisseyJ on 2014-04-07
Thanks for getting back to me. 

I am not sure. What sort of jobs might those be?

I am pretty sure this behaviour happens on a vanilla install - i can check when i upgrade to Trusty, next week.

---

### Post by MorrisseyJ on 2014-04-22
Problem is solved under 14.04!

Not sure what did it, but i am glad to have it working.

Thanks whoever fixed this.

j

---

### Post by MorrisseyJ on 2014-07-17
An update a while back broke this. 

Anyone have any idea how i work out what happened?

---

### Post by MorrisseyJ on 2014-07-22
hmm, seems that another recent update fixed this again. 

It would be great if someone could help me identify what is breaking and fixing this process so that i could flag it in a bug report.

---

### Post by MorrisseyJ on 2014-07-22
@redalert: what is your hardware setup?

I am running an Lenovo x131e with intel processor.  Perhaps if we can find the common components we can identify the problem.

---

### Post by MorrisseyJ on 2015-02-01
Problem persists in 14.10.

j

---

### Post by javi13 on 2015-12-02
Hi, I&#7743; having the same problem. Whenever i try to shutdown, it just reboot instead. Even with sudo poweroff it reboots. Any idea? Thanks!

---

### Post by MorrisseyJ on 2015-12-02
Hi javi13,

Unfortunately I don't think i can help you. In the end i managed to diagnose this problem, as i describe in this thread: The problem was that if i suspended the machine at some point since the last boot, then it would restart on shutdown. After it had rebooted, so long as i did not suspend, i could shutdown. 

This all became moot when updates solved the problem. It was a few releases back that a fresh install started to fix things. Then an update to the system would break them again. Eventually, the update that was breaking things never arrived, and i have a fully functioning system.

I am sorry not to be of more help. 

j

---

### Post by oldos2er on 2015-12-03
Old thread closed.

Anyone still having problems should start a new thread.

---

