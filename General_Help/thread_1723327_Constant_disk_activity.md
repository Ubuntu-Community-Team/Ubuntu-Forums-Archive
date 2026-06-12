---
title: "Constant disk activity"
date: 2011-04-06
forum: General Help
---

### Post by cjhabs on 2011-04-06
Hi

I understand that Ubuntu typically has some disk activity even when idle, but I believe that I have a problem that I am worried is affecting my disk drive - which has recently become quite loud.

The system disk activity light flashes about twice per second, all the time, when idle.
iostat shows a Blk_wrtn/s of between 10 and 40.

I am running Lucid x64. The system disk uses ext4 for root and ext4 for /home.

The disk activity starts before I even log in.
There is no disk activity if I drop to the root shell in recovery mode - as seen by no flashing light and iostat writes = 0.
I have tried killing my media server processes, Mediatomb and Squeezeboxserver.
I have unmounted the ntfs data drive.
There is nothing else running beyond the vanilla install to my recollection other the services above that I stopped.

How can I determine which process is causing the constant writing? I do not have this issue on my laptop which is running Karmic, and as I mentioned earlier, I think this non-stop activity is damaging my drive.

Thanks for any insight.

BTW - I have read all of the existing posts regarding this issue and tried/checked what was recommended - nothing applied to me. 
The resource usage on my decent server is minimal - no swapping or taxing of the cpu - and performance is ok - just constant disk activity.

Chris

---

### Post by cjhabs on 2011-04-07
Well, I've done some more digging.
iotop showed that jbd2 was kicking in constantly - this is the journalng for ext4 - so I changed it to run every 20 seconds and that worked. However, the disk light is still flashing constantly.

I killed hald and all of its related processes - no change.

What is strange is that iostat shows writes constantly happening to my system disk, but iotop does not. I am guessing that the writes are being caused by a kernel level process that iostat catches but iotop does not - but it's a guess.

The good news is that the noise I am hearing turns out to be the cpu fan, not the disk.

But I sure would like to work out what is writing to the disk every few seconds. It is definitely not any kind of logging - the logs are all quiet.

Any ideas would be welcome!

---

