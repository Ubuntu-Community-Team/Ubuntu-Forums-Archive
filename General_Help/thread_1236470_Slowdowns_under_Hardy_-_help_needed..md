---
title: "Slowdowns under Hardy - help needed."
date: 2009-08-10
forum: General Help
---

### Post by Thanh-BKK on 2009-08-10
Hello.

I am in need for a little help here. My Hardy starts playing up on me and i have no idea why.

A little background info:

Since as long as i have used Hardy there were slowdowns when using Thunderbird, and specially so when Firefox was open at the same time. Thunderbird would grey out for some time and eventually display "a script on this page is busy or has stopped responding". Upon clicking the "stop script" button Thunderbird would continue to work normally.

This has gotten worse to a point that it is pretty much impossible to start Thunderbird and Firefox together - even a switch to Swiftfox brought no change whatsoever. I feel that with every update to either Thunderbird or Firefox it gets worse. The grey-out period is always exactly 30 seconds, but now it also happens when Firefox/Swiftfox is not even running, it is extremely annoying.

What i noticed is that, during the time Thunderbird greys out, the entire computer slows to a crawl but System Monitor shows no noteworthy CPU load or frozen applications at all. However (and this might be the point) the HDD light is steadily "on" during that period, it stops the moment i click the "stop script" button.

Now as of lately my computer behaves similarly (i.e. greying out) when opening folders with many files in them or when drag/dropping files between folders. These "grey-outs" always last only few seconds, but then, too, the HDD light is steadily "on".

My system-HDD is a 80 GB one which holds only Ubuntu, but my data is still on a second HDD with NTFS-partitions (a 500 GB drive with four partitions). I doubt that the hardware is about to fail because everything appears to work perfectly, i did not see a single corrupted file or like that which would indicate a failing drive. And the Thunderbird-issue does not involve those NTFS-partitions at all either.

Is this a bug in Ubuntu that can somehow be fixed (maybe a log somewhere worth looking at?) or would it go away if i change the NTFS partitions to ext3? By now i am fairly sure i won't ever use Windows again :) Could my NTFS partitions have become fragmented and if so, is there a way to defragment them from within Ubuntu? 

The machine still starts very fast and general operation is not affected at all, it never crashes and applications don't crash either, it is just these annoying delays at times. 

With best regards.....

Thanh

PS there is still lots of space on all of the partitions, none of them is anywhere near "full". The computer is powered by an AMD Athlon 64 x2 5000+, 2 GB of RAM.  Ubuntu is 8.04.2 with the latest updates as of yesterday.

---

### Post by Thanh-BKK on 2009-08-11
*bump*

Anyone..? 

Thanh

---

### Post by DaithiF on 2009-08-11
Hi,
do you have any thunderbird add-ons installed?  I would start disabling them one-by-one to see if one of those is the cause.  For example, your problem sounds a little like this one:
 [http://vienna.in-a-nutshell.net/2006/thunderbird-extension-mailbox-alert-problem-script-unresponsive](http://vienna.in-a-nutshell.net/2006/thunderbird-extension-mailbox-alert-problem-script-unresponsive)

good luck
D

---

### Post by Thanh-BKK on 2009-08-11
Hello.

Yes there are two add-ons (or rather extensions), one is "Webmail" and the other is "Hotmail". Without them Thunderbird would be useless as i still (need to) use three Hotmail accounts (one is actually a live.com, same-same) and three G-Mail. 

I will test in the evening how it performs with those two disabled as i am at work now using Winblows.

Best regards....

Thanh

---

### Post by Thanh-BKK on 2009-08-12
Hello.

Some update. I saw that Hotmail nowadays supports POP/SMTP so i quickly changed the servers and disabled the two extensions for T-Bird. The result is that fetching/downloading mails goes a hell of a lot faster - but regardless, T-Bird still greys out for 30 seconds exactly, followed by the "script" error message. 

It also greys out, although only for a few seconds, when opening an e-mail which contains html of some sort (reading this in the lower right side window, not double-clicking it to open in a new window), and also when starting to compose an e-mail. 

With or without Swiftfox/Firefox being open at the same time. 

And again there is HDD activity during it greying out, which i don't know why that is there. I checked with the System Monitor, there is no obvious CPU load (dual core, both are at less than 5%) and neither RAM (420 MB of 2 GB used) nor swap usage (0 byte/0.0% of 3.9 GB).

Kind regards.....

Thanh

---

### Post by Thanh-BKK on 2009-08-25
Hello.

Another update to this issue - it seems to be solved now. Thunderbird came out-of-the-box with a thingy named "Beagle", i still don't know what it actually does (indexing mails, yes, but in which way is that useful..?) and disabling that, even though it came with Thunderbird originally, solves the slowdown-and-HDD-thrashing issue. 

At least until now (disabled it yesterday evening after my computer was stuck for several consecutive 30-second-terms and have since started T-Bird deliberately for testing half a dozen times, including once after a reboot. Even when i start Firefox simultaneously the both of them just open, neither one goes grey).

Kind regards.....

Thanh

---

