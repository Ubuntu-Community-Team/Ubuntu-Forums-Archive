---
title: "Changing the /home partition"
date: 2012-02-05
forum: General Help
---

### Post by joey9801 on 2012-02-05
Right, this is a problem which has stumped me for the last day, and I've finally conceded defeat.

When I installed ubuntu on the family computer I put /home on a separate partition, just to help keep things organized. Not knowing what I was doing at the time, I had made all of the partitions primary partitions (which it turns out you can only have 4 of), and now we've run out of them...

Basically what I've been trying to do (and failing miserably), is to get the /home folder back onto the main ubuntu partition. I've found a few guides on the 'net about how to do the opposite, but I'm not competent enough to attempt it this way round :/

Thank you in advance for any help :3

Joey9801

---

### Post by dcstar on 2012-02-06
> **joey9801 said:**
> Right, this is a problem which has stumped me for the last day, and I've finally conceded defeat.

When I installed ubuntu on the family computer I put /home on a separate partition, just to help keep things organized. Not knowing what I was doing at the time, I had made all of the partitions primary partitions (which it turns out you can only have 4 of), and now we've run out of them...

Basically what I've been trying to do (and failing miserably), is to get the /home folder back onto the main ubuntu partition. I've found a few guides on the 'net about how to do the opposite, but I'm not competent enough to attempt it this way round :/

Thank you in advance for any help :3

Joey9801

```
sudo mkdir /home2
sudo cp -r /home /home2
sudo gedit /etc/fstab
```
and comment out the existing /home entry, save the file.

Boot off a Live CD/USB and then copy all the contents of /home2 on the hard disk partition to /home on the same partition.

Reboot normally and see how things go, if they seem ok then delete the /home2 folder and eventually the partition that used to be /home.

---

