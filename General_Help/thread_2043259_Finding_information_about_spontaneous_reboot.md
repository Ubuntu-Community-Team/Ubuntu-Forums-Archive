---
title: "Finding information about spontaneous reboot"
date: 2012-08-16
forum: General Help
---

### Post by Alqamar on 2012-08-16
Good morning.

I installed Ubuntu two years ago (10.04, I think...) and I am still a complete newbie. I'm very happy with it, but there are still lots of things I don't know how to do.

This morning my 12.04 spontaneously rebooted while I was away for two minutes. It was displaying a full-window Firefox tab. I didn't have any other programs opened. I checked for updates after the reboot (everything looks like it is working fine), and I got asked to install 23Mb of updates. 

Where can I find information about the reboot? I used the Log Reader to read kernel.log and kernel.log1 (because I read in the Forums that it could be a thermal problem) but I haven't found any messages about 'thermal' 'temperature' 'heating' or anything similar.

Could you please tell me where I should look? Or should I forget about it until it happens again?

---

### Post by decrepit on 2012-08-16
Do you mean your computer shuts it's self down then starts up again, or you computer starts up by it's self when switched off?
Mine does the later, but it happens regardless of distro, I think it must be something to do with the hardware.

---

### Post by Mark Phelps on 2012-08-16
Kernel bugs were introduced in recent kernel version that can lead to overheating in laptops.  If yours is a laptop and is overheating, that's most likely the reason it's shutting down.

---

### Post by Alqamar on 2012-08-16
Thanks, Marks, but my computer is a desktop. 

It didn't turn on on its own, it was working fine. Then I went away from the room for two minutes and we I came back it had rebooted itself and was showing me the login screen.

The main problem is I don't know why it happened and I don't know where to look for more information, in case it happens again.

Should I post complete technical specifications?

---

### Post by decrepit on 2012-08-19
Logs are in /var/log/
have a look at messages there's a lot of stuff in there, may be a bit of a needle in a haystack. But if you can find the exact date and time, somebody here may be able to decipher the info.

---

### Post by robert shearer on 2012-08-19
> **Alqamar said:**
> Thanks, Marks, but my computer is a desktop. 

It didn't turn on on its own, it was working fine. Then I went away from the room for two minutes and we I came back it had rebooted itself and was showing me the login screen.

The main problem is I don't know why it happened and I don't know where to look for more information, in case it happens again.

Should I post complete technical specifications?

Have you eliminated the simple explanations  ?
1) You had a power outage perhaps ...?
2) You returned to the lock screen of the screen-saver...? that asks for your password if configured so, (and you are assuming a reboot.)

Generally the default setting of bios is to stay powered down in the event of some power glitch causing loss of power.
 So #2 seems more likely.
Step away from the keyboard for the same length of time as before and don't leave the room.. :-)

---

