---
title: "I need a TRUE Hardware RAID1 controller card"
date: 2009-07-27
forum: General Help
---

### Post by ant2ne on 2009-07-27
The below quote is an e-mail correspondence between myself and a sales rep who sold us 2 servers. Since it is cut from e-mail, you have to start at the bottom of the quote and read up.

> ME

The link supplied does not include linux drivers. Selecting Suse or Redhat from the drop down list does not display any drivers. It does display “RAID Web Console Utility for Linux” but that doesn’t sound like drivers. 

Regardless: I’m not thinking that is going to work. Even if I had the drivers you are suggesting for the motherboard, then I would be able to successfully set up Motherboard RAID aka “Fake RAID”, which is not what I want to do. On true RAID, the OS never knows it is sitting on a raid device. This is what I need.

Notice my first e-mail (below) where I say “linux servers using ubuntu 8.04” and “a RAID1 controller card with at least 500GB drives” 

SALES PERSON

Here is the link I promised.
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2869&lang=eng](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2869&lang=eng)

SALES PERSON

I am so sorry you are having more trouble!* Intel’s onboard raid supports the Linux operating system.* Chris is going to e-mail me the driver links for you.* If you need further help getting it installed, we can conference you in with Intel.* It is really unusual for us to install a raid card on an entry level server that is only utilizing a RAID 1 configuration (I have been building these servers for almost five years and I’m not sure that I have ever done that).* The cost is so high for the card on an entry level system that people just usually go the other way.* We can get you an add on card from Adaptec, but my server guys are telling me that the support offered for the ad on card and onboard raid are for the same Linux versions.* I will get you the link for the drivers very soon.* Let me know if I can do anything else.

ME

I’m trying to set up these linux servers and I’ve run into problems with the RAID setup. It seems this server uses Motherboard RAID or “Fake Raid”. “Fake RAID is not supported by Ubuntu. Trying to install Ubuntu on such a partition could easily result in the loss of all your data.” [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This type of raid is not true raid as it requires software to run it. Not only does it require special drivers to be loaded at install time, (and only windows drivers have been supplied) but “Fake RAID” is not stable in linux and I’ve had bad experiences with “Fake RAID” in both Windows and Linux. 

I assumed the server quoted would include true Hardware RAID controller that would be 100% linux compatible.

SALES PERSON

Here is a revised quote that says it is Linux Compatible (there are drivers available) and it will have 2 open memory slots.* Thanks!

ME

That looks perfect! It doesn’t say that it is linux compatible. We must be certain. The fewer surprises the better. Another thing I need to know is if there are empty Ram slots. If we choose to upgrade the ram later, we’d like to just add new RAM as apposed to replacing the current RAM.

SALES PERSON

Is this more in line with what you are thinking?
{attaches spec sheet that appears to suit my needs. It says supports RAID configurations}

ME

Try to put something together as close to the stats I specified below. We do not need hot swappable drives. But we do want RAID1 with the possibility of upgrading to RAID5. These drives need not be scsi if you have sata raid controller cards with linux drivers.

SALES PERSON

Do you want me to pair it down?* What do you want me to take out?

ME

I think that is way over the top of what we are needing.

SALES PERSON

Here is an option for you.* It is Linux compatible.* What do you think?* I am happy to make any changes you want.* Thanks!
{attaches spec sheet that way exceeds my specifications. It says supports RAID configurations}

ME

I’m looking to set up 2 linux servers using ubuntu 8.04. My minimum specs are a dual core CPU, 4 Gigs of RAM (with potential for future upgrades), a RAID1 controller card with at least 500GB drives, and a Gb Ethernet NIC. These will not be rack mounted servers.

Please reply with some price quotes. And verify that your hardware is linux compatible.


It appears that I may be in the market for a Hardware Raid Controller card to suit my needs. Please suggest a TRUE Hardware RAID1 controller card.

I may also be in the market for a chassis manufacturer that not only knows linux, but can sell me what I ask for.

---

### Post by LoneWolfJack on 2009-07-27
haven't read the entire thing, but if you are serious about hardware raid 1, be ready to spend 150 bucks or more for a 2 disk controller.

3ware is a pretty good choice and most of their latest controllers come with drivers for fedora/redhat/suse. you may have some luck with adaptec as well (in fact, my working machine uses and adaptec raid controller with ubuntu).

honestly though, I don't see anyone buying a 2 or even 4 drive controller for raid 0/1 unless it's a machine used for video editing.

---

### Post by ant2ne on 2009-07-27
This is to be a production Moodle Server. Speed isn't necessary, but redundancy is needed. The loss of student work/grades would be catastrophic.

Thanks for your recommendations. Could you specify a model number?

---

### Post by LoneWolfJack on 2009-07-28
2 drives: 3WARE 9650SE-2LP
4 drives: 3WARE 9650SE-4LPML

I'd still go with a software raid if speed isn't too important,

---

### Post by ant2ne on 2009-07-28
> **LoneWolfJack said:**
> I'd still go with a software raid if speed isn't too important,Yeah, maybe I should give it another try. 3rd time is the charm, right?

---

### Post by sloggerkhan on 2009-07-28
Why are people so obsessed with hardware raid? mdadm works great.

---

### Post by ant2ne on 2009-07-29
[http://ubuntuforums.org/search.php?searchid=62358262]("http://ubuntuforums.org/search.php?searchid=62358262") Read teh first few posts. In my experience; Hardware RAID is far more reliable. Also, Hardware RAID does all of the processing and the OS/CPU doesn't have to.

---

### Post by ant2ne on 2009-07-29
> **LoneWolfJack said:**
> True warriors don't follow paths - they make them.
It's not their desire, it's their nature. 
Foster and polish the warrior spirit while serving in the world; illuminate the path according to your inner light. 
- Ueshiba's famous quotes

---

