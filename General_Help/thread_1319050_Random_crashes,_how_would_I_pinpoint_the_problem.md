---
title: "Random crashes, how would I pinpoint the problem?"
date: 2009-11-08
forum: General Help
---

### Post by KrisWillis on 2009-11-08
I have an old-ish (AMD 2200+ / 1GB) machine that lives in my airing cupboard, headless, which I use as a general server for downloading and serving media so it's mainly running Samba, SABnzbd (Perl based usenet client), Torrentflux, mt-daapd etc. It is on 24/7. Almost...

Randomly, this machine crashes, in that it drops off the network and becomes unresponsive, I can't SSH into it, or ping it. There is a keyboard hooked up to it, and the Caps Lock / Num Lock keys are also unresponsive, where they don't switch the lights on the keyboard itself. The machine has gone weeks without crashing, but it might crash after a few days, or even a few hours after re-booting, without any obvious action being taken to cause it. It could be idling in the middle of the night, or seeding some torrents, or whatever, it'll decide to crash.

It used to have 9.04 Desktop installed on it, which was upgraded from 8.10, which was upgraded from 8.04. I decided to give it an overhaul and replaced the actual OS HDD with a newer, larger one, and installed 9.10 server from scratch. This has not solved the problem, as for the first time since the re-install (9.10 release day), it crashed in the middle of the night, while grabbing some stuff from usenet.

During the re-install I also upgraded its storage capacity to 6TB over RAID 5. This is now a bigger problem, as when I hit the reset button to resolve this crash, it now needs to rebuild the RAID array, and 6TB takes about 18 hours.

Does anyone have any suggestions as to how I can figure out what is causing the crashes? Are there any logs that I should be looking at? I have considered that it might be over-heating, after-all it is in the airing cupboard, but I have done random checks with hddtemp and the hard drives never appear to go above ~30c. Considering I have replaced the OS HDD and reinstalled from scratch, I guess there is the possibility of there being a hardware problem? Any pointers would be much appreciated.

---

### Post by Vernünftiger Verbrecher on 2009-11-08
I would run memtest86, could be bad ram. If you get any responses from it post back here and I'll guide you through what to do if that is the problem.

Edit: You said over-heating is a possibility, and to my knowledge that is often what causes bad ram, so yeah I would be surprised if that isn't the problem. ;)

---

### Post by laluz on 2009-11-08
check /var/log/messaging and look for the records just before reboot is logged.
For the raid, add a internal bitmap [http://ubuntuforums.org/showpost.php?p=8060525&postcount=16](http://ubuntuforums.org/showpost.php?p=8060525&postcount=16)

---

### Post by KrisWillis on 2009-11-09
Thanks for the suggestions guys - I'll run memtest86 overnight to see if it picks anything up. I'll also create the internal bitmap on my RAID - I did actually have one on there, but I had to remove it before I could grow my RAID and forgot to put it back!

---

### Post by KrisWillis on 2009-11-10
Ok, so I ran memtest86 for ~8 hours and it didn't turn up any problems. I'm going to leave it running in a different room where I have easier access to a monitor to hook it up to, to see what happens if/when it crashes next time - I'll also check what's recorded in /var/log/messaging

---

### Post by bchurchill on 2009-11-10
also /var/log/dmesg and /var/log/syslog can help.  using the tail command can be helpful to condense output.

---

### Post by KrisWillis on 2009-11-20
So my server became unresponsive this afternoon while I was at work, I had an idle SSH session open at the time which got disconected. I came home this evening, the attached keyboard was not responding either so I hit the reset button.

Upon reboot, I checked the logs that you guys suggested, but unfortuntaly there was nothing in there of any interest. Just the stuff that's logged at boot time. The only things before that were at 06:00 and the day before...

Looks like I might have to find a screen I can hook up to this thing to see if there is any output when it crashes next time. If nothing still, looks like I might be swapping out some major hardware.

---

### Post by bchurchill on 2009-11-20
> **KrisWillis said:**
> So my server became unresponsive this afternoon while I was at work, I had an idle SSH session open at the time which got disconected. I came home this evening, the attached keyboard was not responding either so I hit the reset button.

Upon reboot, I checked the logs that you guys suggested, but unfortuntaly there was nothing in there of any interest. Just the stuff that's logged at boot time. The only things before that were at 06:00 and the day before...

Looks like I might have to find a screen I can hook up to this thing to see if there is any output when it crashes next time. If nothing still, looks like I might be swapping out some major hardware.

We should have recommended this earlier, but you should test your memory.  There's an option to do this on the Ubuntu live CD.

---

### Post by P4man on 2009-11-20
To be clear, this problem also occurred with ubuntu 8.04 or not?

A few things to try: find an update for your bios. Try booting with vesa drivers (if you are running X on it, are you?). Try booting with acpi=off. kernel option.

Also if it does lock up, rather than hitting reset always try [reisub]("http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html") first. And yes, that can work even if the numlock doesnt respond.

---

### Post by KrisWillis on 2009-11-23
> **bchurchill said:**
> We should have recommended this earlier, but you should test your memory.  There's an option to do this on the Ubuntu live CD.

I have already ran memtest86 for about 8 hours, with no errors.

> **P4man said:**
> To be clear, this problem also occurred with ubuntu 8.04 or not?

Yes, this also happened with 8.04, 8.10 and 9.04.

> **P4man said:**
> A few things to try: find an update for your bios. Try booting with vesa drivers (if you are running X on it, are you?). Try booting with acpi=off. kernel option.

Thanks, I'll look for a BIOS update and try with acpi switched off. X is not running (or installed?) on this machine - I'm running the server install.

> **P4man said:**
> Also if it does lock up, rather than hitting reset always try [reisub]("http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html") first. And yes, that can work even if the numlock doesnt respond.
Interesting, I wasn't aware you could do this - I'll give it a go next time - Thanks.

---

