---
title: "Automatically wake up computer from completely off or suspend mode."
date: 2012-03-13
forum: General Help
---

### Post by Roasted on 2012-03-13
Is such a thing possible? I'm curious about setting up a file server that kicks on for an entire day once a week, so that way it's available and online for the users of the household to back up to it using automated backup software also set up to run that same day. From an energy saving standpoint if I can shave 6 days off of the week, it's be a nice bonus since the backup isn't a high demand one that needs to be on 247.

Is this possible? Or is this screaming the need for advanced BIOS features to handle this task? I'm just not sure this system is that advanced to have anything crazy with it. It's a basic Pentium Dual Core system from a few years ago...

---

### Post by miklcct on 2012-03-13
I think you need to use BIOS to handle this.

(or maybe you get a mechanical-based device installed on the power button of your computer)

---

### Post by Roasted on 2012-03-13
I've come across some computers in the past that turn on once they're plugged in to power, kind of negating the need for a power button. Is this a BIOS setting to turn on once power is sensed? I thought about getting some sort of Christmas light timer type thing to kick it on, as long as the computer has the ability to turn on once it receives power.

---

### Post by 2F4U on 2012-03-13
> **Roasted said:**
> I've come across some computers in the past that turn on once they're plugged in to power, kind of negating the need for a power button.

Never heard of that. But there are options (usually in the BIOS) to wake-on-lan, wake-on-usb or wake-on-pci, meaning that if one of these components becomes active, the PC wakes up.

---

### Post by Toz on 2012-03-13
**rtcwake** might be able to do the job. Have a look at the script from post #5 of this thread: [http://ubuntuforums.org/showthread.php?t=1822517&highlight=rtcwake]("http://ubuntuforums.org/showthread.php?t=1822517&highlight=rtcwake"). This script worked only in a 24-hour time period, but you can edit it to wake at any time using the -s parameter.

---

### Post by Roasted on 2012-03-13
> **2F4U said:**
> Never heard of that. But there are options (usually in the BIOS) to wake-on-lan, wake-on-usb or wake-on-pci, meaning that if one of these components becomes active, the PC wakes up.

Yeah, I just went into the BIOS on this system and there's a section under Power listed as "Power After Failure" with a few options. Stay off was the default, however there was an option for Power On. Sure enough, if the computer is on and I cut the power, then plug it back in, it turns right on. Nice simple way to ensure the gizmo turns back on if you don't have a UPS sitting around.

Nonetheless, I'd still like to find a way to kick this guy on at a specific time. I'll look further into that script. On top of that, the BIOS had specific times I can fire up the computer as well. I tested a few and they worked. Thing is, I can only specify it by every day, or a specific day of the month. I can't lock it down to a specific day of the week.

I'm playing with GShutDown now to see if there's a way I can have it shut down automatically 6 hours after it turns on. That way if I could have the BIOS kick it on at 6 pm and power off at midnight, that way the system is only running 6 hours a day, cutting its up time down significantly.

At the same token, I still have to wonder, if this box is sitting idle most of the time, I wonder if it's even using a significant amount of energy worth worrying about. After all, there's nothing to the box... 300w 80+ PSU, 7200 RPM HDD... and that's it... no other drives, video cards, etc.

EDIT - what if I just set up a cron job to run daily at a specified time for "sudo poweroff" and let the computer's BIOS handle the power-on in the evening?

---

### Post by CatKiller on 2012-03-13
I find Wake-on-LAN useful. Another computer that's on can send a magic packet over the network to tell the computer to turn on. The other computer in my case is my phone.

Otherwise, your solution is fine for having your computer automatically come on for just the evening. You can be more flexible with your cron job, though; shutdown has an "at a particular time"option. You also don't need to use sudo in your command if you're using a system-wide job: that would just make the computer sit there waiting for you to type in your password.

---

### Post by Paqman on 2012-03-13
+1 for Wake-on-LAN. If the only time this machine needs to wake up is to accept a backup, then it makes sense for the machine that wants to send its backup to wake it up when ready.

---

### Post by Roasted on 2012-03-13
The only question I have about WOL is how would I handle the timing? If I have WOL and the backup set for 6:00 PM that of course wouldn't work because the system wouldn't be up yet. I assume WOL @ 5:45 PM and backup at 6:00 PM? How can you handle WOL like that? I wasn't aware other systems could do WOL... I thought it was always from the router (which in my case, I'm not sure if it's supported)

I set the system to fire up at 5:30 this evening via BIOS. I'm trying to SSH into it now and it doesn't appear to be online. Go figure. Either that or my parent's external IP changed. Possible, but very unlikely... I should probably register them a DDNS hostname while it's on my mind...

EDIT - Ya know, I'm just not sure... Deja Dup doesn't work based on a specific time... just "run once daily"... so I'm not sure I could get Deja Dup to choreograph properly with the example I explained above... Not to mention, even if I wanted my router to handle it - oh wait - I can't seem to find a single mention of "wake" or "wol" in this 59 page manual for the router. Nice.

---

### Post by Paqman on 2012-03-13
I would simply put it all in a script invoked by cron. There are command line tools that can send the magic packet (eg: etherwake), have your script send the wakeup, wait for a couple of minutes, check that the destination is up, then if it is commence an rsync backup. 

I would imagine deja dup is just using anacron, which doesn't really allow you to do exact timings like this. Anacron is an asynchronous cron tool (hence the name), which is a very handy thing to have on a desktop system, but not what you want in this case.

---

### Post by Roasted on 2012-03-13
> **Paqman said:**
> I would simply put it all in a script invoked by cron. There are command line tools that can send the magic packet (eg: etherwake), have your script send the wakeup, wait for a couple of minutes, check that the destination is up, then if it is commence an rsync backup. 

I would imagine deja dup is just using anacron, which doesn't really allow you to do exact timings like this. Anacron is an asynchronous cron tool (hence the name), which is a very handy thing to have on a desktop system, but not what you want in this case.

Yeah, I love Deja Dup though, but I'm not sure it's optimal in this case. It'd probably be easier to just set up SSH keys with the boxes and be done with it, and just have the Windows side (some boxes dual boot) mount the shares via samba.

I'm playing with gWakeOnLan right now for fun, but it's not kicking on my file server. Do I have to install something on the target system first? Or should Wake On Lan just magically work?

Also, what about laptops? Can a laptop send a WOL packet to wake up my file server since it's hard wired? Or do both systems in question need to be hard wired?

---

### Post by markbl on 2012-03-14
I use wake on lan on my ubuntu PC. Usually you must activate it via your bios. Also, ubuntu requires the following command in /etc/rc.local to set wol on the lan card each time you boot (eth0 for me):
```

ethtool -s eth0 wol g

```
Then you need a utility to issue wol packets on your lan. I use my iphone often but also use the "wakeonlan" command line utility form another debian box (aptitude install wakeonlan). You can run that from a cron job.

This wakes my PC up from cold, suspend, or hibernate.

PS, BTW: I backup my home windows PCs using a cron activated rsnapshot job on my ubuntu PC which backups that PC and "pulls" directories from the windows pc's. I install deltacopy on the windows boxes which is a windows version of rsync. All works well. Been using this for years now.

---

### Post by Roasted on 2012-03-14
I think I may have found a viable answer...

I just found "wakeonlan" in the repos, which simply runs in terminal... wakeonlan 11:22:33:44:55:66. Easy as can be. I just tested it and it works great.

Out of curiosity, I created a quick script and threw it in /usr/local/bin. It's owned by root:root but it's 755 perms, so even a regular user can execute it (after I ran chmod +x on it of course). I set it up in cron for a test and sure enough, it woke up my file server from suspend mode.

The real reason behind having my file server run for several hours was because Deja Dup from time to time does a full backup from scratch again, which of course takes time. If I'm using synchronize applications on the Windows side, and rsync on the Linux side, it should be substantially quicker.

As a result, I'm liking the idea of just setting the file server to suspend after an hour (currently the max suspend setting in power management) since I probably won't need to bank that heavily on longer uptime since it'll just be syncing raw data and not focusing on actual backups.

The only thing is, I can't get it to WOL from off, I can only wake it from suspend mode. I'm thinking suspend mode is likely the way to go anyway, just because it's quicker to re-initiate everything instead of going from a complete power off, but it still raises an eyebrow as to why it's not working. I wonder if there's a BIOS setting that only allows it to WOL from suspend, which I assume is the S1, S3, S4 etc settings I saw earlier.

At any rate, that sounds like a solid option. WOL from all machines on the network (since then that guarantees the file server will be woken up since none of the systems stay on 247 to guarantee that WOL will hit each time), and just rsync on Linux with ssh keys and synchronize with Windows 3rd party apps over Samba and suspend after 1 hour. Easy as pie.

The only thing now is to find an application for Windows systems to WOL...

---

### Post by Roasted on 2012-03-14
> **markbl said:**
> 
Then you need a utility to issue wol packets on your lan. I use my iphone often but also use the "wakeonlan" command line utility form another debian box (aptitude install wakeonlan). You can run that from a cron job.

This wakes my PC up from cold, suspend, or hibernate.

PS, BTW: I backup my home windows PCs using a cron activated rsnapshot job on my ubuntu PC which backups that PC and "pulls" directories from the windows pc's. I install deltacopy on the windows boxes which is a windows version of rsync. All works well. Been using this for years now.

Oh duh, I guess I don't need to create a script, but simply enter wakeonlan 11:22:33:44:55:66 in cron and call it a day. Wow, go me. Thanks for mentioning that, at least I don't need the script idea, even if it works. :P 

About DeltaCopy, glad it works for you! I had tinkered with DeltaCopy on Windows systems a while back but I was also trying to use rsync with DelaCopy over SSH-key based authentication over the WAN... didn't work out so well... but maybe now that I have a file server on the LAN I can give it another shot! At any rate, SyncBack Free Edition works great for syncing raw data over Samba shares from Windows boxes...

EDIT - I couldn't help but to notice, but I'm running two VM's of Ubuntu... one 11.10, the other 12.04.

11.10 - Software Center - Searched "wakeonlan" and received wakeonlan as an option.
11.10 - Software Center - Searched "etherwake" and received etherwake as an option.
12.04 - Software Center - Searched "wakeonlan" and received wakeonlan as an option.
12.04 - Software Center - Searched "etherwake" and received.... wakeonlan as an option.

Looks like etherwake was removed from the repos and the search query just routes over to wakeonlan. Anybody else notice that?

---

### Post by CatKiller on 2012-03-14
Waking up from powered off will be a BIOS setting.

---

### Post by Paqman on 2012-03-14
> **Roasted said:**
> Oh duh, I guess I don't need to create a script

I would run the actual backup from a script, so you can put some logic in there to check your destination is available and handle errors. You don't want your backup system failing silently and dumping massive backups onto the local machine.

---

### Post by Roasted on 2012-03-14
> **Paqman said:**
> I would run the actual backup from a script, so you can put some logic in there to check your destination is available and handle errors. You don't want your backup system failing silently and dumping massive backups onto the local machine.

How is that possible? I've never seen a failed rsync attempt re-route the data locally and just dump a duplicate onto the drive...

---

### Post by Rodney9 on 2012-03-14
```
sudo rtcwake -m mem -t `date +%s -d"2012-03-16 07:30"`
```

Will wake the computer from suspend on the 16th march 2012

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

I use this to wake my computer at 4:30am the next day.

Rodney

---

### Post by LiNIX420 on 2012-03-14
Nice thread.

A timer maybe could help?

---

### Post by Roasted on 2012-03-15
> **Rodney9 said:**
> ```
sudo rtcwake -m mem -t `date +%s -d"2012-03-16 07:30"`
```

Will wake the computer from suspend on the 16th march 2012

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

I use this to wake my computer at 4:30am the next day.

Rodney

I suppose that could work. Can you offer a little more insight on RTC wake? Is it entirely OS based, or is it dependent upon the BIOS features as well? I'm finding, on all of the towers I own personally, that WOL and RTC to be extremely unpredictable and unreliable. It works sometimes, doesn't work other times in identical scenarios, etc. I've grown rather untrustworthy of anything BIOS related at this point. One system will RTC 3x, but fail the next 2x. Another doesn't work at all, and then randomly works once and that's it. Really? 

If RTC wake is entirely OS based, I'd be a fan of it immediately (though I might be a little biased since most Linux utilities I utilize just plain friggen work), but I'd rather that than a BIOS level setting at this point.

My goal is to get the system to boot up every day at 5:00 PM. How would that work out? Would I have to set up a bunch of scripts, or simply install rtcwake and cron rtcwake-etc-etc-etc-etc @ 17:00 daily?

The only scary thing is I've heard of RTC wake being responsible for losing data. Any insight there?

> **LiNIX420 said:**
> Nice thread.

A timer maybe could help?

That's the next route I'll likely go... I thought about setting the BIOS to turn on after power failure (the one power BIOS setting that seems to work predictably each time, imagine that?) and just having the light timer kick power on @ 5:00 PM so it'll fire up the computer. Then, cron poweroff or something so the system shuts off at 6:50, then at 7:00 PM, the light switch shut off, losing all power. That way the system gently shuts down on its own while power is available, and then the power is cut so there's no draw until the following night when it fires up at specifically 5:00 PM again. It might not be the most glorious solution, but it's looking to be more enticing now.

EDIT - Further thinking about this, and considering the cheap price of timers, has suggested this is the way to go. WOL is a sweet idea, but it just doesn't work on all systems. The RTC thing is great too, when it works, but I really need something reliable. I'm seeing a lot of newer surge strips come with certain outlets timer-based, so I can rig it up so the port used by the backup server will be a timer slot, and then just set the BIOS to power on after power failure. Bingo bango, done.

---

### Post by Roasted on 2012-03-17
So, last night I couldn't help but to think, I have to be doing something wrong. I called MSI and talked to them about it and they said "the latest BIOS release should fix that" despite the fix it wasn't listed on the comments of fixes for the new version on their site. Nonetheless, I flashed to the latest BIOS, and it definitely made no change.

So... I did what I mentioned above. Went to Wal Mart, got a surge strip (6 outlet with 2 outlets set on a timer) and set the timer to power on 2 mins from now and shut off 3 mins from now. Worked beautifully.

Overall, my settings for my parents backup server will be like so:

6:50 PM, power up.
7:00 PM, clients back up.
8:30 PM, server shuts down via cron.
9:00 PM, power off to outlet.

That way, the clients don't back up immediately when the server does, there's a time offset. Then the offset with shutting down at 8:30 and cutting power at 9:00 is in case it hangs up for a bit when shutting down. I've never seen it happen, but I'd rather offer some sort of buffer there.

Sucks that the BIOS thing didn't work (I felt a little better reading other people had similar issues, even with different branded boards), but at least we still got a winning solution here.

---

### Post by Rebelli0us on 2012-03-17
This command will wake from suspend any machine on your network. Use the MAC address for your particular machine.

```
wakeonlan 00:1B:FF:B8:C4:68
```

You can create a menu item, or shortcut, or script.

---

### Post by Rodney9 on 2012-03-17
> **Roasted said:**
> I suppose that could work. Can you offer a little more insight on RTC wake? Is it entirely OS based, or is it dependent upon the BIOS features as well? I'm finding, on all of the towers I own personally, that WOL and RTC to be extremely unpredictable and unreliable. It works sometimes, doesn't work other times in identical scenarios, etc. I've grown rather untrustworthy of anything BIOS related at this point. One system will RTC 3x, but fail the next 2x. Another doesn't work at all, and then randomly works once and that's it. Really? 

If RTC wake is entirely OS based, I'd be a fan of it immediately (though I might be a little biased since most Linux utilities I utilize just plain friggen work), but I'd rather that than a BIOS level setting at this point.

My goal is to get the system to boot up every day at 5:00 PM. How would that work out? Would I have to set up a bunch of scripts, or simply install rtcwake and cron rtcwake-etc-etc-etc-etc @ 17:00 daily?

The only scary thing is I've heard of RTC wake being responsible for losing data. Any insight there?

.

I have used this ```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"` 
``` for the last few months with no problem. 

You just copy it into a terminal, probably easy to write a script or put in to cron.

I use it to have my laptop wake me from Suspend with some music and ready to check the net and my mail.

The only glitch is for all long uptimes, your browser wont release memory and sometimes you run out.

Rodney

---

### Post by bpmarkham on 2012-03-17
If you're looking to automatically wake up a computer you may want to look into [this]("http://askubuntu.com/questions/61708/automatically-sleep-and-wake-up-at-specific-times") as well. It's pretty simple script and it's easy to add to cron. Here are my cron entry examples. 

```
30 22 * * 1,2,3,4,7 /home/user/suspend_until.sh 14:00
00 01 * * 5,6 /home/user/suspend_until.sh 10:00
```

You may also want to consider installing ntp to keep your time from drifting. You can check that with the date and hwclock commands. Check out [this]("https://wiki.ubuntu.com/HardwareClock") reference for more information.

---

### Post by Roasted on 2012-03-18
> **Rebelli0us said:**
> This command will wake from suspend any machine on your network. Use the MAC address for your particular machine.

```
wakeonlan 00:1B:FF:B8:C4:68
```

You can create a menu item, or shortcut, or script.

Yeah, I know about that command. The issue is you need the hardware to support it... which has been back and forth with what hardware I've seen.

At any rate, the surge strip with the timer ports work great.

---

### Post by Rebelli0us on 2012-03-18
> **Roasted said:**
> Yeah, I know about that command. The issue is you need the hardware to support it... which has been back and forth with what hardware I've seen.

At any rate, the surge strip with the timer ports work great.

Wakeup from suspend S3 should work on all modern hardware. Wakeup from shutdown is trickier, but you can let the machines auto-suspend.

Ubuntu Software Center also has "Scheduled Tasks", similar to Windows' scheduler, so you can create a script and run it that way.

---

### Post by Roasted on 2012-03-18
> **Rebelli0us said:**
> Wakeup from suspend S3 should work on all modern hardware. Wakeup from shutdown is trickier, but you can let the machines auto-suspend.


Oh, I know. Believe me, I read pretty far into it, and even contacted several motherboard manufacturer's that I ran into this issue with. A quick Google suggests I'm hardly alone with WOL frustrations, even on several boards I bought within the last 3 weeks. 

I love WOL, but it's hard to get an array of different systems that act the same. That might be asking a lot, but I don't exactly have the same hardware for my HTPC as I have for my desktop, backup server, etc. So having different WOL behaviors is a bit frustrating. One WOL's from shutdown, the other from suspend, the other does something wacky. It'll WOL, but only if I suspended in between.

Example:

Power On - Suspend - Wake Up - Shut Down - WOL Works.
but...
Power On - Shut Down - WOL doesn't work. I need the suspend in between for WOL to work from shutdown.

WOL from suspend flat out doesn't work on that particular system.

That said, it's all good. The backup system is working beautifully. The only thing I ran into tonight is I needed some extra time for the initial backup to get done on the one laptop, and I forgot to reset the surge timer, so even when I turned off the cron job for powering off at 830 PM, the power still cut off at 9 PM. As a result, I set it so the power won't cut off until 11:59 PM, which is probably a good thing. That way, this is how it goes:

6:50 PM - Power On
7:00 PM - All systems back up
8:30 PM - Cron'd poweroff job
11:59 PM - Power Off

That way if I need to remote in and do some work that takes longer than expected, I just adjust the cron job and it'll stay on, since power won't cut until nearly midnight. That said, what I said above will be the projected schedule once initial backups are done and whatnot.

---

### Post by Rebelli0us on 2012-03-19
> **Roasted said:**
> Oh, I know. Believe me, I read pretty far into it, and even contacted several motherboard manufacturer's that I ran into this issue with. A quick Google suggests I'm hardly alone with WOL frustrations, even on several boards I bought within the last 3 weeks. 

I love WOL, but it's hard to get an array of different systems that act the same. That might be asking a lot, but I don't exactly have the same hardware for my HTPC as I have for my desktop, backup server, etc. So having different WOL behaviors is a bit frustrating. One WOL's from shutdown, the other from suspend, the other does something wacky. It'll WOL, but only if I suspended in between.

Example:

Power On - Suspend - Wake Up - Shut Down - WOL Works.
but...
Power On - Shut Down - WOL doesn't work. I need the suspend in between for WOL to work from shutdown.

WOL from suspend flat out doesn't work on that particular system.

That said, it's all good. The backup system is working beautifully. The only thing I ran into tonight is I needed some extra time for the initial backup to get done on the one laptop, and I forgot to reset the surge timer, so even when I turned off the cron job for powering off at 830 PM, the power still cut off at 9 PM. As a result, I set it so the power won't cut off until 11:59 PM, which is probably a good thing. That way, this is how it goes:

6:50 PM - Power On
7:00 PM - All systems back up
8:30 PM - Cron'd poweroff job
11:59 PM - Power Off

That way if I need to remote in and do some work that takes longer than expected, I just adjust the cron job and it'll stay on, since power won't cut until nearly midnight. That said, what I said above will be the projected schedule once initial backups are done and whatnot.

Some of the Windows magic packet wakeup & suspend utilities work better, so you can run these instead from inside Windows running in VM under Linux.

I wakeup & suspend all machines on my network from Windows Guests using WolCmd.exe & Sysinternals' PsTools PSSHUTDOWN.exe

---

