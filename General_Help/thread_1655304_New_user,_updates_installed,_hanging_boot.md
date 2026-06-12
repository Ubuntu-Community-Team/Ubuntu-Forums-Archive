---
title: "New user, updates installed, hanging boot"
date: 2010-12-29
forum: General Help
---

### Post by camtom12 on 2010-12-29
Hi!
 
I've got 10.4.1(rev190?) installed in what I guess is Wubi and have been running dual boot for a couple of weeks now. My other OS is XP. I recently ran the updater then shut the computer down for a week. I can't remember now if I had to restart to complete any updates or not but my laptop battery is fried so once I unplugged it after it completed shutdown all power was removed from the system for 9 days. Today I tried to boot Ubuntu and after I chose it from the boot menu it flashed some sort of message about WUBILDR really quick (I wasn't able to read it all) then went through its normal boot until the Ubuntu splash screen where one dot went red and the system hung. I allowed it a good 15 minutes to see if it would unhang but no dice. It boots fine on XP.
 
Any advice? I'm reading the Wubi Megathread right now but as I'm new to Ubuntu I figured I'd check to see if anyone else experienced these particular problems here, too.
 
Right now I'm going to download the Ubuntu installer to a disk to try some of the Megathread troubleshooting.
 
Thanks!
--Cameron

---

### Post by bcbc on 2010-12-29
> **camtom12 said:**
> Hi!
 
I've got 10.4.1(rev190?) installed in what I guess is Wubi and have been running dual boot for a couple of weeks now. My other OS is XP. I recently ran the updater then shut the computer down for a week. I can't remember now if I had to restart to complete any updates or not but my laptop battery is fried so once I unplugged it after it completed shutdown all power was removed from the system for 9 days. Today I tried to boot Ubuntu and after I chose it from the boot menu it flashed some sort of message about WUBILDR really quick (I wasn't able to read it all) then went through its normal boot until the Ubuntu splash screen where one dot went red and the system hung. I allowed it a good 15 minutes to see if it would unhang but no dice. It boots fine on XP.
 
Any advice? I'm reading the Wubi Megathread right now but as I'm new to Ubuntu I figured I'd check to see if anyone else experienced these particular problems here, too.
 
Right now I'm going to download the Ubuntu installer to a disk to try some of the Megathread troubleshooting.
 
Thanks!
--Cameron
This doesn't sound like the problem the megathread deals with. Try editing the first menu entry (hit 'e') and remove 'quiet splash', then CTRL+X to boot.
See what the last lines are before the computer halts.

Also you try booting a previous kernel as there was a kernel update recently.
Finally you could try recovery mode too.

---

### Post by camtom12 on 2011-01-02
> **bcbc said:**
> This doesn't sound like the problem the megathread deals with. Try editing the first menu entry (hit 'e') and remove 'quiet splash', then CTRL+X to boot.
See what the last lines are before the computer halts.

Also you try booting a previous kernel as there was a kernel update recently.
Finally you could try recovery mode too.

Well, I haven't had a lot of time before about 3 hours ago to pick this up and work on it but boy has it been an academic 3 hours!  An additional symptom that hadn't shown up until the last couple of times I tried booting was a complete system reset after selecting Ubuntu from the boot menu.

I got all my Ubuntu files backed up in a couple of places, then fixed the grub issue permanently.  Now I've got a little breathing room until I get more time to partition.

This was the solution to my problem: [http://ubuntuforums.org/showpost.php?p=10180622&postcount=13](http://ubuntuforums.org/showpost.php?p=10180622&postcount=13)

Thanks!

---

