---
title: "mdadm recovery"
date: 2010-02-27
forum: General Help
---

### Post by gencha on 2010-02-27
Backstory:
So, a few days ago, I added a new drive to this mdadm raid5 array, bringing it to a total of 6 disks. After the reshaping process and the filesystem expansion was complete I noticed that one drive was listed as "faulty spare".

I assumed it was the new drive. Although I am not even sure about that anymore as I have now noticed that under certain circumstances the /dev/sd_ mappings seem to change after a reboot.

Nevertheless, I replaced the new new drive and booted back up only to find a more confusing situation. The raid was shown to consist of 4 drives. So I thought I better at least switch the disks that I had just replaced back to hopefully get back to the previous state. In the process of putting the drive back in, I must have accidentally removed the power from another drive.
So when I booted back up, the raid showed only 5 drives.

I have now all the drives back in place and they seem to work technically fine.

Problem:
During the above, I have once run
```

/dev/md0 --verbose --level=5 --raid-devices=6 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf

```
So that pretty much removed the info of the old raid structure.
Now that I have all the original drives back in place, I was hoping I could simply re-create the array again. Sadly after doing so, mount tells me there is no filesystem on them. fsck also complains about invalid superblocks:
> 
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/mapper/crypt


During the process I have read several texts describing similar issues that often could be solved by re-creating the array with the drives in another order (to find the original order of the array). I have tried only 3 combinations yet. Only 3 of the drives are candidates for the first one. And I assumed if I get the first one right, at least a filesystem would be detectable.
This assumption does not seem to be correct so far.

So before giving up completely and accepting the fact that the data may be lost, I thought I would consult with you :)

---

### Post by gencha on 2010-02-28
I just wanted to say that the issue magically resolved itself. I re-created the array yet again with --assume-clean, with the drives in alphabetical order. Just to see if this would start a recovery as well. Sure enough it didn't.
Just for the sake of it I tried mounting the raid. It worked. And all the data was intact.
Even the drive that was marked as "faulty spare" after the reshape is now listed as "clean".

I guess I just got a little confused and acted too hastily. mdadm never fails to provide :)

---

### Post by tgrimley on 2010-03-02
Glad you fixed your problem.  After you installed all the original disks what you should have done is try to _assemble_ the array, not re-create it.  Creating is a potentially bad and destructive process if there is data you were wanting to keep :)

---

### Post by gencha on 2010-03-02
In fact, that's the first thing I tried. But it failed. Although at this time I can't recall any details about the failure.
But I was used to assembling the array. Creating it was kind of a last measure.
I am still amazed that all the data is still there.

---

