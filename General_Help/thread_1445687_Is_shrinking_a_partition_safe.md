---
title: "Is shrinking a partition safe?"
date: 2010-04-02
forum: General Help
---

### Post by hedgeberg on 2010-04-02
After an insane set of errors after trying to install ubuntu 9.10 using wubi, I have decided to try and reinstall ubuntu, at 10.4. I will do this once the new release is stable and out of beta. To prepare, I want to create a partition for ubuntu, and that requires shrinking a partition, probably my OS partition. Big problem is that OS has most of my data on it, and I need to shrink that to create free space for a new partition. Will this be safe, and is there absolutely NO risk that I will lose data? I already know how to create the partition (Vista has a system for this built in). So, It all boils down to safety.

---

### Post by Primefalcon on 2010-04-02
there is always a risk.... but if you do it properly that risk is very small.... I have resized partitions many times however.... and never had an issue...

Just whatever you do don't cancel it once you start it

---

### Post by takisan on 2010-04-02
It's safe. I did it before, but it takes a lot of time. It might be smart to do a backup and / or Defrag.

Best of luck with Lucid.

---

### Post by lisati on 2010-04-02
Defrag is a good idea, to move the data to the "start" of the disk. I've heard that using Vista's partitioning tools on an NTFS volume is sometimes preferable to using gParted or similar.

---

### Post by prodigy_ on 2010-04-02
Resizing a partition (either way) is always a very bad idea. I honestly can't understand why it's become such a popular practice lately.

---

### Post by hedgeberg on 2010-04-02
I am getting some mixed messages, from totally safe to really risky. I did back up recently, so as to restore my computer. I have looked at what shrinking the partition, and windows does severely limit how much the partition can be changed. Does this show some form of safety, or does it just mean that I can only make so big of a new partition?

---

### Post by wilee-nilee on 2010-04-02
I am familiar with the W7 disk management partitioner, assuming it is similar to Vistas it must have a option to check how much it can be shrunk, so that your within a safety margin MS set.

The auslogics disc defragger will defrag, optimize, and move as many files as possible to the beginning of the OS.
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)

Make sure your backed up use the Vista partitioner, leave a unallocated for Ubuntu, unless you want to build a custom partition setup and install.

---

### Post by prodigy_ on 2010-04-02
> **hedgeberg said:**
> I am getting some mixed messages, from totally safe to really risky.
I could give you some good tech arguments, but let's keep it simple. Just do a search on "General Help" forum about something like "recently I resized my partition and now..." 

You'll be amazed.

---

### Post by rhy7s on 2010-04-02
> **hedgeberg said:**
> Big problem is that OS has most of my data on it, and I need to shrink that to create free space for a new partition. Will this be safe, and is there absolutely NO risk that I will lose data?

Well, you've got a backup don't you?
There's:
[http://clonezilla.org/](http://clonezilla.org/)
[http://ping.windowsdream.com/ping.html](http://ping.windowsdream.com/ping.html)

And for Windows:
[http://www.oo-software.com/home/en/products/oodiskimageexpress/index.html](http://www.oo-software.com/home/en/products/oodiskimageexpress/index.html)
[http://www.paragon-software.com/home/db-express/index.html](http://www.paragon-software.com/home/db-express/index.html)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by wilee-nilee on 2010-04-03
> **prodigy_ said:**
> I could give you some good tech arguments, but let's keep it simple. Just do a search on "General Help" forum about something like "recently I resized my partition and now..." 

You'll be amazed.

Hmm a data base with no actual validity because of it's location, on a forum for helping people with problems.

Skewed demographics are not helpful.

---

### Post by prodigy_ on 2010-04-03
> **wilee-nilee said:**
> Skewed demographics are not helpful.
/sigh
See you in your own personal "...and now I'm screwed" thread.

---

### Post by lovinglinux on 2010-04-03
I also have done this several times and never had a problem. Nevertheless, it is indeed a risky operation. If you have regular power outages on your area, then wouldn't recommend doing this if you don't have an UPS...you know, Murphy's law...

---

### Post by srs5694 on 2010-04-03
The problem is that "safe" and "unsafe" are vague and relative, with little or no quantitative data available. Suppose we begin quantify things, and define safety in terms of percentage of successful operations. In those terms, resizing a filesystem is not 100% safe, and is never likely to be; the risk of power failures, bugs, errors due to minor filesystem corruption, etc., will all drag the safety percentage down. My own personal experience is that it's perhaps 95-99% safe; however, I've been resizing partitions for over a decade. (I wrote a review of Partition Magic that appeared in *Linux Journal* sometime around 1999 or 2000, and I've used more primitive tools even before that.) I know what I'm doing, so I know the pitfalls, I don't make beginner mistakes, and I know how to overcome minor problems like boot issues that can result from a partition resize. My systems are all on UPSes, which minimizes the risk of data loss to power failures. Somebody who's completely new to the practice might have more like a 50-90% chance of success, depending on just how well they've done their homework, although some of these "unsuccessful" operations would still leave data intact (they wouldn't be able to get the operation started). Call it 70-95% safe for a complete newbie. That's a wild guess, though. Even in the event of damage, the damage might be correctable, although of course that requires knowledge, so a newbie would end up having to post here, or might give up in frustration.

Now, is that "safe?" What's your standard? Is a 2% chance of data loss excessive? 5%? 10%? What's your skill level? What resources do you have to deal with problems? (A spare computer? A knowledgeable co-worker, friend, or relative? This forum?) Nobody here can answer these questions for a complete stranger. Worse, AFAIK there are no scientific studies of the issue, so we're left with wild guesses such as those I've presented about the quantitative measures of safety.

---

### Post by fisheater on 2010-04-03
in my n=6 it has been safe.

that said, i always back up my data to a removable USB HD. then disconnect it.

then i accept that it may make my system fail. and i have built in enough time to reinstall my systems.

when all that is done, i resize.

good luck.

fe

---

### Post by 23dornot23d on 2010-04-03
Buy another hard drive if you are really worried ....

If its a laptop ...... get a USB one I recommend the Iomega Terra Drive

If its a Desktop PC ...... just get a compatible one for it ........

As said before there are always risks ..... I have re-sized many times ...... 
but to cut down your worries and open up more options.

Buy another hard drive ..... the prices are always coming down on these
 
What is the cost of peace of mind and your safe data ..... ;)

---

### Post by new_tolinux on 2010-04-03
I'm not going through all the do's and don't's, as you can find them easily.

When done right, with the right tools, it should go fine.
Back in those days, when a drive was expensive and small, I had Partition Magic (which was a perfect tool back then). It really worked well almost every time. But..... it's a program, and it's a drive, so failure is always an option. Always (and I really mean _always_) make sure that you have a decent back-up before you start to cover yourself. 99,9% success-rate is still not 100%.
You would not be the first person who was busy and suddenly there's a power-outage.

---

### Post by hedgeberg on 2010-04-03
fortunately power is not a problem. my computer is a laptop. I can back up, so what is recquired, on vista, to create a system restore point that I can boot from. also, to follow up on previous posts, I do have a high level of skill. The big question now is, should I go with it or not?

---

### Post by lisati on 2010-04-03
I'd say "go for it", with the suggestion that in the unlikely event of something serious going wrong, a set of recovery disks might be of more value than restore points.

---

### Post by Herman on 2010-04-03
My suggestion is to run a file system check in the partition before resizing it since I believe that will reduce your risks in a number of ways.

Firstly, it will fix errors that may already exist in your file system before you start the partitioner. Most partitioners will try to detect file system errors and refuse to operate on the partition, however, if a file system error does slip through it would be likely to be aggravated by subsequent file system operations such as resizing.

Secondly, the feedback you get from running a file system check may include hints about the condition of your hard disk.
If you see scary feedback like 'bad blocks found, x number of sectors re-allocated', 'recovering orphaned file <F88FFA32-1C73.da>.dat <72755> into directory file 56956', 'x number of errors left uncorrected', or words to that effect it might be best to refrain from resizing your partition. On the other hand, if your file system check reports nothing done and that your file system, (and drive), is in perfect health then you can go ahead with more confidence.

For partition containing Windows NTFS, the file system checking program is called CHKDSK.
The easiest way to run CHKDSK is to go to 'My Computer', and right-click on drive C, click 'properties' and go to the tools tab, and click 'check now'. 
A 'check disk' windows will open, and you should place a check mark in both squares, one for 'automatically fix system errors', and the other for 'scan for and attempt recovery of bad sectors'.
Another way to run CHKDSK (often necessary if Windows won't even boot), is to use your 'Recovery Console' for your version of Windows, here's a page about XP's Recovery Console,  [Windows XP 'Recovery Console']("http://members.iinet.net.au/%7Eherman546/p18.html#Windows_XP_Recovery_Console") - kelly's-corner-xp.com
 I recommend running CHKDSK /R, because that includes CHKDSK /F, and while it takes a lot longer, it will do a much more thorough job.
It's important to use the right version of CHKDSK to match your version of NTFS. Different versions of Windows have different versions of the file system, so if you have Windows XP, it's best to use an XP installation CD, or an Vista install CD if you have Vista, and a 7 install CD if you have Windows 7, and so on.

---

### Post by w8ye on 2010-04-03
I put all my personal data on a USB drive and reinstalled Ubuntu only - getting rid of Vista.

reused the old book marks and other setups and I feel at home with the new way.

It boots up in Ubuntu and it uses the whole drive. No problems.

After backing up everything and taking note of how I had the old system, it took 45 min to reload the system up and running wireless and all.

---

### Post by gadolinio on 2010-04-03
> **wilee-nilee said:**
> 

 	Quote:
 	 	 		 			 				 					Originally Posted by **prodigy_** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9068251#post9068251") 				
 				[I]I could give you some good tech arguments, but let's keep it simple. Just do a search on "General Help" forum about something like "recently I resized my partition and now..." 

You'll be amazed.[/I]
 			 		 	 	 
Hmm a data base with no actual validity because of it's location, on a forum for helping people with problems.
Skewed demographics are not helpful.




I agree; this place might not be the right one for stastistics.

I've resized partitions several times, and have never had a problem, though i've read that it is somewhat risky. I guess it could be compared with undergoing a surgery: it is not the safest thing in the world and people are nervous because of that, but in a single day it is done many times... and people usually end up better than before (doctors make a living out of it). It is what you could call a "normal" practice.

If you have a backup of all your data, you are pretty much protected against Murphy's law. The problem if you're unlucky could be the time you'd have to spend fixing the OS.

If you need to resize, my advice is that you go and do it.
Good luck!

---

### Post by lovinglinux on 2010-04-03
> **srs5694 said:**
> The problem is that "safe" and "unsafe" are vague and relative, with little or no quantitative data available. Suppose we begin quantify things, and define safety in terms of percentage of successful operations. In those terms, resizing a filesystem is not 100% safe, and is never likely to be; the risk of power failures, bugs, errors due to minor filesystem corruption, etc., will all drag the safety percentage down. My own personal experience is that it's perhaps 95-99% safe; however, I've been resizing partitions for over a decade. (I wrote a review of Partition Magic that appeared in *Linux Journal* sometime around 1999 or 2000, and I've used more primitive tools even before that.) I know what I'm doing, so I know the pitfalls, I don't make beginner mistakes, and I know how to overcome minor problems like boot issues that can result from a partition resize. My systems are all on UPSes, which minimizes the risk of data loss to power failures. Somebody who's completely new to the practice might have more like a 50-90% chance of success, depending on just how well they've done their homework, although some of these "unsuccessful" operations would still leave data intact (they wouldn't be able to get the operation started). Call it 70-95% safe for a complete newbie. That's a wild guess, though. Even in the event of damage, the damage might be correctable, although of course that requires knowledge, so a newbie would end up having to post here, or might give up in frustration.

Now, is that "safe?" What's your standard? Is a 2% chance of data loss excessive? 5%? 10%? What's your skill level? What resources do you have to deal with problems? (A spare computer? A knowledgeable co-worker, friend, or relative? This forum?) Nobody here can answer these questions for a complete stranger. Worse, AFAIK there are no scientific studies of the issue, so we're left with wild guesses such as those I've presented about the quantitative measures of safety.

Well said.

---

### Post by hedgeberg on 2010-04-04
just had an idea. would it be possible to boot ubuntu from a usb hard drive? I could create a new partition on that and then install ubuntu.

---

### Post by 23dornot23d on 2010-04-04
That is exactly what I do ..... boot from USB drives ..... 

I have two plugged in and by switching the boot order in the BIOS ..... USB or Main Hard Drive ..... with one USB excluded from the boot order ...... 
just check that your BIOS allows it (booting from USB hdd ... most new ones do) ..... (The boot menus ie grub need to be located on the USB's)
So that if you ever detach them you can still run the laptop separately .....
I have 3 different menu systems for various versions of linux ...... Mandriva Mint and Ubuntu ..... plus many more ...... and all run well ......
I run Grub 2 from the main drive in the laptop (although I would prefer to still be running Grub 1)
and Grub 1 from one of the USB drives ...... 
then a Mandriva menu on the second USB which allows chainloading from grub 1 to grub 2 .....(this is my preferred choice grub 2 takes too long to load)

This is a safer option in my mind using your USB ..... not that I have ever had any problems re-sizing partitions - 
but there could always be a first time ..... and I would hate for you to have to spend ages sorting it all out if it did go wrong .... 
as I get older I try to reduce the risks ..... too much data to lose ...... and way too much to back up ....... 
if I run out of space or want to try out other Linux OS's .....  I just buy another USB drive ...... the costs are so low now for these ....

Its interesting having different desktops too ..... I use each one for different things ,,,, 3D on one desktop Photo Editing on another etc ..... it can lead to
better organisation of files ...... and by keeping all my files on a partition that I can access from any of the other systems ...... works well for me ........

---

### Post by gadolinio on 2010-04-06
> **srs5694 said:**
> The problem is that "safe" and "unsafe" are vague and relative, with little or no quantitative data available. Suppose we begin quantify things, and define safety in terms of percentage of successful operations. In those terms, resizing a filesystem is not 100% safe, and is never likely to be; the risk of power failures, bugs, errors due to minor filesystem corruption, etc., will all drag the safety percentage down. My own personal experience is that it's perhaps 95-99% safe; however, I've been resizing partitions for over a decade. (I wrote a review of Partition Magic that appeared in *Linux Journal* sometime around 1999 or 2000, and I've used more primitive tools even before that.) I know what I'm doing, so I know the pitfalls, I don't make beginner mistakes, and I know how to overcome minor problems like boot issues that can result from a partition resize. My systems are all on UPSes, which minimizes the risk of data loss to power failures. Somebody who's completely new to the practice might have more like a 50-90% chance of success, depending on just how well they've done their homework, although some of these "unsuccessful" operations would still leave data intact (they wouldn't be able to get the operation started). Call it 70-95% safe for a complete newbie. That's a wild guess, though. Even in the event of damage, the damage might be correctable, although of course that requires knowledge, so a newbie would end up having to post here, or might give up in frustration.

Now, is that "safe?" What's your standard? Is a 2% chance of data loss excessive? 5%? 10%? What's your skill level? What resources do you have to deal with problems? (A spare computer? A knowledgeable co-worker, friend, or relative? This forum?) Nobody here can answer these questions for a complete stranger. Worse, AFAIK there are no scientific studies of the issue, so we're left with wild guesses such as those I've presented about the quantitative measures of safety.

Interesting analysis... +1

---

