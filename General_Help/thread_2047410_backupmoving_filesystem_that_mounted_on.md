---
title: "backup/moving filesystem that mounted on /"
date: 2012-08-24
forum: General Help
---

### Post by roimekoi on 2012-08-24
Hi,
when i first installed ubuntu(dual boot win 7), i partitioned it to /boot / and /home.
After installing ubuntu for a few months, one of my filesystem /dev/sda7 which is mounted on / is running out of space. 

i tried shrinking some space from win7 partition, 
from that free space i wish to create a new filesystem of 30-40GB and move the /dev/sda7 content over to the new filesystem and mount the new filesystem to /.so i would fallback on remounting /dev/sda7 back to / if the new filesystem fails..

is it possible to do that?
how is the steps?
if the steps involved typing in terminal as well as modifying some config files, is it possible to add some comment/ keywords on what does that do because im still learning and this will be much appreciated.

Thank you.

---

### Post by cortman on 2012-08-24
> **roimekoi said:**
> Hi,
when i first installed ubuntu(dual boot win 7), i partitioned it to /boot / and /home.
After installing ubuntu for a few months, one of my filesystem /dev/sda7 which is mounted on / is running out of space. 

i tried shrinking some space from win7 partition, 
from that free space i wish to create a new filesystem of 30-40GB and move the /dev/sda7 content over to the new filesystem and mount the new filesystem to /.so i would fallback on remounting /dev/sda7 back to / if the new filesystem fails..

is it possible to do that?
how is the steps?
if the steps involved typing in terminal as well as modifying some config files, is it possible to add some comment/ keywords on what does that do because im still learning and this will be much appreciated.

Thank you.

If I understand correctly you're trying to increase the size of the root partition? Very easy- but you must do it from a live CD. Boot up a live CD and open GParted. Locate the root partition, select to expand it.
But first, before you do anything else,

[U]**[SIZE=4]BACK UP YOUR DATA.[/SIZE]**[SIZE=4]
[/SIZE][/U][SIZE=2]
Before you even put the live CD in the drive. Seriously. :)
[/SIZE]_[SIZE=4][/SIZE]_

---

