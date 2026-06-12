---
title: "NTFS permissions issue?"
date: 2009-08-21
forum: General Help
---

### Post by mbuehl on 2009-08-21
I'm not sure if this'll fix my problem, but I'm new and it seems like a good place to start. 

I finally got WINE running, sorta... I think it runs though I haven't been able to verify. I have a drive which is formatted with NTFS, but when opening the game I get random errors that seem to be I/O related.

After perusing around the web I found the command:

/dev/sda5 /windows/D ntfs-3g defaults,force 0 0
I was wondering if someone could explain this command to me, and also how to use it. I have a number of partitions (5 in total, 4 non-swap) on my main 500g harddrive, all of which are ext3 formatted, and one 40 gig harddrive I backed up some stuff to before removing windows from my system and installing ubuntu, formatted NTFS.

How does the sdax (assuming this is a correct term) hierarchy work as far as labeling goes?

I kinda get the whole /dev/sdax thing, is the next physical drive /sda1? or does it just increase by partition?

Also, in order to "mount" something with certain permissions, do I have to unmount it first? How do you unmount at the command line? I can right click the icon and do it like that, but just out of curiosity I'm sure there's a way! And just to clarify.. what is sda, and what do hda/sda stand for?

Thanks ahead of time... =)

-m

---

### Post by mbuehl on 2009-08-21
okay, well I found where it allows you to set mount permissions.

I pasted the 
/dev/sda5 /windows/D ntfs-3g defaults,force 0 0

in...

and now it wont mount at all! hah. How do I undo these permissions?

---

