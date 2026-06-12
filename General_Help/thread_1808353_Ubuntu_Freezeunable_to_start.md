---
title: "Ubuntu Freeze/unable to start"
date: 2011-07-20
forum: General Help
---

### Post by Shadowstrike2 on 2011-07-20
Basically I was playing World Of Warcraft when my mouse suddenly began locking up and becoming unresponsive jumping and then not moving at all. My keyboard soon followed suit and my internet appeared to disconnect on its own however the way the battle continued while I was in party suggested otherwise. Finnally everything locked up and was frozen so I used the power button to turn off. Now when I attempt to boot my computer nothing happens. I get past bios and then It simply displays 56hz 108 frequency out of range. I believe this has to do with my monitor being excessively old. That was the first time. I used my Install CD and reinstalled and now less then 36 hours later it happens again. However this time once I noticed the mouse doing the same thing I immediately shut the computer off via alt f4 and hitting enter. Am currently booting off the "try ubuntu without installing" option on my disc. I've had similar problems on Windows and I believe it might be the hardware going bad.

Computer specs: Dell Dimension C521
2GB Ram
500GB Western Digital Hard Drive
Nvidia Geforce 6150 built in card.
2.8 AMD processor
Unsure about my sound card.

Am primarily looking for some kind of fix or an easy way to recover from this issue short of a full reinstall so I can keep this computer running for as long as possible. I am currently unemployed and can not afford to get a new computer or new hardware.

Thanks in advance for the help. 

-CW

---

### Post by Shadowstrike2 on 2011-07-20
Bump. Still seeking assistance. Please help.

@Edit@ unbolded.

---

### Post by mokrates on 2011-07-20
I don't understand how a reinstall is able to fix hardware problems.

I know the effect of the machine going unresponsive. Mostly it happens when the cronjobs tidy up the system. Does it happen at night? Around 12 to 4 o'clock in the morning?
If it is related to this (and windows does similar things) then it could be, that you corrupted your harddrive by just turning it off. If the system goes unresponsive, you should check, if there is massive harddrive activity, and try to just wait it out.

A faulty harddrive can be the reason for slow harddrive responses (corrupt sectors will be tried a couple of times and the drive will be reset repeatedly, causing software-hangs)

You should check your harddrive i think: logs, S.M.A.R.T, fsck, etc

---

### Post by Shadowstrike2 on 2011-07-20
After a reinstall my computer appears to work again minus all my personal files :( I'm likely wrong, I was taking a shot in the dark.

Well the way I'd describe it as it feels like my drivers sort of bite it. For example the sequence seems to be mouse then sound then Internet then keyboard stop working in that order.

Actually it did happen around 3am. Not sure exactly what that means however. However the first time couldn't have been after 8pm.

How do I check hard drive logs? I cant seem to access my computers file-system. Error appears to be "Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1"

Just though about something. It does seem like the hard drive is corrupting from what I recall from windows. However on windows I had no choice but to shutdown as a blue screen would occur. Do you think my hard drive is simply bad?

---

### Post by mokrates on 2011-07-20
what did you enter to mount the device? did you try it from a live-system?

---

### Post by Shadowstrike2 on 2011-07-20
I simply attempted to click it in places while using the disc option *Try Ubuntu without installing* Not sure if thats live system mode.

---

### Post by mokrates on 2011-07-20
yep, that sure looks like a corrupted drive. good thing you already wiped it, so there is no data lost, i hope? seems you have to buy a new one. (in my humble opinion. best find your local guru and have him have a look at the drive)

---

### Post by Shadowstrike2 on 2011-07-20
That's so odd though. This hard-drive is under two years old. Its western digital a bad company to buy from for future note? Also I have a sixty gig hard drive that I used to use. I'll try reinstalling on there.

---

### Post by mokrates on 2011-07-20
Not really a bad company. If it's running much, 2 years is a good average for a drive. Some stay longer, some go earlier.
And, yes, if you had similar problems with windows, it points to hardware, so: harddrive matches.

---

### Post by Shadowstrike2 on 2011-07-27
Swapped the drives. Reinstalled. Worked till an hour ago. internet wasn't loading anything so i restared and now I have the same problem. No error message, no nothing. Some way to fix this?

---

### Post by mokrates on 2011-07-27
I don't know. Anymore. I'd suggest you try a memtest (knoppix or grml live cds have that installed). You also can install memtest in your bootloader, but if your machine doesn't really work, that could be hard.

---

