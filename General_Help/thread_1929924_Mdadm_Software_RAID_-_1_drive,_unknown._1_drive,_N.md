---
title: "Mdadm Software RAID - 1 drive, unknown. 1 drive, NTFS????"
date: 2012-02-22
forum: General Help
---

### Post by Roasted on 2012-02-22
Here was my previous setup:

250gb Windows 7 + Ubuntu /
1TB MDADM Mirror - Home
1TB MDADM Mirror - Home

My new setup:

250gb Windows 7 (removed Ubuntu + maximized NTFS partition on 250gb HDD)
Installed 60gb SSD for Ubuntu /
Left 1TB MDADM Mirror - Home (untouched)
Left 1TB MDADM Mirror - Home (untouched)

I fired it up, ran sudo blkid, added the /dev/md0 UUID to my /etc/fstab and set it to ext4 defaults 0 2. Rebooted and I got an error. "An error occured when mounting /etc/fstab". That was it. Nothing else. No /dev/sda or whatever. Just that alone. However, if I hit S for skip, my home directory was there, which suggested to me the fstab entry for my mirror'd home directory worked fine.

On a hunch I fired up GParted, and this is what I saw:

/dev/md0 - EXT4
/dev/sdb - Unknown (from what I understand having Unknown partition on a RAID component is normal)
/dev/sdc - NTFS

Wait, WHAT?! How did one of my drives get labeled as NTFS? I didn't format them. In fact, I didn't touch them. All I did was nuke Ubuntu root on the 250, expand W7 across the entire 250gb drive, and install Ubuntu root on the SSD. The 1TB drives in the array were both left untouched.

I just started playing in disk utility and any time I tried to break apart the array, it errored out that it was busy. I was attempting to break open the array, format the NTFS labeled drive, then re-add it to the array and let it sync up, but like I said, it kept erroring out. Sure enough, I saw it began a self repair.

Can anybody explain to me what happened? Will this repair fix it by chance? It has several hours to go. I'd really like to know what happened so I can avoid it in the future... Has anyone seen this before?

---

### Post by Roasted on 2012-02-22
I've grown rather frustrated with something here. So I keep seeing in disk utility, oh boy, raid functions! I can manage my array there! I decided to take this opportunity to break open my raid array since I had no flipping idea why the system was seeing my one disk as NTFS. I formatted the NTFS drive once it was broken off from the array and tried to re-add it. Nope.

Okay, so now what? I tried a whole bunch of different things, nothing of which worked. Ultimately, I had to use the command line. A quick:

sudo mdadm --add /dev/md0 /dev/sdb1

...added it right back to the array and it is now "recovering."

The big question is this: Why on earth are there raid utilities in disk utility if I cannot use their functions? Was I doing something wrong? Do I have to run disk utility as an administrator or something to do that? (though if I recall, it prompted me for admin password at some point). Any info on why you guys think this may have happened would be appreciated. Don't get me wrong, I love the ole faithful terminal. I just find it confusing why GUI options would be presented if they do not work. However, I'm halfway convinced I was doing the process wrong. What do you guys think?



EDIT - now that it's morning and it is done, I noticed that now sdb is "ext4" while sda is "unknown". Yet, both are part of the raid array.

jason@Area51:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[2] sda1[1]
      976759672 blocks super 1.2 [2/2] [UU]



EDIT II - I'm starting to get the jist of how disk utility works with RAID. During my first post when I was ranting about how some of the features wouldn't work, the array must have been busy doing something even though it wasn't listed as in recovery or anything. I went in the following day and was able to tinker around accordingly. The only confusing part I'm finding is adding a drive to the array. For example, I took sdb and split it from the array. Then I completely formatted it with simply empty space. In Disk Utility, if you select the drive from the left pane you can change the partition type. So of course I select it and went to Linux RAID Autodetect since I was utilizing this drive for a RAID array. Okay, fine. So it was basically a 1 TB unformatted disk that was labeled as "Linux RAID Autodetect". Once done I went to my array, clicked add component.... but the drive was grayed out. Wait, what? Why? 

So I took to terminal and ran:

sudo mdadm --add /dev/md0 /dev/sdb1

And it worked... So my original frustration with Disk Utility is nearly gone, as I realized afterwards that it must have been busy as the features in it that weren't working then were working fine afterwards. However, I'm a little confused over why I couldn't add my drive to the array but terminal worked great. Does that "add component" feature do something different than sudo mdadm --add?

---

### Post by Roasted on 2012-02-24
I come to you guys bearing an antenna new question. When I read about software RAID guides online, the instructions always say to add the partition. Example:

sudo mdadm --add /dev/md0 /dev/sda1

Note sda1? Particularly the 1? That would be adding the partition to the RAID.

However, someone told me I should just add the entire disk to the array, meaning:

sudo mdadm --add /dev/md0 /dev/sda

What would the advantages and disadvantages be to such a setup?

---

### Post by lildigiman on 2012-09-27
[This link]("https://raid.wiki.kernel.org/index.php/Partition_Types") is a little response to your last question.

It says you can choose either a whole disk or just a partition.

Sorry I can't help with anything else.

---

