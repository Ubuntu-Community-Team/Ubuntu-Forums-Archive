---
title: "HDD does not mount when restarting"
date: 2011-03-17
forum: General Help
---

### Post by victor9098 on 2011-03-17
I have two external HDD attached to my PC which start normally when I turn on the PC. When I restart (after an update for example) one of the two drives does not mount, always the same drive. It has always acted like this but I was wondering was there a way to fix this.

Currently running Ubuntu 10.10, let me know if more information would help

---

### Post by blueridgedog on 2011-03-17
So if you restart, one mounts and one fails to.  If you do a cold start, each mount.  In each case the drives remain powered and on regardless correct?

I would be curious to see the output of the following when typed in a terminal:

```
sudo fdisk -l
```

then:

```
mount
```

In each instance, just to see if the reluctant drive is actually seen by the OS.

---

### Post by victor9098 on 2011-03-17
> **blueridgedog said:**
> So if you restart, one mounts and one fails to.  If you do a cold start, each mount.  In each case the drives remain powered and on regardless correct?

I would be curious to see the output of the following when typed in a terminal:

```
sudo fdisk -l
```

then:

```
mount
```

In each instance, just to see if the reluctant drive is actually seen by the OS.

You asked, so I shall try to deliver.

Yes you are right with that summation. I have since tried adding both the HDD to Fstab manually, but now when I restart I get an error message saying that the 'problem drive' is not ready or not available, then to press a key to skip or attempt to mount manually.

---

### Post by blueridgedog on 2011-03-17
So, the external one that will not currently mount is not one of these:

/dev/sda5 on /home type ext4 (rw,commit=0)
/dev/sdf1 on /media/Jukebox type ext4 (rw,commit=0)
/dev/sdg1 on /media/Shadow type ext4 (rw,commit=0)

Correct?

What is the output of:

```
lsusb
```

---

### Post by victor9098 on 2011-03-17
> **blueridgedog said:**
> So, the external one that will not currently mount is not one of these:

/dev/sda5 on /home type ext4 (rw,commit=0)
/dev/sdf1 on /media/Jukebox type ext4 (rw,commit=0)
/dev/sdg1 on /media/Shadow type ext4 (rw,commit=0)

Correct?

What is the output of:

```
lsusb
```

The problem drive is 'Shadow' (my backup folder), sorry, should have said.

---

### Post by matt_symes on 2011-03-17
Hi

Is the drive that will not mount /dev/sdg1 ?

Kind regards

---

### Post by victor9098 on 2011-03-17
Looking at the output of lsusb I just noticed the file size for the maxtor drive (what I label as 'shadow') is incorrect. Should only be 500GB not 1TB. Do not know if that is significant :confused:

---

### Post by matt_symes on 2011-03-17
Hi

/dev/sdg1 or shadow has the boot flag set on it (i assume this is the drive that is causing the problem).

I was wondering if the boot flag was causing some kind of problem (Maybe in the bios). Try removing it.

/dev/sdg1 look fine in fdisk

> Disk /dev/sdg: 500.1 GB, 500107862016 bytes

Kind regards

---

### Post by victor9098 on 2011-03-17
> **matt_symes said:**
> Hi

/dev/sdg1 or shadow has the boot flag set on it (i assume this is the drive that is causing the problem).

I was wondering if the boot flag was causing some kind of problem (Maybe in the bios). Try removing it.

Kind regards

In Fstab at the moment I have:

> UUID=5137d402-5faa-4f27-be74-63aa41e82372 / ext4 defaults 0 1
UUID=84317423-3293-4868-beac-8198297a1fbf /home ext4 defaults 0 2
UUID=0f5b11d6-55ae-43b8-ad2a-e1cd5f41852d swap swap sw 0 0
UUID=01fab9d9-5dca-4d42-b18d-d3d908705449 /media/Jukebox ext4 defaults 0 2
UUID=20f66a4c-34dc-4481-9de5-43a31b557788 /media/Shadow ext4 defaults 0 2

Is this where I change the value or somewhere else?

---

### Post by matt_symes on 2011-03-17
Hi

> Is this where I change the value or somewhere else?

No. The best place to change it is probably from GParted. Make sure the disk is unmouted, select it, right click  and select "Manage flags". Untick the boot flag and close the dialog. Then press the big green tick button at the top. That assumes you have a desktop.

Kind regards

---

### Post by victor9098 on 2011-03-17
> **matt_symes said:**
> Hi



No. The best place to change it is probably from GParted. Make sure the disk is unmouted, select it, right click  and select "Manage flags". Untick the boot flag and close the dialog. Then press the big green tick button at the top. That assumes you have a desktop.

Kind regards

Ok, did what you suggested via Gparted. Restarted the system and it all worked perfectly. The drive mounted for the first time. Then I turned of the computer, started up, drive mounted as normal. Restarted again and the same error returned saying the drive was not ready.

Have just gone back into Gparted, clicked the unmounted drive and in the information section is just says "cannot have a partition outside the disk".

So it worked, but then went back to normal. Going to try again (turn on/off, then restart) just to check.

---

### Post by victor9098 on 2011-03-17
Just noticed in Gparted that the 'problem drive' has an unallocated section of 2.49mb, which the other external HDD does not have. Could this be the issue? Would a reformat of the whole drive be what this needs?

---

### Post by matt_symes on 2011-03-17
Hi

> "cannot have a partition outside the disk".

That's an odd message. Can you open a terminal and post the results of

```
sudo sfdisk -V /dev/sdg
```

Kind regards

---

### Post by victor9098 on 2011-03-17
> **matt_symes said:**
> Hi



That's an odd message. Can you open a terminal and post the results of

```
sudo sfdisk -V /dev/sdg
```

Kind regards

The output is:

> Warning: partition 1 extends past end of disk

---

### Post by matt_symes on 2011-03-17
Hi

> Warning: partition 1 extends past end of disk

Yes. That's an issue. I not sure if it's your main issue but that wants to be fixed. It can be fixed using sfdisk but i am no expert in that program. 

It's late here so i will let you google about sfdisk if you want to and see if anybody else here has used sfdisk more than i have.

If not i can try to give you a hand tomorrow.

Kind regards

---

### Post by victor9098 on 2011-03-17
> **matt_symes said:**
> Hi



Yes. That's an issue. I not sure if it's your main issue but that wants to be fixed. It can be fixed using sfdisk but i am no expert in that program. 

It's late here so i will let you google about sfdisk if you want to and see if anybody else here has used sfdisk more than i have.

If not i can try to give you a hand tomorrow.

Kind regards

Thanks a lot for all your help, really appreciate it. Late here too, so might resume with fresh eyes in the morning.

Thanks again!

---

### Post by blueridgedog on 2011-03-18
I recommend deleting the partition and then repartitioning the disk.  I can assist if that is the route you elect.  I believe it will turn out to be hardware failure though.

---

### Post by matt_symes on 2011-03-18
Hi

> I believe it will turn out to be hardware failure though.

This is quite possible. However you want to try to fix it, i would recommend running some SMART tests using smartctl after the partition has been fixed. 

As long as the disk is newish it should have smart data.

```
sudo apt-get install smartmontools
sudo smartctl -t long /dev/sdg
```

That will take a while to finish.

After it has finished

```
sudo smartctl -a /dev/sga
```

This will produce a report that can be posted back here.

But first the partition table needs to be fixed.

Kind regards

---

### Post by blueridgedog on 2011-03-18
A typo:

> sudo smartctl -a /dev/sdg

---

### Post by victor9098 on 2011-03-18
Sorry for the late response.

Last night I used gparted to reformat the drive and removed the unallocated space. I then left it to do a full backup of my system before leaving it.

This morning I went through the cycle of turning on then restarting and the problem still is present. At first it was because the wrong UUID values were in Fstab, so I deleted the two drives altogether. Then next startup everything mounted fine, but when I restarted the sdg drive still refuses to automount.

I have installed smartmontools and have it running a test now. It should not finish for about 116mins it said.

After that I will run the following command, but that might be later this evening but will post the results as soon as I can.

Thanks again for your help

---

### Post by blueridgedog on 2011-03-18
Also, change cables and ports between the drives, just be make certain that there are no issues.

---

### Post by victor9098 on 2011-03-18
Here is the output from the test. Also good idea about checking the cables. I unplugged the hub and connected to my laptop (running natty). Started up, saw all the mounted drives. Restarted and saw all the mounted drives. The error did not occur. Plugged back into my PC and sure enough, error happened again.

---

### Post by blueridgedog on 2011-03-18
I would also try the offending drive directly attached to the PC an another USB port.

---

### Post by matt_symes on 2011-03-18
Hi

I will have a look at your file soon. In the meantime reboot your computer and when the drive is not recognised open a terminal and type.

```
grep 'sdg' /var/log/syslog
```

Does that return any information that may explain why the drive is not being registered ?

It seems really odd behaviour. :confused:

Kind regards

---

### Post by matt_symes on 2011-03-18
Hi

As a quick aside, this is the first thing that strikes me about the file you posted.

> ==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931)
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951)
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957)

Have you checked out the links to see if they are relevant ? I have not had time to check myself yet.

Kind regards

---

### Post by victor9098 on 2011-03-18
> **matt_symes said:**
> Hi

As a quick aside, this is the first thing that strikes me about the file you posted.



Have you checked out the links to see if they are relevant ? I have not had time to check myself yet.

Kind regards

No I have not, going now

---

### Post by victor9098 on 2011-03-18
Some issues with looking up the links, they do not describe my drive, it is Maxtor and none of the serial or model numbers from the other providers match up with it.

Just restarted the system and attaching the output requested on sdg (had to split into 2 files due to size limits)

---

### Post by matt_symes on 2011-03-18
Hi

Reading through the smartctl file your drive looks all right. It passed and has not registered any errors apart from a temperature issue once.

Check out the firmware issues and also the syslog as i mentioned in the post above.

Kind regards

---

