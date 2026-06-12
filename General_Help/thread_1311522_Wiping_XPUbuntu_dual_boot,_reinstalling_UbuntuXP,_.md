---
title: "Wiping XP/Ubuntu dual boot, reinstalling Ubuntu/XP, need backup checklist, thoughts?"
date: 2009-11-02
forum: General Help
---

### Post by aaronchall on 2009-11-02
My current setup is XP/Ubuntu dual boot, and I'm now running XP in Virtualbox OSE, which gives me the best of both worlds and verifies the functionality of the setup for my purposes and future use.  
 
So what I'm going to do is do a full reformat, including reclaiming and wiping the recovery partition (hey it's 10 gigs on an 80 gig HD, that's valuable space!).  Then I'm going to reinstall XP (it's media center edition) on say a 20 gig partition. Then I'm going to install Karmic so I get the grub(2?) and ext4 (and then a Virtualbox XP for most XP computing..., the first XP install will be for when I need it to do something it can't do in Virtualbox.)  
 
Here's a question, do I need 2 partitions (for future upgrades and whatnot?) and how do I do that? (HOW and WHY?)
 
I think I need to make a backup list.
 
Things I need to backup off the top of my head: 
[LIST]
[*]documents
[*]document folders
[*]tomboy notes (HOW?)
[*]music files
[*]configuration for firefox/ (HOW?)
[*]zotero (I think I have it backed up online, so what else might I need to get from it? If someone has this specialized info, thanks!)
[*]what else?
[/LIST]

---

### Post by lisati on 2009-11-02
Recovery partition(s)?

---

### Post by aaronchall on 2009-11-02
> **lisati said:**
> Recovery partition(s)?
 
It's a dell laptop, and I can download any drivers that aren't on the XP CD.

---

### Post by xtremesupremacy3 on 2009-11-02
I am a little confused about the 2 partitions to be honest.

when you say 2 partitions, is this for Ubuntu and XP? And do you mean 2 additional partitions?

As for the backup...
Firefox, I am unsure of, but if you open Tomboy, select Edit, then Preferences and then it tells you where you could save a 'synchronisation'...then once it's set up, click tools, and Syncronise

---

### Post by aaronchall on 2009-11-07
> **aaronchall said:**
> My current setup is XP/Ubuntu dual boot, and I'm now running XP in Virtualbox OSE, which gives me the best of both worlds and verifies the functionality of the setup for my purposes and future use.  
 
So what I'm going to do is do a full reformat, including reclaiming and wiping the recovery partition (hey it's 10 gigs on an 80 gig HD, that's valuable space!).  Then I'm going to reinstall XP (it's media center edition) on say a 20 gig partition. Then I'm going to install Karmic so I get the grub(2?) and ext4 (and then a Virtualbox XP for most XP computing..., the first XP install will be for when I need it to do something it can't do in Virtualbox.)  
 
Here's a question, do I need 2 partitions (for future upgrades and whatnot?) and how do I do that? (HOW and WHY?)
 
I think I need to make a backup list.
 
Things I need to backup off the top of my head: 
[LIST]
[*]documents
[*]document folders
[*]tomboy notes (HOW?)
[*]music files
[*]configuration for firefox/ (HOW?)
[*]zotero (I think I have it backed up online, so what else might I need to get from it? If someone has this specialized info, thanks!)
[*]what else?
[/LIST]


Anyone else want to take a shot at advice or a link to a page with suggestions?

---

### Post by Junkieman on 2009-11-28
Hi. Did you manage this in the end? 

Most settings are stored inside your /home folder, a good idea to double check with the app developers if there's any particular ones you can't risk to lose.

I assume you are talking about installing your /home partition on it's own, and the Ubuntu system on a separate partition. I did the same on a 80GB a few days ago, my experiment drive for new OS's and such, with Karmic and Windows 7, here is what I did:

I used the Windows install partitioner and split the disk into two partitions, a 20GB primary, and an extended with the rest of the space. I left the extended unformatted. Install Windows on the primary. -- I should add that Windows automatically created a tiny partition within it's allocated space, that it used as it's boot partition. This is fine.

When that's done, you install Ubuntu. When you get to the disk stage, use the custom/advanced option, to define your own partitions, and split your extended partition further (just leave the Windows NTFS partition alone):

Select the extended space, and click 'New' to create a new partition for your system (mine was 15GB), assign it to '/'.

Create a swap partition (mine was 3GB to match my system RAM), and finally create another partition, with the rest of the space, this will be assigned to /home.

That's it, click through and the partitioner will install Ubuntu with your /home on it's own partition. 

Grub should detect the Windows partition and add it to the boot list automatically. I say 'should' since I installed Ubuntu first (was too excited for it!) and Windows after, so I manually had to reinstall grub, but that picked up Windows all the same.

Hope this helps :)

I'm about to reinstall my main drive with Ubuntu, but this time I'm going for a separate /home and system (my current setup is all on one drive, since Hardy days). 

I'm doing this mainly for ease of future upgrades. My current system files run at about 8GB, and I install a lot of apps (but not many high-content games). So I figure 15GB for system is way more than enough. Your mileage may vary, and the [recommended disk space]("https://help.ubuntu.com/community/Installation/SystemRequirements") is 8GB, so anywhere in between is a safe bet.

If you have the space, [make an image]("http://clonezilla.org/") of your system, in case of purple alert. 

There's some [more info here]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by ed-koala on 2009-11-28
Tip time!!

Google "Firefox Ubuntu backup", and other "<your app> backup", to find info on how to save needed configuration files.

I'm curious, what exactly isn't VirtualBox doing that you need Vista for?  Can Wine help?  Personally, I *hate* Windows and will do almost anything to keep from having to install it on my PC (but that's just me). Let us know, we might know a way to help make it work, or some alternate app you can use that does the same thing (assuming it's not a game).

---

