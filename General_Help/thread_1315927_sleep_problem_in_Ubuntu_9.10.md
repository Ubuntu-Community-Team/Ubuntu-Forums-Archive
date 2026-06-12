---
title: "sleep problem in Ubuntu 9.10"
date: 2009-11-05
forum: General Help
---

### Post by dave clark on 2009-11-05
I am a new user of Ubuntu Linux and know very little about it.
I am using an Emachine with a pentium processor and windows XP sp3.

I downloaded the 9.10 Ubuntu ISO image and burned it to a CD. From the CD, I made a permanent install of Ubuntu 9.10 the other day and all proceeded as expected. My hardisk was partitioned for Linux and a menu came up at startup letting me select my operating system.

Since the install, I have run both systems Linux and XP and both worked perfectly as far as I can see.

Under windows my emachine keyboard has a sleep switch which powers the machine down, and when hit again, wakes it up.

I was running Ubuntu Linux and made what seems to be a very serious mistake. I hit my sleep button and the system powered down. I hit the sleep switch awhile later and neither my monitor nor system would power up. 

I have turned the monitor off and on a number of times.It comes on and them immediately goes into sleep mode. I have turned the computer off and on a number of times. It comes on but does not reboot. I turned it off, put the Ubuntu install disk in the CD Drive hoping it would reboot from the CD (my BIOS is set properly) but nothing happened.

I now have a machine that comes on but will not reboot and a monitor that stays asleep and will not display any images.

Does anyone have any ideas about how I can recover from this disaster? I'd appreciate any thoughts.

Thank you 

Dave Clark

---

### Post by mcduck on 2009-11-05
Just turn both the computer and the monitor off, and unplug them for a couple of minutes. After that everything should work just fine.

I can't really say anything about the suspend feature failing, since that depends mostly on your hardware and you didn't tell anything about the computer itself. But I've seen this kind of thing happening couple of times with Ati graphics cards (and Ati/AMD's drivers). I was never able to suspend the machine reliably when using Ati's drivers, about one time out of ten the computer woke up again but graphics card didn't, meaning that I got no picture no matter what I did (the system itself was running however). I had the same problem in bot Linux and Windows. Using the opensource driver seems to have solved the problem so I suppose it was related to Ati's proprietary driver.

---

