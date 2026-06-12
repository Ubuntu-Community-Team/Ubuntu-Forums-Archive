---
title: "Losing terminal and other window text"
date: 2010-03-21
forum: General Help
---

### Post by ckuecker on 2010-03-21
Hello,

I don't quite know how to put this problem - recently, my installation has started losing the text in terminal and other windows. I will open a terminal window, and there's nothing there - no cursor, no background. After this occurs, I try to restart the system - the 'Restart" window appears, and is also blank. Hitting enter at this point blanks the entire screen to black, after which the only recourse is to power-down and restart. Of course, then I need to run the recovery mode and fsck to get the system back up.

The first time this happened, I had to rebuild the kernel to recover. Luckily, i lost no data, but this is making the system unusable. I need a stable system to finish the project I am developing for an embedded Linux system.

I am running Ubuntu 9.10, with the latest updates.

Chuck Kuecker

---

### Post by ckuecker on 2010-03-21
One other possible clue - when this happens, I lose my email server. That symptom has been popping up every few days - I have to restart postfix and dovecot to get the server back up.

Does this suggest anything systemic?

Chuck Kuecker

---

### Post by lidex on 2010-03-21
Check your logs and post anything suspicious here. 
```
/var/log/dmesg
/var/log/messages
~/xsessions.errors

```

---

### Post by dcstar on 2010-03-21
And check CPU temps etc.

Also a thorough boot memory check would be in order.

---

### Post by ckuecker on 2010-03-23
CPU temperature is running around 10 C above ambient in my shop - right now, it's sitting at 28 C.

When I run 'sensors' in the terminal, I see peak temps of 142.6 C. Artifact of just installing the sensor code, or real trouble?

The system locked up twice again last evening. I found one interesting message in 'messages' - it looks like my USB external backup drive might be the culprit. I unmounted and removed it.

This is interesting - I have a similar machine tunning Windows 2000 for my engineering apps, and it has had serious problems with USB connected hard drives in the past. Random lockups. When I removed the drive, the troubles disappeared. Maybe the mother board or BIOS has a problem with USB hard drives.

If it does not lock up in the next 24 hours, I will start to think I've fixed the trouble.

Chuck Kuecker

---

### Post by ckuecker on 2010-03-23
Further information - I found the main hard drive cable was intermittent. Replaced it.

I still have instances of weirdness with the display - I just opened the log file viewer window, and it's blank.

Restart from the upper left hand corner pull-down does not work, either.

About to try the control-printscreen sequence again It has not been working lately.

Chuck Kuecker

---

### Post by ckuecker on 2010-03-23
Control-printscreen does not work. sudo reboot from the terminal returns "sudo: reboot: command not found"

It amazes me that Firefox is still working right.

Killing power right after this - yet again. 

Chuck Kuecker

---

### Post by ckuecker on 2010-03-23
Well, whatever the problem, it's getting worse. I restart the machine, run fsck to recover from the hard shutdown, and it runs for ten or fifteen minutes before something ties up.

Log files show nothing provocative. Temperatures are running in the upper 20 C range - it's cool in here today.

Major symptoms are still losing text in message boxes, and now I am seeing inability to launch programs from the GUI or from the terminal - I get 'command not found' messages, like the filesystem is fouled up. Ultimately, the mouse and keyboard lock up.

I am getting real frustrated here. I need a Linux machine to develop my project code on, and to run my email server and web server. I can't survive having to restore the machine every half hour.

---

### Post by ckuecker on 2010-03-23
Again!

I tried to look at the logs - got 'Could not launch Log File Viewer Failed to execute child process "gnome-system-log" (No such file or directory)"

All the icons on the desktop went away.

Do I have the cursed version of Ubuntu by any chance? Anyone know a Ubuntu exorcist?

Firefox works yet - so does the spell-checker - but everything else is gone. I guess Firefox is still live because it's running in RAM.

Chuck Kuecker

---

### Post by ckuecker on 2010-03-24
OK. This morning, after running the RAM test overnight, and seeing no problems, I restored the system and restarted it, to retrieve some of my emails.

I got a few dozen emails out of the Ubuntu box before I got the 'can't connect' message. Switched to the Ubuntu box and saw the screen saver merrily plugging away.

I realized the the lockups seem to correspond to the screen saver kicking in. So, I restored the system again, restarted, and tried to disable the screen saver.

The power management screen was blank after I changed to 'blank screen' and unchecked the 'activate screensaver when computer is idle' box.

Restoring the system yet again, I found the screen saver settings back to where they were.

So - the latest thought is that the 'engine' screen saver from the older release, or possibly the screen saver system, is the culprit. Time will tell.

Chuck Kuecker

---

### Post by ckuecker on 2010-03-24
Just accessing the screen saver screen causes the lockup. Getting closer.

Next, I'm going to try removing the package with the old screen saver - without touching the screen saver preferences page, then restart.


Chuck Kuecker

---

### Post by ckuecker on 2010-03-24
:p

Well, that seems to have fixed the major lockup problem. I removed all of the screen saver packages, and the preferences selection is now gone. The machine has been running for over an hour now, no lockups.

Thanks for listening!

Chuck Kuecker

---

