---
title: "Bad Sectors"
date: 2011-01-04
forum: General Help
---

### Post by RabbitWho on 2011-01-04
Hi my moms computer wouldn't start so i backed everything up using a live disk and then tried to reinstall the OS (Vista) 
Still wouldn't start and after some time spent panicking and trying different things Gparted told me there were over 35 bad sectors (It's a 100GB hard drive), I'm running badblocks now (it's at 70%) with the command badblocks -ws
Which is destructive read-write mode. 
This hasn't happened before and I don't really know what I'm doing, so any information anyone could give me would be great, like for example what exactly does it "destroy" if it's destructive o.O and what will I need to do after it's finished. 
I'm hoping to dual boot it with Vista and Ubuntu, at this point I don't think it would be worth the money to replace the hard drive, considering it's a miracle to have a HP pavilion dv6000 last this long at all with all the problems they've had with melting graphics cards. What do you think? Any advice at all is appreciated.

tl;dr [B]
My hard drive has bad sectors.
What does badblocks -ws actually do?
What should I do when it's finished? 
If it works how long more could the hard drive be expected to last?[/B]

---

### Post by dino99 on 2011-01-04
hm bad sectors dont mean hard troubles :)

time to time hdd need some cleanings / reordering

there is a usefull toy for doing it : ccleaner

vista come with something like chkdsk & defrag

but saying: i dont know what i'm doing, its really scary dude :(

if you plan to install ubuntu:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Rubi1200 on 2011-01-04
Are you in the habit of running commands without knowing what they will do?

If there was data on the drive it is gone now:
From the manpage:
> Never use the **-w**  option on an device containing an existing file system. This option erases data! 

If the drive had Windows on it, you should have first tried something like chkdsk.

Now you will have to wait until it is finished and tell us what happened before we can advise you on the next step.

The one thing I want to add is this: kudos that you had the presence of mind to backup the data before doing this.

---

### Post by endotherm on 2011-01-04
I'd recommend you check the drives smart stats with Disk Utility (system-> administration ) to make sure that your reallocated sector count is still in a pre-fail state (it will tell you).
if it isn't, then you would prolly have to replace teh drive. I disagree with Dino that badblocks are not hardware issues, since they are:
[https://secure.wikimedia.org/wikipedia/en/wiki/Badblocks](https://secure.wikimedia.org/wikipedia/en/wiki/Badblocks)

if you have more than a few, your drive is headed in a bad way, and will not likely last long. I'm glad you managed to get your data backed up. 

here are some replacement drives for less than 50$
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007605%2050001306%204025&IsNodeId=1&name=%2425%20-%20%2450](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007605%2050001306%204025&IsNodeId=1&name=%2425%20-%20%2450)

---

### Post by RabbitWho on 2011-01-04
> **Rubi1200 said:**
> Are you in the habit of running commands without knowing what they will do?

If there was data on the drive it is gone now:
From the manpage:


If the drive had Windows on it, you should have first tried something like chkdsk.

Now you will have to wait until it is finished and tell us what happened before we can advise you on the next step.

The one thing I want to add is this: kudos that you had the presence of mind to backup the data before doing this.


As I said I had just reinstalled the operating system in the hopes that would make the computer start so obviously formatting the drive means nothing to me, there's nothing to save. 
But do you mean that it will have even ignored partitions and gone through the entire drive and deleted things it wasn't told to delete? Because that's what you suggested by saying all data on the drive will be gone. This would mean not being able to save Vista as I was planning on recovering it from the other partition.  (I wasn't able to make recovery disks because you have to be able to access Windows to do that, really clever way of saving money HP.. really clever. :rolleyes:)
I don't see why the command would do all partitions when it was specifically told to do just one.

As I said previously unfortunately Vista wouldn't start, there was no way for me to get a windows command line so I couldn't run chkdsk or ccleaner, or could I? 
Even with the repair utilities (which usually offer a command line) they automatically started trying Start up Repair (which you're not allowed to cancel) before i got to that screen they got stuck in a loop and something which was supposed to take 2 hours tops took 15 and eventually the computer just crashed. 

>  I'd recommend you check the drives smart stats with Disk Utility (system-> administration ) to make sure that your reallocated sector count is still in a pre-fail state (it will tell you).
if it isn't, then you would prolly have to replace teh drive. I disagree with Dino that badblocks are not hardware issues, since they are:
[https://secure.wikimedia.org/wikiped...wiki/Badblocks]("https://secure.wikimedia.org/wikipedia/en/wiki/Badblocks")

if you have more than a few, your drive is headed in a bad way, and will not likely last long. I'm glad you managed to get your data backed up. 

here are some replacement drives for less than 50$
[http://www.newegg.com/Product/Produc...25%20-%20%2450]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007605%2050001306%204025&IsNodeId=1&name=%2425%20-%20%2450") 

Thank you endotherm, that was exactly the type of information I needed! 


I read somewhere that bad sectors can be caused by power surges, which are really common where my parents lived, I also read that if this is the cause they're unlikely to spread.. so fingers crossed that was it!

---

### Post by QLee on 2011-01-04
RabbitWho,

It probably would have been a better choice to have used e2fsck -c on the partition to do a read only scan for badblocks, that should have left the data on the partition. It is always a good idea to read the manual page for a command you don't already know before using it. I also recommend that.

Yes, there is a good chance the sectors were corrupted during a power surge if the disk was writing at the time. Something to consider is a small battery back -up unit to plug their computer into, it can protect for a short time from surges and brown-outs.

---

### Post by psusi on 2011-01-04
Check the SMART data.  Look specifically at the reallocated and pending counts, also offline_uncorrectable.

---

### Post by HermanAB on 2011-01-04
Howdy,

Disks don't last forever.  A 100 Gig disk must be rather old.  I'd suggest that you buy a new disk and re-install the system.

---

### Post by phalantice on 2011-01-04
Rabbit the drive is dead a win util thats handy if smart is turned on is hdtune you can see ecc read/write errors and how many relocated sectors etc.  smartctl is in linux and can give you similer information from the cli. If its a dell it would fail the read test and probably the confidence test.  

as for the life of the part.  hdd's tend to have 3 yr warranty for a reason.  any thing after that is gravy though some are warrantied for 5 now.  1 you need to know what type of hdd it is. make/model of the pc would help.  some older pc's may have issues with 1tb+ drives check the manufacturers documentation on limitations.  you will probably want to get a 100-300gb 7200rpm ata drive.  thats just a guess though.  they come in a few sizes though.  most laptops have a 2.5" drive.  some of the ultra portable systems have a 1.8 or propriatary sized drive.  

Power issues = pc death.  laptops are a bit more forgiving due to battery and hot plugging of the power source/dockinstations.  over/under voltage and noise on the power line can quickly chew threw pc's though.  

herman many manufacturers were still giving out 60-80gb drives on new pc's till the last year or so as the base setup.

---

### Post by QLee on 2011-01-05
[QUOTE=RabbitWho]...

It's a laptop, does the laptop battery count?[/QUOTE]

Maybe, depends on how well the combination of power brick and internal circuitry filters power surges from the line. Battery back up units are designed to do that task.

Even though you spent 1K Euros on the computer that does not mean the hard drive was a particularly expensive one and laptop hard drives typically see rougher service than desktop units.

---

### Post by RabbitWho on 2011-01-05
Hi again everyone, thanks for all the information. 

Badblocks is still running

it says:

_10028875_ done 47:32:08 elapsed 

Any idea what was does the bit I underlined refer to? It seems like it could mean anything. Hopefully not bytes or we'll be here for the rest of our lives ha ha. 

It's frustrating because I was only home for the Christmas and I have to leave tonight at 6, at this rate I'm not going to have time to see if it works at all, let alone reinstall Vista or put Ubuntu on for them even if it does work.... or explain how to use a live CD if it doesn't.

---

### Post by endotherm on 2011-01-05
hdd's, like any mechanical technology, are dying every second they are alive. sometimes incidents like power failures, application crashes that cause a blue/black screen shutdown, impacts, or even just jostling it around at exactly the wrong millisecond can cause significant damage all at once, but small bits of damage from a not-so-great IO controller, or a bad acting driver, or bad firmware operations can really start to add up after a few years. for instance, remember the load cycle count bug with some HDDs in Gutsy - Jaunty?
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by endotherm on 2011-01-05
> **RabbitWho said:**
> Hi again everyone, thanks for all the information. 

Badblocks is still running

it says:

_10028875_ done 47:32:08 elapsed 

Any idea what was does the bit I underlined refer to? It seems like it could mean anything. Hopefully not bytes or we'll be here for the rest of our lives ha ha. 

It's frustrating because I was only home for the Christmas and I have to leave tonight at 6, at this rate I'm not going to have time to see if it works at all, let alone reinstall Vista or put Ubuntu on for them even if it does work.... or explain how to use a live CD if it doesn't.

it's my understanding (based on this: [http://terminalapp.net/bad-blocks-badblocks/](http://terminalapp.net/bad-blocks-badblocks/)) that the output is indicating that you have one bad block at index 10028875.

---

