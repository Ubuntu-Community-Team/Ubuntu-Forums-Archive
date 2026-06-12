---
title: "Why does hibernation uses laptop battery?"
date: 2010-06-09
forum: General Help
---

### Post by Svens on 2010-06-09
Hi everybody!
I have a little question for you. All the time I thought, that laptop hibernation doesn't use battery power at all, because all data from RAM is stored in HDD and nothing needs battery power in that time. But since I installed Ubuntu 10.04 (I didn't saw that kind of thing in previous versions), hibernation uses battery power. Is that supposed to be so?
I attached a picture to show the data from which I have this question.
All those lines from 19h to 9h, from 9h to 4h, and 3h to 0s are times when I used hibernation. I hope that it is easy to understand.
Thank you!

---

### Post by ThesaurusRex on 2010-06-09
From what I know, the only way to get your computer to stop using power is to unplug it and remove the battery. Simply going into hibernation, think of some things that would use a battery to stay updated: system clocks, network printers, etc...

---

### Post by Svens on 2010-06-09
As far as I know, for system clock there is another battery inside the motherboard like this: [IMG]http://www.technibble.com/articlecontent/2007/12/remove-battery.jpg[/IMG]
As I thought before - the hibernation should be in power-consuming thing the same as shut down. Isn't that so?

---

### Post by ThesaurusRex on 2010-06-09
Does that battery get charged by the main battery? I actually don't know.

---

### Post by cherva on 2010-06-09
Suspending uses battery power to power the RAM of your laptop/pc (to preserve the data there) so when you power up your laptop/pc you are presented the screen from where you left.
If you do not want to stop using the battery use the hibernate mode. This mode puts all data from your ram to the SWAP space on your hard drive and you are presented the same screen you left, but it is slower because the data must get from the SWAP space to the RAM.
Google "Hibernate vs Suspend mode"
I hope this helps.

---

### Post by Svens on 2010-06-09
Wait, wait, wait. I don't know what is going on, but you just clearly described these two things, so I can see that you know what you are talking about. BUT I havent mixed those things. I know Hibernation and I know Suspend. And the Suspend is the one who clearly uses battery power and it can be seen in the situation when my PC from Suspend comes up in few seconds, while getting up from Hibernation takes much longer time. And I don't know what is mixed up now, but I clearly know that I am talking about that mode, which SHOULDN'T use battery power.
I even switched my PC language back to english, so I could see if I haven't mixed those two terms, but no - suspend uses RAM and Hibernation saves data in HDD. And my PC in hibernation (or to be more clearly - when it has saved its' data in HDD) uses battery power as you can see in the picture in my first post.

---

### Post by Slim Odds on 2010-06-09
> **cherva said:**
> Hibernation uses battery power to power the RAM of your laptop/pc (to preserve the data there) so when you power up your laptop/pc you are presented the screen from where you left.
If you do not want to stop using the battery use the suspend mode. This mode puts all data from your ram to the SWAP space on your hard drive and you are presented the same screen you left, but it is slower because the data must get from the SWAP space to the RAM.
Google "Hibernate vs Suspend mode"
I hope this helps.

No, it does not help. You have it exactly backwards. Hibernate stores your current running configuration to disk and then shuts down the computer. Suspend halts most system functions in memory and then goes into a low power mode.

To the original poster, does your system properly shut down after writing to disk?

Also, there is always a small drain on any battery even when not powering anything. I don't think that this is your problem, but wanted to mention it.

---

### Post by x C0MMAND0 x on 2010-06-09
> **ThesaurusRex said:**
> Does that battery get charged by the main battery? I actually don't know.

No it does not.  I have seen on systems that are a few years old users will notice their system clocks aren't functioning properly, this can usually be fixed by replacing the battery on the motherboard which has died.  It is the same battery that is used in most wireless keys as well (as in car keys with that have remote unlock).

---

### Post by Svens on 2010-06-09
Yes, as I can see, the PC shuts down properly - no lights are on, no sounds are coming from it, as it would be if some cooler or HDD would spin.
By the way - my laptop is HP Pavilion DV6698en.

---

### Post by Svens on 2010-06-10
:confused:

---

### Post by Svens on 2010-06-10
Still here. ):P

---

### Post by Manyette on 2010-06-10
Hi Svens,
You are correct in your understanding.  Hibernate should not use battery power, while suspend does use some small amount to keep the RAM alive.  But, have you considered that your power graph that you posted could not be running (it takes power to operated the graphing program) if you were truly in hibernate with absolutely nothing running?  Just a thought.

---

### Post by Svens on 2010-06-10
I understand your thought, but I assume that the way, how this power graph (that is built in to Ubuntu) works, is that it knows how full battery was when it was shutted down, then it messures battery level in the moment when it is turned on again and then it draws a straight line to connect those two points. It would be more logical and would exclude this kind of power waste. 
Does anybody have any suggestions?

---

### Post by Manyette on 2010-06-10
Hi Svens,
You may be correct, I do not really know, but I think it might be just as likely that there is no recording during that period, and there is not any battery drain, and that straight line it between the previous power draw, and the current power draw, and simply does not show the zero drain while there is no recording.  Again, I don't know for certain, but perhaps someone who is knowledgeable about how it actually works will come to our rescue and answer it for certain.

---

### Post by steveneddy on 2010-06-10
The "straight line" on your graph does not account for the actual "power off" event. So the software merely draws a line from last known "on" time to next known "on" time and merely connects the two.

To have a graph accurately depict an actual power "off" event you would:

1. Need system power to power the hardware that is powering the software

2. Need another PC or device that actually monitored the "suspended" PC for actual power "off".

So your graph is correct for the information that it is actually provided but will not actually depict the power "off" event as the graphing application is powered "off" itself, or shut down during the suspend process, so would be impossible for the application to "know" that there had actually been a power "off" event.

EDIT:

Another thing you may consider is when posting in the English portion of the UF, change the system language to English before snapping a screen shot so that all of the labels are actually in English.

Just a friendly suggestion.

Cheers

---

### Post by philinux on 2010-06-10
On my desktop if I suspend the power light flashes slowly while in suspend mode. With Hibernate it's completely off and I can unplug the machine.
Hibernate should not use any power at all.

---

### Post by Manyette on 2010-06-10
But I would suggest that the graphing software could have set a flag with the saved data during hibernate that would allow the graph to show the power off state upon resume.  Just a thought.

---

### Post by aysiu on 2010-06-10
Maybe it's this bug:
[Toshiba laptop battery is drained while shut down](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

According to some of the comments, it isn't just Toshiba laptops.

---

### Post by ktemkin on 2010-06-10
The vertical line you're seeing actually represents a period of 'no data'. The power daemon *intermittently* checks battery power; the graph draws a line between each point and its previous; when it receives no data at all (i.e. when it is in hibernate), this 'slanted' line can become elongated.

The battery power is probably being used in several ways between the two checks:

1) As was stated above, the most prominent is probably startup and shutdown; before the gnome power daemon runs, and after it is ended during shutdown, the system has no way of checking the battery power.

2) Your system itself may use minute amounts of power while off. Features such as 'wakeup on LAN' may drain very small amounts of the battery, depending on the hardware implementation.

3) Batteries naturally discharge, especially when store inside of a computer. If you were to charge your laptop to full, unplug it, turn it off, and then leave it alone for a week, you'd notice it had less charge than when it started. This is because no technology is completely efficient- the battery is losing energy to its environment.



It is *incorrect* to say a computer uses no power when in hibernate; just as it is incorrect to say a computer uses no power when its off.

---

### Post by Svens on 2010-06-10
Thank you for your replies!

Steveneddy - I will regard your suggestion for future, thank you. :)

Ktemkin - answering to your assumptions:

Assumption #1 - Yes, your thought is correct, the deamon could not check battery power while the system would have been just started, BUT it would mean that this battery lose should every time be the same amount. (as I understand it)

Assumption #2 - Yes, I agree to you that batteries naturaly discharge, but in my case this would mean that in one week my battery would self discharge 50%. Isn't it a little bit too much?

Aysiu - thank you, I will check that bug and post my inference to it!

---

