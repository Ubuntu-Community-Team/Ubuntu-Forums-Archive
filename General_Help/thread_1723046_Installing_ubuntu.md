---
title: "Installing ubuntu?"
date: 2011-04-06
forum: General Help
---

### Post by branko.savic on 2011-04-06
I am helping a friend to install ubuntu, and he has a small ssd hardrive that he wants the OS installed on, but everything else he wants to save to another drive!

Is it possible to setup ubuntu to automaticly save into another drive?

---

### Post by wolfen69 on 2011-04-06
Just set the browser to wherever you want stuff to be saved to. Some browsers will ask where you want things saved for each download.

---

### Post by Dupointx on 2011-04-06
> **branko.savic said:**
> I am helping a friend to install ubuntu, and he has a small ssd hardrive that he wants the OS installed on, but everything else he wants to save to another drive!

Is it possible to setup ubuntu to automaticly save into another drive?

what size is the ssd?

---

### Post by Quintilian on 2011-04-06
when installing you can set a separate hard drive/partition to mount at /home. this way, yes, all his files would be saved on the other drive if he saved everything under /home or /home/[user]

during the install however you will have to manually set the partitions when it asks you how you want to install ubuntu. on the ssd just make the mountpoint at / and the swap can either go on the ssd if he plans on hibernating a lot or on his other hdd to save space for installed programs or if he wont use hibernate. it used to be recommended to have twice as much swap space as RAM installed, but i'd just do the same amount so that hibernation is enable-able (this is where the ram image is stored during hibernation).
hope that helps...

---

### Post by branko.savic on 2011-04-06
> **Quintilian said:**
> when installing you can set a separate hard drive/partition to mount at /home. this way, yes, all his files would be saved on the other drive if he saved everything under /home or /home/[user]

during the install however you will have to manually set the partitions when it asks you how you want to install ubuntu. on the ssd just make the mountpoint at / and the swap can either go on the ssd if he plans on hibernating a lot or on his other hdd to save space for installed programs or if he wont use hibernate. it used to be recommended to have twice as much swap space as RAM installed, but i'd just do the same amount so that hibernation is enable-able (this is where the ram image is stored during hibernation).
hope that helps...

it helps, but could you please give me an example on how the patiotions should look like?

is it like:

/home (on the ssd or on the harddrive?)
what should the rest be?

Thanks, I have never done this before!

The SSD is a revodrive 120GB PCI-E 4

---

### Post by davidmohammed on 2011-04-06
I would recommend / on the SSD to allow fast booting.

/home should be on your other drive

Its a judgement call for /swap - if you have a particular slow external drive have /swap on the SSD.  However - if the other drive is reasonable put /swap on that drive

---

### Post by Dupointx on 2011-04-06
> **branko.savic said:**
> it helps, but could you please give me an example on how the patiotions should look like?

is it like:

/home (on the ssd or on the harddrive?)
what should the rest be?

Thanks, I have never done this before!

The SSD is a revodrive 120GB PCI-E 4

/home is where the user files are, so that would be on the hard drive if that is what your friend wants. It can be from 20GB-very large. formatted as ext4.

The rest would be:
"/" on the SSD, size 20GB, formatted ext4, this is where boot-up and system files are.
"linux-swap" either on the SSD or HDD, it's like the page file in Windows, you need it to hibernate, size would be as large as amount of RAM up to two times the amount of RAM more than that would be a waste.

---

### Post by branko.savic on 2011-04-06
> **davidmohammed said:**
> I would recommend / on the SSD to allow fast booting.

/home should be on your other drive

Its a judgement call for /swap - if you have a particular slow external drive have /swap on the SSD.  However - if the other drive is reasonable put /swap on that drive

Ok, thank you for your time!

---

### Post by branko.savic on 2011-04-06
Another question

My friend has two 750GB harddrives that he used in raid 0 on his previouis system!

Now when he has then in his new I7 system and ubuntu 10.10 the system can not identify the drives!

When trying to format the I get an error on both drives that they are busy!

Is there a solution to format the drives somehow?

---

### Post by davidmohammed on 2011-04-06
is this in a hardware RAID configuration or as a software RAID configuration?

If its a software RAID I suspect you'll need to recreate the [RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

I dont know enough about hardware RAIDs to give you more advice but I suspect someone will ask what the hardware RAID type is?

---

### Post by branko.savic on 2011-04-06
> **davidmohammed said:**
> is this in a hardware RAID configuration or as a software RAID configuration?

If its a software RAID I suspect you'll need to recreate the [RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

I dont know enough about hardware RAIDs to give you more advice but I suspect someone will ask what the hardware RAID type is?

umm I honestly dont know... he raided the drives in his motherboard, so I would like to say it is a hardware raid, but then again as I am aware of, it is still a software raid as long as you dont have a propriatary raid card!?

---

### Post by Quintilian on 2011-04-06
it sounds like he's using a hardware raid. if it's configured through the motherboard during bootup (after the POST) then it's generally hardware.

---

### Post by branko.savic on 2011-04-06
> **Quintilian said:**
> it sounds like he's using a hardware raid. if it's configured through the motherboard during bootup (after the POST) then it's generally hardware.

Yes, it is after the POST!

So how do we proceed now to format the drives?
He does not want to use them in raid anymore, just plain disks!

---

### Post by davidmohammed on 2011-04-06
press whatever key it says during boot to edit your RAID set.  You'll be able to break the RAID there.  Once done, ubuntu will see two separate drives.

---

### Post by branko.savic on 2011-04-06
> **davidmohammed said:**
> press whatever key it says during boot to edit your RAID set.  You'll be able to break the RAID there.  Once done, ubuntu will see two separate drives.

Ok thank you, I will try that!

---

### Post by branko.savic on 2011-04-06
> **branko.savic said:**
> Ok thank you, I will try that!

Another questuion!

We have a 2TB NTFS drive that does not show up under places!
It shows up if I go into the computer however!

How can I make it show up under places?

---

### Post by davidmohammed on 2011-04-06
suspect you'll need to get ubuntu to automount the ntfs drive - see [here]("http://www.psychocats.net/ubuntu/mountwindows") for a good guide

---

### Post by oldfred on 2011-04-06
Not sure if this applies to hardware RAID or not, but RAID drives hold meta data that interfers with normal installs. If you for sure do not want raid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Since you have some very large drives, you will be mounting data partitions anyway, you could also leave /home inside the SSD and link in the data partitions folders so that they look like a standard install.

There are several ways to do it. I just do linking. Others suggest direct mounting, or bindfs.

What formats will the other partitions be? If NTFS you also can link in folders:
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

Painless Linux Multi-boot Setup - see also comments on linking:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

### Post by branko.savic on 2011-04-06
> **davidmohammed said:**
> I would recommend / on the SSD to allow fast booting.

/home should be on your other drive

Its a judgement call for /swap - if you have a particular slow external drive have /swap on the SSD.  However - if the other drive is reasonable put /swap on that drive

I cant find how to set the swap drive?

I have configured the ssd as / and the harddrive as /home but how do I configure the /swap?

If I double click the drive it only shows the /home and I can not add anything, just change from /home to something else!

I am using the live dvd!

---

### Post by oldfred on 2011-04-06
You have to create a partition and set it as swap. For swap you do not have to specify anything else as swap just seems to know & work.

---

