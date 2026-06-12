---
title: "I crated an encrypted /home. How do I shred the old one?"
date: 2010-05-31
forum: General Help
---

### Post by Old_Grey_Wolf on 2010-05-31
I am using Ubuntu 10.04.

I created a new user account with an encrypted /home. Then I copied everything from the "old user's" /home to the "new user's" /home. Got everything working eventually. I then deleted the "old user's" /home, and account.

It occurred to me that someone could use some data recovery tools, like photorec or testdisk, to recover the unencrypted files from the "old user's" deleted /home.

Is there are way I can overwrite the deleted "old user's" /home files so they can not be recovered easily?

---

### Post by harrismh777 on 2010-05-31
> **Old_Gray_Wolf said:**
> I am using Ubuntu 10.04.
[snip]
Is there are way I can overwrite the deleted "old user's" /home files so they can not be recovered easily?

You might have used the DD command to write nulls 00 to the files rather than deleting them... but alas.

So, you can back off the files in the new /home to some removable media (external usb whatever) and then startup the system in as single user root shell. 

Unmount the /home directory and then use the DD command to write nulls 00 to the device that /home was mounted over. 

oops ,  don't tell me...   you don't have a separate partition for /home either, do you?

Well, in that case, you are going to have to recover those nasty beasties. And after you do, use the DD command to write nulls 00 over them
and then delete them again.

---

### Post by Old_Grey_Wolf on 2010-05-31
> **harrismh777 said:**
> You might have used the DD command to write nulls 00 to the files rather than deleting them... but alas.

I already know that I should have done that in the first place; however, I didn't. My original intent wasn't concerning physical possession of my laptop. I was wanting to learn about any performance differences when using encrypted disks. I am now planing to take a trip, and want to secure the laptop if it is stolen.

> **harrismh777 said:**
> So, you can back off the files in the new /home to some removable media (external usb whatever) and then startup the system in as single user root shell.

As you can see from my signature, I recommend a backup before making changes to your system.

> **harrismh777 said:**
> oops ,  don't tell me...   you don't have a separate partition for /home either, do you?

Well, actually I do have a separate /home partition.

> **harrismh777 said:**
> Well, in that case, you are going to have to recover those nasty beasties. And after you do, use the DD command to write nulls 00 over them and then delete them again.

You haven't actually tried to help me with this. It seems that you just want to show off your superior knowledge. I'm looking for a simple way to work around this issue. I know I can shred or DD the disk and reinstall with encryption enabled; however, that is a PITA.

---

### Post by louieb on 2010-05-31
Files are now  deleted so its now free space you want to wipe - its that right?

a search in Synaptic for "wipe free space" brings up** bleachbit **and** secure-delete **

have not used either - but have see good things written in this forum about bleachbit.

lol - got some stuff I need to remove all traces of myself -

---

### Post by Old_Grey_Wolf on 2010-05-31
> **louieb said:**
> Files are now  deleted so its now free space you want to wipe - its that right?

a search in Synaptic for "wipe free space" brings up** bleachbit **and** secure-delete **

have not used either - but have see good things written in this forum about bleachbit.

lol - got some stuff I need to remove all traces of myself -

Thank you, I will look into those options.

---

### Post by harrismh777 on 2010-05-31
> **Old_Gray_Wolf said:**
> 
I know I can shred or DD the disk and reinstall with encryption enabled; however, that is a PITA.

Its a good thing to have a separate partition for /home, so good job.

The only way to make sure that the old /home is not recovered by any means is to  DD  nulls over the partition and then remake the file system on that device.  I am serious.  And I am sorry ...  I know its a PITA... believe me. But there really is no other way than to write zeros over the space (the whole space) and then create a new file system over that space. 

But I should also tell you that theoretically, even if you do write zeros over the space, it is still possible to read the residual first writes if the person who steals the laptop has the right equipment... but they would need to be working for the NSA, or other. Not likely. 

No, the way to make sure is to write zeros over the old partition. 

:popcorn:

---

### Post by Ubuntist on 2010-05-31
> **Old_Gray_Wolf said:**
> I was wanting to learn about any performance differences when using encrypted disks.

BTW, what are your conclusions regarding the effect on performance of an encrypted disk?

---

### Post by mkvnmtr on 2010-05-31
I use secure delete from time to time. What you want to wipe your free space is sfill. After you have installed secure-delete and wipe do man sfill. What I do is use the -r -v -l -l options. one pass is enough. Do it an night. It takes a long time. The idea of doing 35 passes might take a week. 
Secure delete also gives you programs to wipe the memory, swap and of course any file. It is a good program.
Alos you might wish to look at your .cache and .thumbnail files.

---

### Post by _H3MLOCK on 2010-05-31
You evidently are aware of shredding and wiping with random data, but you apparently just need to know what to shred. If you had kept track of the blocks or if the old /home space is now unallocated, then you can use clonezilla to random wipe specific blocks on a hard disk and then zero them out.

---

### Post by Old_Grey_Wolf on 2010-06-01
> **Ubuntist said:**
> BTW, what are your conclusions regarding the effect on performance of an encrypted disk?

Without actual benchmarks, it seems that operations involving writing to the disk are a little slower; such as update manager, however not by enough to annoy me. The variation in download speed is far more annoying.

---

