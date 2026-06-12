---
title: "Annoying disk checks locking me out"
date: 2011-11-12
forum: General Help
---

### Post by FLCL on 2011-11-12
So I have a SMART fail on my drive but it's still fine, not many corrupt sectors yet. Though ubuntu keeps doing disk check on boot and says it finds errors and it can't fix them. Just keeps trying and failing and an endless cycle. So I try to ignore them and boot but then nothing works. All dialogue boxes are blank even though I can select options, terminal is blank. No programs launch, and I'm confined to the desktop essentially.

I've had to wipe 3 times in a month- luckily I have all data on a separate partition. It happens every time it tries to disk check, system goes to crap right after. I've tried to use
```
 sudo tune2fs -c 9999
``` on the partition it says there are errors on and reboot but it ignores that and checks anyway.  

So, how can I disable all disk checks on boot and ensure that it won't ignore it and check them anyway? 
Windows works fine (dual boot) and so does Ubuntu..until the disk check- them I have to wipe again.

---

### Post by JKyleOKC on 2011-11-12
Look at the /etc/fstab file and note that each non-comment line ends with two numbers separated by spaces. These numbers control how the disk that line deals with are checked. If you change both numbers to 0, you should never see a file check again.

However, don't be surprised if some day soon you find that you cannot boot the system, and no amount of effort will make it possible. When SMART warns you of imminent failure and the disk check is unable to successfully recover, the life expectancy of that hardware can be measured not in days, hours, or minutes, but in seconds. If you don't have everything important backed up to another drive, or to CD or DVD storage, you'll find it gone with no chance of recovery -- and turning off the disk checks removes your last chance of being warned.

---

### Post by FLCL on 2011-11-12
Thanks for the reply, I'll give it a shot. 
I'm aware that the drive is doomed, I've backed up everything to an external but can't get a new laptop drive right now. So I'm riding the ship until it sinks essentially lol
Thanks for the help!

---

### Post by JKyleOKC on 2011-11-12
Actually it's only the final number that controls the check. If it's zero, no check will take place. A "1" means that drive will be checked first, while "2" means do it after the previous check finishes. Those are the only values defined for that position, per "man fstab".

---

### Post by HermanAB on 2011-11-13
Better start saving up for a new disk drive!

---

