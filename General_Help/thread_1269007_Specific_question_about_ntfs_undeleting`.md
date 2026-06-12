---
title: "Specific question about ntfs undeleting`"
date: 2009-09-17
forum: General Help
---

### Post by morganpatrick on 2009-09-17
OK I'll try to break this down as simply as possible:

I reformatted a friend's ntfs hard drive and split it into two partitions.

On the original disk, there was a program called Fundraiser Professional, a proprietary program that I reinstalled now that I reinstalled XP.

She didn't back up the data for this program. The data resided in C:/Program Files/Fundraiser Professional/data. All the files have obscure extensions: adi, adm, adt.

Now: What is the best way to undelete what she had before? Testdisk? Photorec? Knoppix?

The issues are as follows: The hard drive was reformatted, there are a bunch of new files in the path where the old files resided, and the files are unusual formats. In the past I've seen recovery software that can look at headers to guess the filename or do a mass undelete.

Given my situation, what would be the best program to use?

THANK YOU!

---

### Post by undecim on 2009-09-17
Well, I have good news and bad news for you.

The good news is that if you reformatted the drive and haven't touched it since, the data is more than likely still there (unless of course, the program you formatted it with zeroed the drive first, or if the filesystem overwrote it with any various bookkeeping datas). though, even if you have messed with it since, part of the data might still be there.

The bad news is you need some information about the files you are trying to recover. Most recovery programs look for specific patterns (for example, JPEG images), and others will dump contiguous blocks of unallocated data (data existing, but not marked as being used in a file). Since none of the blocks are used in files anymore, there will be a lot of blocks like that...

If the data is mostly text, the best thing to do would use a livecd and search the drive the device in /dev/ (using the grep command maybe? I don't know how that would work on a hard drive) for the text you need.

If you REALLY need this data, I think the only way to get all of it back within any reasonable amount of time would be to send the drive to a professional data recovery service.

---

### Post by morganpatrick on 2009-09-17
Thank you for your reply.

I have told her to stop using that computer because we might have a solution and the more she uses it, the more likely she is to overwrite the data.

I also just discovered that adi, adt and adm files are Sybase Advantage Database Server files. I don't know if that makes them any less exotic.

Any help would be greatly appreciated.

---

### Post by morganpatrick on 2009-09-18
bump

Now that I have identified the file types, does this make it any more likely I can restore this data? Do I simply need to know the file type or do I need to find a tool that will search for patterns for my specific filetype? I looked at one of them (I think photorec) and it looked like the method was to search for popular filetypes (jpg, txt).

---

### Post by ubongo2008 on 2009-09-18
well i never used testdisk but have seen people around here who have been successful with that application.  i also had some problems with defect hard-drives in the past. If the journal/file-allocation-table or whatever you wanna call that is still intact then you won't need raw-recovery which will only be able to recover known file types.  since i never used testdisk i can't recommend or abuse it but there are some commercial apps out there with which you can test the condition of the partition.   they often support both recovery by usage of file system tables or rar recovery.  to find out which recovery type you'll need you may try an such a demo version   maybe here is someone who used testdisk or an other linux tool after accidently formating and repartitioning. If you did an &quot;full=zeroing everything&quot; formating i would say that your chances aren't that good to get your data back but don't hesitate just give it a try in any case  I had some great success with an commercial recovery tool but it is on an computer to which i haven't access right now coz i don't have an gfx-card for it at the moment.

---

### Post by ubongo2008 on 2009-09-18
edit: was offtopic

---

### Post by morganpatrick on 2009-09-18
if i reformatted and repartitioned, would the journal still be there?

---

