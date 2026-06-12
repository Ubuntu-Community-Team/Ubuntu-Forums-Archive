---
title: "Are Ubuntu file systems junk, or am I missing something?"
date: 2010-07-06
forum: General Help
---

### Post by BillRebey on 2010-07-06
I've been performing power-recovery testing on several Ubuntu installations, and the results are horrendous.  

I've used 9.04 with EXT3, and 9.10 and 10.04 with EXT4, and all yield the same results:  the file systems corrupt very quickly, rendering the computer unbootable, which means that it's impossible to use Ubuntu for anything but a hobbyist installation.  I can't have a whole PC bricked just because the lights went out!

I'm mounting my root EXT3 systems with options:
```
(rw,noatime,nodiratime,errors=remount-ro,data=journal,barrier=1)
```

I'm  mount my root EXT4 systems with options:
```
(rw,noatime,nodiratime,norelatime,nodelalloc,barrier=1,errors=remount-ro)
```

Are these not the "bullet-proof" mounting options?  Is there a better way to mount a file system so that it can't become corrupted, or are Ubuntu's file systems just not intended to be reliable?

Thanks to any and all for any help in this area.  I'm very frustrated right now, and am not looking forward to having to switch platforms just to get the most basic and fundamental of reliability features:  I just want the O/S to work!

---

### Post by Strongman332 on 2010-07-06
what hard drive are you using some wd hard drives only work well ntfs and fat

as for the reliability, ext has been considered very stable. also i personally have no trouble.

of course this could be hardware error as well, you may get more help if we know what you are running.

---

### Post by Yarui on 2010-07-06
I don't really know what is causing your problems, but I have never had an ubuntu filesystem die.  To blame this problem on the OS seems a bit unreasonable.  Instead of telling us that the filesystems are becoming corrupt maybe you can give a bit more detail about the symptoms you are experiencing.  Tell us how long the filesystem worked before dying, what it started doing that was out of the ordinary and what you have tried to do to fix it.  If you give enough information someone may be able to help you out.

---

### Post by AlanR8 on 2010-07-06
The Web runs on *nix servers so something would appear to be right on millions of servers.....

---

### Post by imbjr on 2010-07-06
I take it you have regular power outages? We used to have them at home, until we replaced the freezer. During this period I had ext4 partitions installed with the default mount options. I think I only saw one loss of data and that was when ext4 was first introduced to Ubuntu and not the default - i.e. it probably wasn't considered stable enough for everyone to start using. I think I may have had one or two ext3 partitions too, but do not recall any data loss with them.

If you are having regular outages, you may need to get a electrician in - as we did, or get a UPS. However, if you live some place where the power regularly dips out for everyone, I'm not sure what I can suggest that wont cost a small fortune.

---

### Post by snowpine on 2010-07-06
Interesting thread. Can you boot the computer in "recovery mode"?

---

### Post by GreenN00b on 2010-07-06
I have regular power outages because of the environment and I never had lost a file and the system always boots.
Details: ext3 partitions, over 100 power outages in the last 2 years, personal computer.

---

### Post by BillRebey on 2010-07-06
Thanks for the speedy replies, all!

***_Imbjr_***, you misunderstood my post.  I&#8217;m not suffering frequent power outages, but rather am *_testing power recovery of Ubuntu_*.  I.e., I&#8217;m intentionally power-failing the machines for the specific reason of evaluating the durability of the file system and the O/S in general.  Solutions such as a UPS, etc. are not the issue.  The specific thing being tested is Ubuntu's response to power failure, and I&#8217;m getting terrible results.  I&#8217;m getting very high failure rates &#8211; on the order of 1 in 100 power cycles;  maybe even higher. 

***_Strongman332_***, I&#8217;m using two different drives:
-	One is a 64GB SSD 1.8&#8221; uSATA drive that came with the PC.  It&#8217;s only branded &#8220;Super Talent&#8221;, model FUM64G218H, so I don&#8217;t know who the &#8220;real&#8221; manufacturer is (this &#8220;Super Talent&#8221; thing sounds like a Chinese rebrand, to me).   The PC that it&#8217;s in is a BIS-6620 Atom-based PC from Habey ([http://www.habeyusa.com/products_show.php?id=207#Menu=ChildMenu112](http://www.habeyusa.com/products_show.php?id=207#Menu=ChildMenu112)).  
-	The other is a 2.5&#8221; 160GB Hitachi SATA mechanical drive, model HTS543216L9A300, that is in an Atom-based PC called a Fit-PC2 ([http://www.fit-pc.com/web/](http://www.fit-pc.com/web/)).  

***_Yarui_***, the symptoms are that once the file system gets corrupt, the boot process hangs at fsck.  I  currently have two machines &#8211; (both Ubuntu 10.04 and EXT4) in the corrupted state.  Related diagnostics displayed are as follows:

First machine:
```
fsck from util-linux-ng 2.17.2
/dev/dsa1: Inode 1190386  has an invalid extend node (blk 7899166, lblk 0)
/dev/sda1:  UNEXPECTED INSONSISTENCY; RUN fsck MANUALLY.
	(i.e., without &#8211;a or &#8211;p options)
mountall: fsck / [279] terminated with status 4
mountall: Filesystem has errors: /

```
Second machine:
```
fsck from util-linux-ng 2.17.2
/dev/sda1  contains a file system with errors, check forced.
i/dev/sda1: Duplicate or bad block in use!
/dev/sda1: Multiply-claimed block(s) in inode 1180437: <list of 12  block numbers>
/dev/sda1: Multiply-claimed block(s) in inode 1180489: <list of 45 block numbers>
/dev/sda1: Multiply-claimed block(s) in inode 1180572: <list of same 45 block numbers as above>
/dev/sda1: Multiply-claimed block(s) in inode 1966094: <list of same 12  block numbers as first entry>
/dev/sda1:  UNEXPECTED INSONSISTENCY; RUN fsck MANUALLY.
	(i.e., without &#8211;a or &#8211;p options)
mountall: fsck / [279] terminated with status 4
mountall: Filesystem has errors:  /
```

Running fsck manually as suggested is irrelevant,  as the PC is considered "bricked" at this point.  The user will either return it as defective, or will issue a service call.  The PCs run headless (no monitors or user i/o devices attached) so these diagnostics will never be seen.  *Correcting* the corrupted file system is not an issue;  *_preventing_* it from getting that way is all I care about.  

As for how long the file system worked before breaking, I can probably get one to break within an hour or two of re-imaging the PC.  

Given what I know now, *it just looks to me like the file system is very fragile and can't be interrupted by a power failure*.  

I very much want to use Ubuntu as my development and distribution platform, but I can't deploy an industrial-quality product on this platform if I can't rely on the file system to remain in-tact across power failures.    

Have I used the proper mount options (as stated in my original post) to get the most durable file system Ubuntu has to offer, or are there other mount options that I can use to make the system more reliable?

Regarding your observation that Ubuntu's file  systems have been reliable for you, I don't doubt that in the least.  I haven't seen any trouble at all with any Ubuntu file system that wasn't subjected to power interruption.  Remember, though, that the very  thing that I'm testing is power-recovery and power-fail safety of the file system.  My test case is to run 10 instances of a multi-threaded program that has a writer thread that writes to a disk-based queue every 100 milliseconds, and a readerr  thread that reads from the queue and drains it at startup plus every 10 seconds thereafter;  there is also lots of diagnostic logging that goes on to a text file.  The idea is simply to get the O/S and file system plenty busy, then pull the plug.  I'm  guessing that if you emulated this kind of test, you'd get the same results.

***_AlanR8_***, I was unable to glean any usable or helpful information from your post, and you requested no further information that might better illuminate the problem. 


Thanks again, all, for any further assistance.  **Any and all help is appreciated!!**

---

### Post by BillRebey on 2010-07-06
Snowpine,

No, I can't boot to recovery mode.  I get the same errors before recovery mode even gets started.

I don't care at all, though, about recovering from this error.  Once the file system is corrupted, the the PC is considered bricked and my clients will consider them "junk", and will either return them to me as "broken", or a service call will be generated.  The "repair" is simply to re-image the PC.  

The key is to PREVENT this from happening in the first place.

Any ideas how to make either EXT3 or EXT4 work reliably and not crumble under the strain of power failure?

---

### Post by snowpine on 2010-07-06
> **BillRebey said:**
> Running fsck manually as suggested is irrelevant,  as the PC is considered "bricked" at this point.  The user will either return it as defective, or will issue a service call.  The PCs run headless (no monitors or user i/o devices attached) so these diagnostics will never be seen.  *Correcting* the corrupted file system is not an issue;  *_preventing_* it from getting that way is all I care about. 

This comment makes no sense to me. fsck is the Linux tool for recovering your filesystem after a power outage (among other things). "My Linux filesystem is corrupted, but I don't want to run fsck" is like saying "my screws are loose, but I don't want to use a screwdriver." :) 

The alternative is that the system boots OK, there is no warning, data is potentially lost without you knowing about it. Maybe it is possible to enable this behavior in Ubuntu if that's what you need for the project, I really don't know. 

Basically you are asking "Are phillips screws junk or am I missing something?" and the answer is "Use the phillips screwdriver that came with your toolbox."

---

### Post by BillRebey on 2010-07-06
GreenN00b, thanks for jumping in!

0 failures in 100 power cycles with EXT3 is not unexpected.  On one EXT3 test, I got about 385 good power cycles until a failure.  (EXT4 seems to fail much quicker than that - on the order of 1 in 100 in my testing).

1 failure in 400 means that if I have a client whose facility has 400 installed units, one of them will be bricked EVERY DAY!  If I have 10 clients that size, I'm looking at 10 bricked units a day, and 10 service calls, not to mention the lost data.  That's clearly not a good business model.

Also note that your own experience is not likely anywhere near as taxing as my testing.  My test case makes the disk very busy, with 20 threads across 10 processes reading to and writing from files.  If I uncover a bug that permits 1 failure in 500 power cycles, I'd expect that an average home desktop user, under typical desktop use and load patterns, might uncover that same bug in 50,000 power cycles, or maybe many, many more.  The typical desktop PC just isn't very busy.

---

### Post by imbjr on 2010-07-06
> **BillRebey said:**
> Thanks for the speedy replies, all!
***_Imbjr_***, you misunderstood my post.  I’m not suffering frequent power outages, but rather am *_testing power recovery of Ubuntu_*.  I.e., I’m intentionally power-failing the machines for the specific reason of evaluating the durability of the file system and the O/S in general.  Solutions such as a UPS, etc. are not the issue.  The specific thing being tested is Ubuntu's response to power failure, and I’m getting terrible results.  I’m getting very high failure rates – on the order of 1 in 100 power cycles;  maybe even higher. 


OK so from your tests you appear to be getting results that do not meet your expectations. However, if you are not in a scenario where power-offs do occur, I'm not sure if the issue of power recovery is one worth testing. If you were in that frequent power-off situation, then I'd say that UPS was indeed a possible solution.

---

### Post by BillRebey on 2010-07-06
Haha!  I see where you're coming from, but I think you've misinterpreted my postion, or perhaps I've penned it poorly.  Accept my apologies and let me try again...

I have no aversion to fsck having to run, and if the file system is built such that fsck is required after a power failure, then that's just great - so long as it can run automatically and correct the file system without user intervention.  My problem is that I'm deploying "black boxes" that have no user interfaces, and I simply can't have them breaking all the time.

Your philips screw analogy, however, isn't very good.  You're right - if Ubuntu's file system is alanagous to philips screws, then yes, I am indeed asking "are philips screws junk or am I missing something", which equates to "are philips screws junk or am I installing them wrong from the onset". 

If your lug nuts fell of your tires every time you had to break hard for an animal or an unexpected stop sign around a corner, and your auto maker said "Oh, that's what the lug wrench is for!  Just re-install the nuts after any hard braking, and you'll be OK", would you accept that answer?  That's what you're suggesting I accept as an answer for Ubuntu's file system becoming corrupted.

I'm guessing that if your lug nuts did indeed fall off regularly, you'd not be asking around for instructions on how to use a lug wrench, but rather you'd be asking "are lug nuts junk, or am I missing something?"

You see, what I'm suggesting is that Ubuntu's file systems *shouldn't break AT ALL*.  I understand that things like delayed writes and buffering schemes will certainly have some exposre to power failure, the file system should have (and I suspect DOES HAVE) a mode that makes it reliable ALL THE TIME.  

So maybe the real question is: 

***"Is there some way to mount a file system in Ubuntu - either with EXT3 or EXT4 (or anything else) - that will allow the file system to ramain intact and uncorrupted across power failures?"***

Does that sound like a more reasonable question to you?

Thanks again for any help.

---

### Post by ks07 on 2010-07-06
I don't know the slightest about making ext3/4 more reliable, but have you done similar tests with other filesystems? It seems to me that corruption is inevitable when you're writing that much data during a power cycle, so instead of questioning ext3/4, you might want to compare them to others to see if they really are junk or the best of a 'bad' bunch. ;)

And obviously, if you want more security against corruption, ext3 will be the way to go due to its increased journaling. :p

---

### Post by BillRebey on 2010-07-06
Imbjr,

The power failure tests are being performed because the production will indeed be subjected to regular power failures, becuase they will be powered with a battery pack, and users will regularly allow the batteries to run down.  This is unavoidable.  I am delpoying inexpensive, low-powered units, and the budget does not allow for UPS hardware with signalling to the attached PC to tell it taht the power is about to go out, etc.  

I chose Ubuntu for this project becuase I thought it was robust and durable, and now that I've seemingly discovered otherwise, most of the answers I'm getting are along the lines of "if it hurts when you do X, don't do X".  

I'm really looking to CORRECT the problem, not avoid it.  The  problem is that the way I have Ubuntu set up, the file system is unreliable and corruptible and can not reliably withstand being interrupted by a power outage.  

I'm trying to find a way to make the file system reliable, durable, and robust, such that it can withstand a power interruption.  

If this goal is simply not attainable, and the file systems that Ubuntu can employ are simply not robust enough to withstand power failures and recover without user intervention, then would a developer of the filesystems, or someone equally well-versed on the issue and "in the know", please tell me so that I can abandon my efforts take another approach?

I have a very hard time believing, though, that Ubuntu's file systems are that fragile.  **I suspect that I'm not using them correctly**, and that if I properly mount and set up a file system, it will indeed perform as reliably as I require.

Once again, thanks for any input or assistance.

---

### Post by snowpine on 2010-07-06
> **BillRebey said:**
> If your lug nuts fell of your tires every time you had to break hard for an animal or an unexpected stop sign around a corner, and your auto maker said "Oh, that's what the lug wrench is for!  Just re-install the nuts after any hard braking, and you'll be OK", would you accept that answer?  That's what you're suggesting I accept as an answer for Ubuntu's file system becoming corrupted.

I'm guessing that if your lug nuts did indeed fall off regularly, you'd not be asking around for instructions on how to use a lug wrench, but rather you'd be asking "are lug nuts junk, or am I missing something?"

That is a good counter-analogy. :) I am subscribed, curious to hear some different perspectives on the topic.

---

### Post by bobcollard on 2010-07-06
In any similar situation with a laptop running on pure battery the computer can be set to shutdown safely just before (0) power is reached, this may be a solution, it's in the Power Manager.  I run Xubuntu 9.10 and have run my battery down many times this way with no effect on the system.

---

### Post by BillRebey on 2010-07-06
KS07,

As for your comment about EXT3 vs. EXT4, I didn't have significantly better luck with EXT3 than I do with EXT4.

Regarding comparing Ubuntu's performance to other O/Ses, I get where you're coming from, but right now it's irrelevant if other file systems are "better or worse".  This isn't a contest - I just need the thing to work.  If ALL O/Ses perform just as poorly as Ubuntu, that doesn't solve my problem.  I'm looking for solutions, not a security blanket.

I get the feeling that everybody is very defensive of Ubuntu.  I'm not interested in throwing stones...I'm interested in the file system working correlty and finding a solution to my problem.  

As far as comparing to other file systems, if ALL file sytems in the world work this poorly, then "yes", they are ALL corruptible and are simply junk in my eyes, and someone might see this as an opportunity to invent a file system that's realible.  

However, since you asked, "yes", I have done similar testing wtih NTFS on a Windows XP installation on identical hardware, and afterr 1000 power cycles, have still not bricked a PC.  

**I do not want to use Windows**, though....I want to use Ubuntu!  I love Unix/Linux/Ubuntu, and really want this to work.   

**I'm not trying to kick anyone's dog...I'm trying to find a solution**.  I'm on your side, folks!  I'm just more pragmatic and less emotional than some others seem to be.  

I've identified a great deficiency in the product, and am looking for a way to correct the problem, that's all.

I'm really surprised that I'm not hearing more replies like "Holy Mackerel!  Are you saying that Ubuntu can be rendered unbootable just by tunring off the PC??!!  Tht's terrible!  Sounds like WIndows 95! We can't have that!  Let's find out why and get it fixed..."  

All I'm hearing, though, is "be nice to Ubuntu!".

Once again, thanks to all who are reading and participating.  I appreciate any direction in finding a solution to this problem.

---

### Post by bobcollard on 2010-07-06
We crossed paths while writing the last entry, see above.

---

### Post by BillRebey on 2010-07-06
bobcollard,

Thanks for the input, and you're quite right - a laptop-like solution does account for this sort of thing by attempting an orderly shut-down when power is failing, as do mobile phones, PDAs, etc.

However, I don't have that luxury in this application.  The PCs in use are small (about the size of 1/2 a paperback book), inexpensive, durable single-board computers without built-in batteries or any user interface (no monitor, kbd, mouse, etc.).  They are to run unattended in an industrical/commercial environment, and the software must be 100% reliable to the extent that the hardware continutes to work correctly. 

They have an external battery that will eventually just "quit" on them.  Furthermore, even if they did have a fancy, intelligent, UPS-style battery pack that would notify the PC of impending power failure, users will regularly unplug them anyway. 

**The correct solution is a file system that doesn't break in the first place**, and my question is simply _*"how do I get a Ubuntu file system to work reliably across power failures?"  *_

I simply need an operating system solution that is rock-solid reliable, like something that you'd consider installing to control an automobile, or an airplane, or a medical device;  I'm pretty sure you wouldn't want your car to be run by an Ubuntu box, knowing that if you changed the batterry in your car, abruptly interrupting Ubuntu, the car might not start again because Ubuntu was waiting for you to "RUN FSCK MANUALLY...".

Ubuntu MUST have a "high reliability" configuration of some sort, doesn't it??!!

Anyone know how to crack this?

---

### Post by bobcollard on 2010-07-06
> **BillRebey said:**
> bobcollard,

Thanks for the input, and you're quite right - a laptop-like solution does account for this sort of thing by attempting an orderly shut-down when power is failing, as do mobile phones, PDAs, etc.

However, I don't have that luxury in this application.  The PCs in use are small (about the size of 1/2 a paperback book), inexpensive, durable single-board computers without built-in batteries or any user interface (no monitor, kbd, mouse, etc.).  The are to run unattended in an industrical/commercial environment, and the software must be 100% reliable to the extent that the hardware continutes to work correctly. 

They have an external battery that will eventually just "quit" on them.  Furthermore, even if they did have a fancy, intelligent, UPS-style battery pack that would notify the PC of impending power failure, users will regularly unplug them anyway. 

The correct solution is a file system that doesn't break in the first place, and my question is simply "how do I get a Ubuntu file system to work reliably across power failures?"
I have worked over the last twenty five years with MSDOS, Windows, Unix, BSD and Apple computers and I can tell you the solution is already there, but, you need the computer to monitor the battery in some manner.  Without feedback you are dead in the water.

---

### Post by bobcollard on 2010-07-06
One further comment.  NASA has many small computers instead of one large one on their crafts.  Why?  Because one system may have a redundant system or it is easier to reinstall the system of one small computer in case of a power surge or a damaged HD than lose everything.  They have the same basic problem, systems crash, you replace them.  If you can figure out how to fix them in another way, you could go to work for them.  Good luck.

---

### Post by amauk on 2010-07-06
No filesystem can completely eliminate data corruption from power outages
although some filesystems are better suited to power outages than others (ReiserFS & XFS are better suited)

It's just a fact of life that filesystem performance is maintained by making them asynchronous
When you write something to disk, it may not actually be written instantaneously
Instead, many small writes are batched together and done as a single, larger write

If you can accept horrendous performance, then I'm sure there's a way to make any filesystem work synchronously

You seem to be trying to solve a physical issue with software, but there's better ways to solve the issue

If you are expecting there to be power issues, then supply your systems with a small battery powered failsafe system.
When power fails, battery kicks in, commits all writes, parks HDD heads and shuts down the system

---

### Post by warfacegod on 2010-07-06
I think what you are asking, in one part, is impossible. To reduce the first part of your question down to its basic idea

*Can I take these electronic devices, that run on electricity, and kill their power while they are doing things with that electricity and have them never break?*

The answer is no. And absolutely not when user idiocy will be involved. Not with our current understanding of the sciences anyway.

Now the second part of your is:

*Can I, at least, take those very same electronic devices and greatly reduce the risk of them breaking if I kill the power while they are doing something?*

The answer to this question is yes. How to go about doing that I don't know. Sorry to say.

Let me ask you this. Have you run your tests with Ubuntu installed with its Standard boot options, if there is such a thing? And if so, have you compared your results with the boot options you have selected?

---

### Post by giddyup306 on 2010-07-06
Can I make a suggestion? If the ext3/4 filesystem is in question, then why not opt for something else like NTFS or FAT 16/32 (I hate the 4 GB limit tho)?  I have 4 harddrives that I use with Ubuntu.  The one that is inside my PC is NTFS.  Two of the externals are FAT 32 as well as all my flash drives, and I have one that is ext4.  For the record the ext4 seems to have the most amount of problems.

---

### Post by warfacegod on 2010-07-06
I've never had issues with ext3 or 4.

NTFS gave me BSOD dozens of times.

---

### Post by Ocxic on 2010-07-06
.

---

### Post by MCVenom on 2010-07-06
Hey OP, have you looked into BTRFS? That may provide a more corruption resistant filesystem, but I don't know for sure.

---

### Post by sille777 on 2010-07-06
I hope you don't mind if a noob and an outsider chimes in a bit.

It seems There is a confusion on Ubuntu being the problem.  At least I was confused.

Ubuntu is a OS that can be installed on or utilize many different File systems, right?. So if a particular file system is not passing a certain benchmark for reliability in a file system, how is that the fault of the OS, or any OS?

Just trying to learn and understand.

---

### Post by warfacegod on 2010-07-06
> **sille777 said:**
> I hope you don't mind if a noob and an outsider chimes in a bit.

It seems There is a confusion on Ubuntu being the problem.  At least I was confused.

Ubuntu is a OS that can be installed on or utilize many different File systems, right?. So if a particular file system is not passing a certain benchmark for reliability in a file system, how is that the fault of the OS, or any OS?

Just trying to learn and understand.

You are partially correct. The filesystem and the OS are independent entities. However, the filesystem can be affected by how the OS deals with a power loss. Or the power loss can harm the filsystem, there for harm the OS. I can't really give you a more detailed explanation than that.

---

### Post by MooPi on 2010-07-06
The solution is a simple one. Either prepare a thumb drive with a minimal install of Ubuntu or have a Live CD available to use. After one of your tests shows a drive is corrupted boot from your removable media and preform ```
e2fsck -f -p /dev/sda1
``` The drive designation to whatever yours is labeled.
This will force the check and make automatic corrections. Review the man pages for e2fsck or --help file for further info.
Your test procedure is faulty. Consider your forcing these power cycles on one machine, where the stress is loaded entirely on a singular files system. By comparison the 400 clients would not have this failure rate due to the lack of stress per unit.For your test to express the actual failure rate for 400 machines you'd need to increase the number of units tested.

---

### Post by Yarui on 2010-07-06
> **BillRebey said:**
> ***_Imbjr_***, you misunderstood  my post.  I’m not suffering frequent power outages, but rather am *_testing  power recovery of Ubuntu_*.  I.e., I’m intentionally  power-failing the machines for the specific reason of evaluating the  durability of the file system and the O/S in general.  Solutions such as  a UPS, etc. are not the issue.  The specific thing being tested is  Ubuntu's response to power failure, and I’m getting terrible results.   I’m getting very high failure rates – on the order of 1 in 100 power  cycles;  maybe even higher. 

***_Yarui_***, the symptoms are that once the file system  gets corrupt, the boot process hangs at fsck.  I  currently have two  machines – (both Ubuntu 10.04 and EXT4) in the corrupted state.  Related  diagnostics displayed are as follows:

Running fsck manually as suggested is irrelevant,  as the PC is  considered "bricked" at this point.  The user will either return it as  defective, or will issue a service call.  The PCs run headless (no  monitors or user i/o devices attached) so these diagnostics will never  be seen.  *Correcting* the corrupted file system is not an issue;  *_preventing_*  it from getting that way is all I care about.  

As for how long the file system worked before breaking, I can probably  get one to break within an hour or two of re-imaging the PC.  

Given what I know now, *it just looks to me like the file system is  very fragile and can't be interrupted by a power failure*.  

I very much want to use Ubuntu as my development and distribution  platform, but I can't deploy an industrial-quality product on this  platform if I can't rely on the file system to remain in-tact across  power failures.    

Have I used the proper mount options (as stated in my original post) to  get the most durable file system Ubuntu has to offer, or are there other  mount options that I can use to make the system more reliable?

Regarding your observation that Ubuntu's file  systems have been  reliable for you, I don't doubt that in the least.  I haven't seen any  trouble at all with any Ubuntu file system that wasn't subjected to  power interruption.  Remember, though, that the very  thing that I'm  testing is power-recovery and power-fail safety of the file system.  My  test case is to run 10 instances of a multi-threaded program that has a  writer thread that writes to a disk-based queue every 100 milliseconds,  and a readerr  thread that reads from the queue and drains it at startup  plus every 10 seconds thereafter;  there is also lots of diagnostic  logging that goes on to a text file.  The idea is simply to get the O/S  and file system plenty busy, then pull the plug.  I'm  guessing that if  you emulated this kind of test, you'd get the same results.

If you are stress testing the system then it makes much more sense that you seem to be having trouble with it.  I know nothing of the development of these filesystems so I can't vouch for how reliable they are in this sense.  Under normal use you are unlikely to have to worry about this but if you are looking to find the absolute most stable file system then maybe Ext 3/4 just aren't the right way to go.  They are far from the only available file systems for you to choose from in Ubuntu, though.  If you really want to stick with Ubuntu and find the Ext 3/4 file systems unacceptable, then you may find some of the others more reliable.

Preventing power outages is always good, but power outages do happen, so I suppose I can understand why you want to be safe.  Just as power outages do happen, though, total system failures do happen and regardless of what you are using you should be prepared to deal with them in the event that they do happen.  No matter how stable the file system you choose is, you shouldn't let that give you a false sense of security.

Regardless of which file system you choose, I really doubt your customers are going to be coming to you every day saying that the file systems are crashing.  That just doesn't happen that often in real world situations.

> **BillRebey said:**
> I've identified a great deficiency in the product, and am looking for a way to correct the problem, that's all.

I'm really surprised that I'm not hearing more replies like "Holy Mackerel!  Are you saying that Ubuntu can be rendered unbootable just by tunring off the PC??!!  Tht's terrible!  Sounds like WIndows 95! We can't have that!  Let's find out why and get it fixed..."  

All I'm hearing, though, is "be nice to Ubuntu!".
There are probably several reasons that you aren't hearing more shocked responses.  What you are doing is stressing the system to a breaking point that no one who has responded here has ever reached on their own, and likely never will.

This isn't probably the right crowd to go to if you want your experience to make a difference, because the Ubuntu community doesn't maintain any of the mentioned file systems.  If you really want to make a difference in the quality of the Ext 3/4 file systems (and yes, it is quite possible that you could), you should probably try to find the developer community for those filesystems and talk to them about it.  That is the group that will be able to give you real feedback on your concerns.  If what you are experiencing really is a drawback they will probably be happy to hear about your experience.  They may not even realize this issue exists.

---

### Post by Seanlol on 2010-07-06
There is no possible way to stop a file system from corrupting when its power continually fails. If it happens regularly, every single file system will fail eventually. Especially if you happen to be in the middle of a write, etc.

---

### Post by QIII on 2010-07-06
It might be instructional for you to point out a file system that can, while in the middle of read/write cycles (especially when system files are involved), recover flawlessly from an unexpected power failure.

Can you provide us with some comparative analysis -- a baseline for your expectation?

I suspect it would be a quite rare thing indeed, since the entire industry invests heavily in the insurance of un-interruptible power supplies and power failover systems.  Whoever was the purveyor of that technology would surely be shouting its virtues from the rooftops.

---

### Post by KdotJ on 2010-07-06
Off-topic (apologies) but this is a really great thread

---

### Post by ScarletWyvern on 2010-07-06
Wait, let me get this straight.

OP is complaining about a *1% or lower failure rate?*

---

### Post by QIII on 2010-07-06
In my former line of work, a 1% failure rate might have led to significant loss of life.

---

### Post by McRat on 2010-07-06
I am I reading this right?

You kill the power during a write cycle deliberately and the directory structure is unsound when you're though?

Good luck with that.

---

### Post by mobilediesel on 2010-07-06
> **BillRebey said:**
> ***"Is there some way to mount a file system in Ubuntu - either with EXT3 or EXT4 (or anything else) - that will allow the file system to remain intact and uncorrupted across power failures?"***

I have two desktop computers using the EXT3 file system. The area where I live has fairly unreliable power. Every time the wind is above 40 miles per hour or more than 10 minutes, the power goes out for a couple hours. Then power comes back at about half-voltage (all light bulbs dim) for a couple days then DTE Energy finally gets it back up.

I have not seen any data corruption on either one of my computers after any of the power failures. I haven't done anything to the way Ubuntu mounts the drives, just left it the way it was set up after installation.

---

### Post by Vaidok on 2010-07-06
I do not know much about this stuff but why did you choose data=journal?

You could try data=ordered or data=writeback. These do not write as much data so they are faster.

---

### Post by ramjet_1953 on 2010-07-07
I'm trying to look at this subject objectively and the thing that keeps hitting me between the eyes is that the poster of this thread maybe needs to look at his own hardware design.

I understand that the black boxes need to be small and low-cost -- but if they are not working under regular power outage conditions, might I suggest that a re-think of that hardware design needs to be made?

It is all well and good to blame a file system, but when industry accepted methods of protecting a system from power failure have not been adhered to, i.e. a UPS, where does the fault lie?

Regards,
Roger:)

---

### Post by capscrew on 2010-07-07
> **BillRebey said:**
> ...
So maybe the real question is: 

***"Is there some way to mount a file system in Ubuntu - either with EXT3 or EXT4 (or anything else) - that will allow the file system to ramain intact and uncorrupted across power failures?"***

Does that sound like a more reasonable question to you?

...

Several times in this thread you have come close to a resolution.

I think if you think about it you will see that this is not a matter or file systems or even operating systems per se.  More to the point is data persistence on volatile media during power failure.  By volatile media I mean RAM, HDD's and SDD's.  This persistence will never happen 100% of the time.  Volatile media by definition needs power to hold instructions in in RAM during operation and cached data must be written to to disk during shutdown.

The failure you are measuring is really the journaling routines of EXT3 and 4.  The are different, hence the differences you have observed.  Both filing systems are based on EXT2 which has no journaling at all.  Hmmmmm... 

The best way to resolve this problem would be to embed the OS (firmware) on non-volatile media and store the data only on HDD or HDD.  Short of that I would at least separate the data from the OS an maybe run EXT on the /boot FS.  In this way data corruption would not be a cause a failure to boot.

---

### Post by Yarui on 2010-07-07
> **ramjet_1953 said:**
> I'm trying to look at this subject objectively and the thing that keeps hitting me between the eyes is that the poster of this thread maybe needs to look at his own hardware design.

I understand that the black boxes need to be small and low-cost -- but if they are not working under regular power outage conditions, might I suggest that a re-think of that hardware design needs to be made?

It is all well and good to blame a file system, but when industry accepted methods of protecting a system from power failure have not been adhered to, i.e. a UPS, where does the fault lie?

Regards,
Roger:)
Good point.  This description of needing the machines to be small and low-cost makes me think of the saying that you can get things good and cheap but they won't be fast,  you can get things cheap and fast but they won't be good, and you can get things good and fast but they aren't going to be cheap.

---

### Post by giddyup306 on 2010-07-07
> **Yarui said:**
> Good point.  This description of needing the machines to be small and low-cost makes me think of the saying that you can get things good and cheap but they won't be fast,  you can get things cheap and fast but they won't be good, and you can get things good and fast but they aren't going to be cheap.

That's a good point, and there's a saying in the racing world:

Cheap and reliable won't be fast.
Fast and cheap won't be reliable.
Reliable and fast won't be cheap.  


To get back on topic I think this has more to do with the harddriive itself failing, not any of the filesystems.

---

### Post by UltraZone on 2010-07-07
From a purely scientific and statistical perspective, your testing is extremely limited and conclusions should basically be thrown out.  Garbage in, garbage out applies also to the testing world not just the simulation world.  Now, from an engineering standpoint you need to design in a _fail-safe_ system, as previous posters have commented, a back-up power system that will allow a safe shutdown when the main power comes off-line.  This is the only way.

---

### Post by philinux on 2010-07-07
How about forcing fsck to run automatically every boot.

Using.

sudo tune2fs -c 1 /dev/sda1

Or running a script at boot up to perform

sudo touch /forcefsck

That way even if power fails fsck should run automagically without user intevention.

Or maybe there's a way to get fsck to run with a default -y option on a failed file system. May have to roll your own version and compile it.

OP needs to test this.

See man tune2fs

---

### Post by JoelOl75 on 2010-07-07
Brings up a good question.  WHY does Ubuntu tell you that the filesystem is corrupted and fsck needs to be run manually.  Why doesn't it just run fsck by itself, answering "y" to any prompts and then reboot when done?

Noobs won't be able to figure this out on their own. The default behavior should be changed IMO.

---

### Post by quinnten83 on 2010-07-07
> **BillRebey said:**
> Imbjr,

The power failure tests are being performed because the production will indeed be subjected to regular power failures, becuase they will be powered with a battery pack, and users will regularly allow the batteries to run down.  This is unavoidable.  I am delpoying inexpensive, low-powered units, and the budget does not allow for UPS hardware with signalling to the attached PC to tell it taht the power is about to go out, etc.  

I chose Ubuntu for this project becuase I thought it was robust and durable, and now that I've seemingly discovered otherwise, most of the answers I'm getting are along the lines of "if it hurts when you do X, don't do X".  

I'm really looking to CORRECT the problem, not avoid it.  The  problem is that the way I have Ubuntu set up, the file system is unreliable and corruptible and can not reliably withstand being interrupted by a power outage.  

I'm trying to find a way to make the file system reliable, durable, and robust, such that it can withstand a power interruption.  

If this goal is simply not attainable, and the file systems that Ubuntu can employ are simply not robust enough to withstand power failures and recover without user intervention, then would a developer of the filesystems, or someone equally well-versed on the issue and "in the know", please tell me so that I can abandon my efforts take another approach?

I have a very hard time believing, though, that Ubuntu's file systems are that fragile.  **I suspect that I'm not using them correctly**, and that if I properly mount and set up a file system, it will indeed perform as reliably as I require.

Once again, thanks for any input or assistance.
 You know, I think this is a problem you need to contact developers with and not people in the forum. Our knowledge here is mostly as regular users and maybe power-users, not as stress-testers. I simply believe that we can't help you, because even if the problem could be corrected, then I don't think that here is the place to find a party to do it.

---

### Post by snowpine on 2010-07-07
Isn't this situation one of the things RAID is for?

---

### Post by QIII on 2010-07-07
I like the idea of the embedded OS and separate data.

But the data would still stand to be corrupted in an unexpected power failure.  In this case, the OS might start, but the data needed to continue the task might not be available.

Say we look at ZFS (and pretend for a moment that the conflicting licensing issues that have kept ZFS from being ported to Linux satisfactorily don't apply).  ZFS has the ability to maintain periodic snapshots.  However, that might lead to poor performance during operation when that is taking place.  Furthermore, it takes power to do that.  Performance and power consumed would seem to rule this out in the OP's case.

It appears to me that two things must be accomplished:

1.  State must be saved as necessary.

2.  Writes must be committed as necessary.

I think this would be true regardless of the OS or file system.

To accomplish 1 and 2, power must be supplied long enough for the "worst-case" length of time it would take for both tasks to finish.

The options for a very small unit would likely be either a small "coin" battery or some built-in capacitance.  The sole purpose of each/either (maybe both for double protection) would be to provide power for that brief interval.

This is more a hardware issue than an OS/File System issue.

---

### Post by CharlesA on 2010-07-07
> **JoelOl75 said:**
> Brings up a good question.  WHY does Ubuntu tell you that the filesystem is corrupted and fsck needs to be run manually.  Why doesn't it just run fsck by itself, answering "y" to any prompts and then reboot when done?

Noobs won't be able to figure this out on their own. The default behavior should be changed IMO.

Personally I would rather have it ask me before automatically making changes to the file system. It does that now. If it just did it automatically, how would you know if you lost data due to file corruption that was unrecoverable?

> **snowpine said:**
> Isn't this situation one of the things RAID is for?

RAID doesn't prevent data corruption from power outages, it only prevents data loss when a drive dies (depending on how it's set up)

My thoughts on what the OP is trying to do: Get a UPS that connects to the box and train the users not to screw with the power cables. I really don't think that any file system that is being written to will handle any sort of repeated power loss. If you set the root file system as read only and store the data elsewhere, that might work, but it's a hell of a lot of work tbh.

---

### Post by capscrew on 2010-07-07
> **QIII said:**
> I like the idea of the embedded OS and separate data.
For mission critical this is the only  way to go and even this is not 100%> 
But the data would still stand to be corrupted in an unexpected power failure.  In this case, the OS might start, but the data needed to continue the task might not be available.
This is true, but...
The OP did not state what the data was or even if it was stored only on the device.  As he said: *[COLOR="Blue"]**My problem is that I'm deploying "black boxes" that have no user interfaces, and I simply can't have them breaking all the time"**[/COLOR]*. It is possible that there is little of no critical data held in the box.  I can envision a stream of data to a central site.  

The separation of the data is an enevetable outcome of the fact that the OS would be immutable as firmware.  If there is data held in the device and it goes down you can remotly ssh to the box and fsck the data parition.> 

Say we look at ZFS (and pretend for a moment that the conflicting licensing issues that have kept ZFS from being ported to Linux satisfactorily don't apply). 

Nextenta does a great job of integrating ZFS with Debian.  See [**_here _**]("http://www.nexenta.org/")for details. 

But I would rather use BtrFS myself.  It has all that ZFZ has and is a native Linux FS.

>  ZFS has the ability to maintain periodic snapshots.  However, that might lead to poor performance during operation when that is taking place.  Furthermore, it takes power to do that.  Performance and power consumed would seem to rule this out in the OP's case.

It appears to me that two things must be accomplished:

1.  State must be saved as necessary.

2.  Writes must be committed as necessary.

I think this would be true regardless of the OS or file system.

To accomplish 1 and 2, power must be supplied long enough for the "worst-case" length of time it would take for both tasks to finish.

The options for a very small unit would likely be either a small "coin" battery or some built-in capacitance.  The sole purpose of each/either (maybe both for double protection) would be to provide power for that brief interval.

This is more a hardware issue than an OS/File System issue.
It is more a design and engineering project.  Yes, it is the choice of hardware here and I would let the OP sort that out.

---

### Post by QIII on 2010-07-07
> **capscrew said:**
> Nextenta does a great job of integrating ZFS with Debian.  See [**_here _**]("http://www.nexenta.org/")for details. 

I think the integration there is going the other direction, perhaps.  Looks like grafting GNU onto the Solaris kernel.  Definitely looks interesting to me, though!

---

### Post by capscrew on 2010-07-07
> **QIII said:**
> I think the integration there is going the other direction, perhaps.  Looks like grafting GNU onto the Solaris kernel.  Definitely looks interesting to me, though!

It is.  As a user of both, I don't really see much difference in functionality.

At present I am waiting for BtrFS to become stable.  I like OpenSolaris but I have misgivings about its "open nature" for the long term now that Sun has been swallowed up by Oracle.

---

### Post by QIII on 2010-07-07
Ah.  My old friend OpenSolaris is not long for this world, I think.  Still 9.06 and the next version is now 6 months over due...

---

### Post by Shompol on 2010-07-07
So you are trying to embed a system designed for (some) human interaction into a 100% autopiloted black box, fsck being the problem.

1. Find where fsck loads and add argument -a "Automatically repair the file system without any questions" - [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

This being said, I can see many other potential loopholes where Ubuntu might go ahead and ask for user input, "bricking" the box. Maybe using off-the shelf ubuntu config is not very safe for a black box. Good luck!

---

### Post by capscrew on 2010-07-07
> **Shompol said:**
> So you are trying to embed a system designed for (some) human interaction into a 100% autopiloted black box, fsck being the problem.

1. Find where fsck loads and add argument -a "Automatically repair the file system without any questions" - [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

This being said, I can see many other potential loopholes where Ubuntu might go ahead and ask for user input, "bricking" the box. Maybe using off-the shelf ubuntu config is not very safe for a black box. Good luck!

I agree this would not be a full blown Linux OS, not should all ideas be incorporated.  What it would be is up to the OP.  As I said earlier this is a design project, not an of the shelf project.

---

### Post by jwbrase on 2010-07-07
> **BillRebey said:**
> GreenN00b, thanks for jumping in!

0 failures in 100 power cycles with EXT3 is not unexpected.  On one EXT3 test, I got about 385 good power cycles until a failure.  (EXT4 seems to fail much quicker than that - on the order of 1 in 100 in my testing).

1 failure in 400 means that if I have a client whose facility has 400 installed units, one of them will be bricked EVERY DAY!  If I have 10 clients that size, I'm looking at 10 bricked units a day, and 10 service calls, not to mention the lost data.  That's clearly not a good business model.

One will be bricked every day *if* 400 machines are experiencing unexpected power losses every day. (Eg, if your client's whole facility is experiencing an unanticipated power loss every day, and there are no battery backups, or said backups are being allowed to run down on each and every machine, every day).

And that's only if the machines are doing as something as likely to cause failure as your test case.

Are you really expecting *that* many power failures?

> 
Also note that your own experience is not likely anywhere near as taxing as my testing.  My test case makes the disk very busy, with 20 threads across 10 processes reading to and writing from files.  If I uncover a bug that permits 1 failure in 500 power cycles, I'd expect that an average home desktop user, under typical desktop use and load patterns, might uncover that same bug in 50,000 power cycles, or maybe many, many more.  The typical desktop PC just isn't very busy.

The question though, is whether the actual load patterns (and number of power failures) these machines will experience is closer to your test case or to the "typical desktop", or somewhere in between.

> **BillRebey said:**
> KS07,

As for your comment about EXT3 vs. EXT4, I didn't have significantly better luck with EXT3 than I do with EXT4.

You said 300-odd vs. 100-odd? That's about 3:1, which I'd say is pretty significant. (It's about the same as the ratio between what you say NTFS gives you and Ext3).

> However, since you asked, "yes", I have done similar testing wtih NTFS on a Windows XP installation on identical hardware, and afterr 1000 power cycles, have still not bricked a PC.

Then you might want to consider Ubuntu with NTFS, assuming that, after testing, Ubuntu/NTFS performs as well as XP/NTFS, and that there are no other problems (it is a rather unconventional solution).

> 
**I do not want to use Windows**, though....I want to use Ubuntu!  I love Unix/Linux/Ubuntu, and really want this to work.   

**I'm not trying to kick anyone's dog...I'm trying to find a solution**.  I'm on your side, folks!  I'm just more pragmatic and less emotional than some others seem to be.  

I've identified a great deficiency in the product, and am looking for a way to correct the problem, that's all.

I'm really surprised that I'm not hearing more replies like "Holy Mackerel!  Are you saying that Ubuntu can be rendered unbootable just by tunring off the PC??!!  Tht's terrible!  Sounds like WIndows 95! We can't have that!  Let's find out why and get it fixed..."

Mostly because we take it for granted that hard shutdowns can render any system unbootable, do what we can to prevent hard shutdowns, and don't experience enough hard shutdowns that we often experience unbootable systems as a result.

I think the big thing is we can't imagine what situation these machines would be in that would be as hard on them as your test case.

> 
All I'm hearing, though, is "be nice to Ubuntu!".

You don't have to be nice to it. If you truly expect the machines to be under a load similar to your test case and losing power every day, ext3/4 is probably not for you. I'm not sure if *anything* that yet exists is really for you under such harsh conditions, but I'm also not a filesystems expert. (Though once again I'm a bit confused at why you're expecting every machine at a 400 machine facility to face a hard-shutdown at least once a day).

---

### Post by eeperson on 2010-07-08
It may be that the linux file systems you have been testing are not as fragile as NTFS.  The error you get when linux boots wants you to run the a fsck manually.  This allows you to make decisions about what data is good and what data is bad.  This is an effort to prevent silent corruption.  It is possible that the the Windows 'chkdsk' simply tries to correct these errors without your intervention. I admit this is pure speculation.

I think there are some steps you can take to deal with this problem in production.  First, I would create a separate read only partition for the OS.  This would ensure that the OS can at least boot and give you some extra ability to automate the repair of partitions that are corrupted.  Second, see if the you can repair the disks that fail the boot fsck.  You may be able to force a fix for the filesystem, on startup, by using the -y or -n flags for 'e2fsck'.  This will probably result in some data loss but I am assuming that this is inevitable and therefore acceptable in this environment.  If all else fails and you have a running OS (due to being on a read-only partition), you could probably write a script to reformat the damaged partition.

---

### Post by svenskmand on 2010-07-08
I think the easiest ways is to have a flash ram attached to you machine, say one of those CF card reading things that connect through SATA. This have the OS on it, and is never ever written to. Then you have a single disk which is partitioned into two equal size parts called P1 and P2. Then you machine runs and writes to P1, when it dies it will on startup inspect P1 and copy all the stuff that is needed onto P2, and clean P1 say by a express format or something. Then your program just uses P2 to read and write from. When it dies again you switch back to P1 and so on.

PS: I just thought about this, and have not had time to read the entire thread - I am somewhere at page 3, so if someone else has suggested this then ignore this post.

---

### Post by The Cog on 2010-07-08
A couple of thoughts:

Try jfs instead of ext3. It "feels" more robust to me.

Keep the OS on a separate drive to the data (or at least a separate partition) and mount it read-only. Or boot from CD. Then you can script an fsck -y before mounting the data partition, and the basic OS should be a lot safer.

Mirror your data. Experiment with btrfs for mirroring the data, perhaps.

---

### Post by endotherm on 2010-07-08
> **BillRebey said:**
> Once the file system is corrupted, the the PC is considered bricked and my clients will consider them "junk", and will either return them to me as "broken", or a service call will be generated. 
not to kibitz, but there is no grey area with "bricking". a bricked device cannot be repaired without physically replacing a signifigant portion of it;s hardware. otherwise, it's not bricked, it's just in need of repair.

---

### Post by DrMelon on 2010-07-08
> **BillRebey said:**
> 
1 failure in 400 means that if I have a client whose facility has 400 installed units, one of them will be bricked EVERY DAY!  If I have 10 clients that size, I'm looking at 10 bricked units a day, and 10 service calls, not to mention the lost data.  That's clearly not a good business model.



A couple of fallacies in your logic, sir.
One - most companies keep machine uptime for as long as possible (especially since these are headless machines). 
Two - any scheduled shutdown will be done properly - and not the result of a power failure. If your power failed at the end of every single day then yes, you probably should expect problems. If I was in that position, I would focus upon fixing the power solution.

---

