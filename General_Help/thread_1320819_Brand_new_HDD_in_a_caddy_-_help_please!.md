---
title: "Brand new HDD in a caddy - help please!"
date: 2009-11-09
forum: General Help
---

### Post by alecspoons on 2009-11-09
I've just bought a brand new HDD and a USB caddy to put it in to use as an external HDD (for backing up data).

It looks like the HDD is being recognised (i.e. in GParted it is listed as /dev/sdg) but I can't access it. GParted says it's file system is unallocated and it says disclabeltype is unrecognised.

What do I need to do, please?
Should I be formatting my new drive?
What is the least painless method?

Thanks!

---

### Post by doas777 on 2009-11-09
just create a partition with gparted and you shoudl be ready to go

---

### Post by shaggy999 on 2009-11-09
> **alecspoons said:**
> I've just bought a brand new HDD and a USB caddy to put it in to use as an external HDD (for backing up data).

It looks like the HDD is being recognised (i.e. in GParted it is listed as /dev/sdg) but I can't access it. GParted says it's file system is unallocated and it says disclabeltype is unrecognised.

What do I need to do, please?
Should I be formatting my new drive?
What is the least painless method?

Thanks!

'Unallocated' means you have not formatted any partitions on it yet. Use gparted to do that.

---

### Post by alecspoons on 2009-11-09
Thanks for your replies.

One other thing, and then I think I've got it:

When I start to create a new partition owith GParted, it tells me that the default is to create an msdos partition table. 

Is this the right choice?

Thanks again.

---

### Post by doas777 on 2009-11-09
yeah, use ms-dos for your partition table type. then I would use ext4 for the partition format, but that is up to you. Just don't select NTFS. It's always a good idea to create your partitions with whatever system will run them natively (so format ntfs from within windows, not ubuntu).

good luck

---

### Post by alecspoons on 2009-11-09
Thanks.

I'm trying that right now - using GParted to create a new partitio using ext4 as the new partition format.

I'm a bit worried because nothing much seems to be happening at the moment...GParted is 'applying pending operations' with 0 out of 1 operations completed and the bar going backwards and forwards.

Hope this is normal...

EDIT: This is infuriating - I have absolutely no idea whether anything is happening. I don't know if everything has stopped or if it is simply taking ages!

---

### Post by doas777 on 2009-11-09
if it's a TB+ disk, then it will take a while, expecially since USB is a slow connection (15-20MB/s write time).
on the upside, even if you abort, since you don't have any data on it, you haven't lost anything but time.

---

### Post by alecspoons on 2009-11-09
That's useful to know.

It's not a TB+, but looking around I've seen plenty of other people complaining that GParted takes a long time!

I shan't give up for a while yet, but at least I know I can stop and try another day without causing any harm.

---

### Post by alecspoons on 2009-11-09
Right - as I'm on the verge of pulling off my own eyebrows (I've read some people say GParted has taken DAYS to finish), I'm going to walk away and do something else.

I wish GParted would give some sort of clue as to where it's got in the process.

---

### Post by alecspoons on 2009-11-09
OK - now GParted has finished and I can see the drive on the desktop when I plug it in, but....

I can't copy anything onto it?!!

Like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135522&stc=1&d=1257803618[/IMG]

Now what do I do?

Please!

---

### Post by alecspoons on 2009-11-09
Think I have sorted it.

Did:

gksu nautilus

in Terminal to run Nautilus as root, then changed the permissions for the drive. Seems to allow me to read and write to the drive now. I've unmounted it and then re-mounted it and it seems to stick. I haven't got time to do it now, but I will see whether it still works after a re-boot!

Hope that's it solved, but I'm not holding my breath. Not yet!

---

### Post by doas777 on 2009-11-09
sounds like it is working for ya! great news!

---

