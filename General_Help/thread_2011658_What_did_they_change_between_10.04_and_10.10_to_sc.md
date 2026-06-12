---
title: "What did they change between 10.04 and 10.10 to screw up NTFS support?"
date: 2012-06-27
forum: General Help
---

### Post by MrNovi on 2012-06-27
Up through 10.04 you could boot up to a LiveCD and have it find all of your NTFS drives/Partitions automatically.  You needed to click on them to mount them, but at least they showed up in Places.  Starting in 10.10 and all subsequent releases that doesn't happen on a motherboard using an Intel chipset that has Raid capabilities.  Even if the controller is set to IDE or plain SATA none of the NTFS Drives/Partitions show up.  One has to download NTFS-Config (or similar app) to get to them.  

This is unacceptable.  One doesn't always have internet access to download something to access drives when booting from a LiveCD.  Plus, why should one have to?  It worked in 10.04 and prior.  What did they change that is causing this problem and how does one fix it so that a current LiveCD recognizes these drives/partitions right out of the box?  

Creating a LiveUSB with customized fstab or NTFS-Config (or other app) isn't the answer.  There has to be a better way.  Knoppix, Fedora, Mandriva, Slackware, Mageia, and other Live CD's don't have this problem. From everything I have been able to determine (either by personal testing or research) it is isolated to the 'Buntus.  10.04 is getting rather long in the tooth and I would like to upgrade to a more recent version, but the lack of NTFS support is making that impossible for now.  

Not knowing what they messed up to cause this problem also makes it difficult to update an existing hard drive install of 10.04 for fear of breaking the NTFS integration.  

I've done a LOT of reading about this, and so far all I find are theories and/or partial solutions, but nothing definitive.  Even when one does come across a theory/solution, all too often it is written by a Linux Expert who won't take the time to properly document the required steps to implement the fix.  One suggested installing an older version of libfuse2 and fuse-utils but doesn't tell you how to force install the older version or where to get them.  

Can someone please shed some light on this issue with a definitive answer, including COMPLETE steps on how to implement them for someone who isn't that familiar with all of the command line jargon.

---

### Post by gordintoronto on 2012-06-28
When I ran 10.10, I had no problems with NTFS partitions.

10.10 is no longer supported, as of April 10, 2012, so I have moved on.

---

### Post by MrNovi on 2012-06-28
I don't have problems with later versions on some hardware.  It's only a problem on Raid Controllers for some reason, even when running in just SATA or IDE mode.  That's what makes it so difficult to track down as not everyone is affected by this problem.

---

### Post by MrNovi on 2012-09-18
Still nothing? So no one has any idea of what Canonical did to Debian's base install when they created Ubuntu (and all of it's derivatives) starting with 10.10 that causes the problems with NTFS drives on some Intel Chipsets? Or is it simply a matter of them not wanting to reveal what they did to the general public. It's common knowledge that they changed something (or left something out) starting with 10.10 as ANY and ALL versions of a 'Buntu  based release (Mint, Pinguy, Zorin, etc.) also have this problem while no version of Debian, or any other distro based directly on a Debain base like Knoppix, SnowLinux, Kanotix, etc. has the issue. 

Let's get real here. Some people know exactly what was done and how to correct the problem. And no, modifying the fstab file is not the solution as it doesn't correct the underlying problem, only covers it up. Why is there such a reluctance to publicly reveal what it is? Continued silence on the matter only makes Canonical look bad and prevents a very real portion of Linux users from using any of your releases or their derivatives.  

Why do you continue to hide the information, and more importantly, why don't you fix the problem you created? You like to claim to be the best Linux, but the proof is in the pudding, and after 10.04 the pudding is spoiled.

---

### Post by Wim Sturkenboom on 2012-09-18
Is there a bug report on launchpad? As that is where the developers / maintainers hang around, not on ubuntuforums. If there is no bug report there, please log one; as you can probably reproduce the issue with a 12.04 liveCD/liveUSB, use that as 10.10 is no longer supported.

PS
If there is a bug report on launchpad, can you please provide a reference; just curious what you're talking about.

---

### Post by QIII on 2012-09-18
I have several NTFS drives that I have never had problems with.  That includes mounting automatically with fstab entries on my primary machine and on my network, including RAID.  That doesn't mean it doesn't happen, but if it involves specific hardware it needs to be addressed.

As stated above, this is not the place to demand an accounting from Canonical.  It is not likely that any developers or MOTUs spend much time here.  By and large, we don't work for Canonical.

This is an issue to address via Launchpad.

---

### Post by MrNovi on 2012-09-18
> **Wim Sturkenboom said:**
> Is there a bug report on launchpad? As that is where the developers / maintainers hang around, not on ubuntuforums. If there is no bug report there, please log one; as you can probably reproduce the issue with a 12.04 liveCD/liveUSB, use that as 10.10 is no longer supported.

PS
If there is a bug report on launchpad, can you please provide a reference; just curious what you're talking about.

There are numerous bug reports on Launchpad. Unfortunately none of them have a definitive fix. The one that comes closest states that one needs to force install an older version of libfuse2 and fuse-utils  but doesn't take the time to tell anyone how to do that so it's essentially useless. I've spent a considerable amount of time Googling how to force install libfuse2 and fuse-utils  with no success and numerous posts in numerous forums on the subject have gone unanswered. 

And I know that any testing should be done with a more current release like 11.10 or 12.04. I mentioned 10.10 as that is where the problem originated and now here it is 3 (going on 4) releases later and it still hasn't been addressed. 

> **QIII said:**
> I have several NTFS drives that I have never had problems with.  That includes mounting automatically with fstab entries on my primary machine and on my network.

As stated above, this is not the place to demand an accounting from Canonical.  It is not likely that any developers or MOTUs spend much time here.

This is an issue to address via Launchpad.

If you had taken the time to actually read my previous posts prior to replying you would have realized that not all chipsets are affected. The fact that you don't have a problem on your system is immaterial, inconsequential, and pointless. This issue is related to some Intel chipsets with a Raid controller, especially the P45/G45 series, and then only certain revisions. 

modifying the fstab entries is NOT the answer here as Ubuntu is completely incapable of even seeing the NTFS partitions/drives, let alone mount them on the affected chipsets. None of the workarounds including downloading and installing ntfs.config while un-installing whatever ntfs driver/tools they switched to starting with 10.10 really solve the problem. You can't get the NTFS partitions/drives to automount even with a customized fstab file. Even if that did work, it wouldn't help with a live cd or usb used on multiple computers. Having to waste 20 minutes or more each time you boot up a computer to recognize the NTFS drives/partitions is ridiculous and shouldn't be necessary. If all I ran was Linux and only rebooted the system occasionally it wouldn't be so bad, but due to work needs I can not switch to Linux full time as the apps I need to use are not available for Linux and do not run under WIne or in a WIndows VM from a Linux system so that is out of the question. I only boot into Linux when I have a need to do specific tasks and with the lack of support on this issue, it makes using any 'Buntu based distro more difficult than it is worth.

My primary purpose here is looking for assistance in fixing a very real problem, something that this forum is for (or at least something it used to be for). There are numerous threads on this very forum about this very problem, and to date none of them have been satisfactorily resolved. That is why I worded my posts as I did. Maybe it wasn't appropriate to call out the developers that way, but when one has been fighting this problem for over two years you get very frustrated when no one is willing (or capable) of offering actual assistance with a problem. 

All I want is a working Linux system, and it seems that a 'Buntu based distro is not the way to go which is a shame as I was a faithful 'Buntu user from version 5 thru 10.04 when they dropped the ball and stopped caring about their end users (except for the corporations that pay for support).

---

### Post by oldfred on 2012-09-18
It may be your motherboard vendor. Have you got the latest BIOS?

It is not the P45/G45 series as that is primarily memory & video. 
The ICH10 is the SATA controller.

We also find BIOS settings can make a big difference in how things are handled.

But I have not had any issues with my ICH10 chip and NTFS at all.
the version of libfuse2 I have is:
fuse (2.8.6-2ubuntu1) precise
 
I had no issues in 10.10 which was my main install  until I installed 12.04.

---

### Post by MrNovi on 2012-09-18
I have the latest bios, and have tried all of the bios available for that motherboard. Different settings in the bios have absolutely no affect. 

Okay, maybe I should have said ICH10R as that is the SATA controller.  The ICH10 (doesn't have raid) and the ICH10M (for mobile platforms and again doesn't have raid) are not affected. It's the ICH10R that has Raid capabilities that is affected, and only some revisions of it are so it's not surprising that you aren't experiencing the problem. The affected revisions were commonly used on later P45 and G45 chipset motherboards. It doesn't matter if you have it setup using Raid or not, or whether you have AHCI enabled or not. It has to do with the revision of the controller chip. I have two nearly identical motherboards setting here. The older board revision isn't affected while the newer one is. Same bios, same bios settings, same hard drives, etc. I can swap out everything connected to the board that has the problem to the other board and no problems accessing NTFS drives and vice versa. Load up ANY and ALL releases of Fedora, Mandriva, Arch, Debian, Knoppix, PCLinux, an older 'Buntu based systems thru 10.04 on the affected system and no problems which shows that it isn't a problem with the motherboard/chipset/controller but with the way that 'Buntu based releases newer than 10.04 deal with NTFS. 

I appreciate your telling me what version of libfuse2 you are running. The latest version that works on any of my 'Buntu based distros is 2.8.1-1. I don't remember what version is in 10.10, but I know that 2.8.4-1 doesn't work on the affected chipset.

Finally, not meaning to be rude but I'm really sick of people telling me that they don't have any problems. I know that not everyone does and it just bugs the heck out of me having people say over and over that they don't have a problem when they are not running the same hardware that I (and the others who do have the problem) are running. At least you took the time to identify what chipset and what version of libfuse2 you are using. That shows that you are trying to help and I appreciate it.

---

### Post by oldfred on 2012-09-18
The only bug reported with a search of ICH10R.

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/619361](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/619361)

They seem to be converting from dmraid or the "fakeRaid" to mdraid.

See very last line in this:
[https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

---

### Post by QIII on 2012-09-18
> **MrNovi said:**
> 
If you had taken the time to actually read my previous posts prior to replying you would have realized that not all chipsets are affected. The fact that you don't have a problem on your system is immaterial, inconsequential, and pointless. This issue is related to some Intel chipsets with a Raid controller, especially the P45/G45 series, and then only certain revisions.

If you had read and completely quoted my post, you would have noticed that I said if you are having problems with particular hardware, that needs to be reported.  If you had specified the particular chipsets affected, OldFred may have been able to do some research more quickly.

Without knowing what chipset you were talking about, indicating that I'm having no problems was a perfectly fair answer, as it was as general as your statements to that point.

"We" didn't create a problem, "we" aren't hiding anything and "we" can't speak for Canonical.  "We" don't know every detail of everything.  Someone may know exactly what was "done".  Maybe it's just not us chickens.

Sometimes a slightly less demanding and accusatory tone is in one's best interest when seeking help.

---

### Post by MrNovi on 2012-09-18
That one doesn't pertain to my situation. The bug reports for the problem I am having, and there are several of them are not listed under ICH10R. It;s been awhile since I last searched for them and don't remember exactly what search parameters I used. Since I don't have access to the computer I was using when I searched for them at the moment I can't point to the specific bug reports, but they are there and were still unresolved when I made the original post in this thread.

Thanks for looking though.

---

