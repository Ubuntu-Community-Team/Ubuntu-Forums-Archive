---
title: "How to format external drive for Linux and OSX?"
date: 2010-03-10
forum: General Help
---

### Post by drabina on 2010-03-10
I would like to format my new external hard drive (1.5TB) so it can be accessed on both Linux (Ubuntu) and OSX. Is that possible without using FAT system? If yes, what file system should I use?

I think I am using Ubuntu mobile on the Linux side (XBMC Live).

Thanks.

---

### Post by coffeecat on 2010-03-10
Ubuntu can read hfs+ (journalled) but not write to it, hfs+ being the MacOS filesystem. But it can read/write non-journalled hfs+. So one option would be to format the drive in MacOS with the non-journalled version of hfs+. Of course, that does mean you are using a non-journalled filesystem.

But - one warning. MacOS uses the same Unix permissions as Linux which are supported in hfs+ (obviously). You will encounter permissions problems. Your UID in Ubuntu will probably be 1000. The first created user in MacOS has a UID of 99. Probably the best way to deal with this is that when you save files in either Ubuntu or MacOS, to set the permissions of them to be read/write by all.

One alternative would be to install NTFS-3g on your Mac so that you have NTFS read-write on both machines. Advantages: no permissions problems, journalled filesystem, and you don't have the 4GB file limit of FAT32. Disadvantage: I wouldn't use NTFS if I didn't have Windows available to repair the filesystem if it became corrupted.

---

### Post by drabina on 2010-03-10
Thanks for reply.

I would need read/write capability so I guess I will go with NTFS. I do have access to Win machine just in case.

One more question. Does Linux (Ubuntu) support NTFS out of the box or I also need a plugin for it?

---

### Post by coffeecat on 2010-03-10
> **drabina said:**
> I would need read/write capability so I guess I will go with NTFS. I do have access to Win machine just in case.

Before you finally make up your mind, do you have a spare external drive you could experiment with to see if the non-journalled hfs+ option is workable for you? The permissions issue seems to be a bit hit and miss. When I was transferring files from MacOS to Ubuntu, sometimes I had "access denied" (solved with a bit of "sudo chowning") and sometimes not. It seemed that MacOS was setting the "all" permission differently at different times. I never did discern a pattern. Perhaps it was determined by the folder from which I was copying. I might look into it.

> **drabina said:**
> One more question. Does Linux (Ubuntu) support NTFS out of the box or I also need a plugin for it?

Ubuntu NTFS read-write has been reliable since about Hardy and it comes in the box. Simply plug your USB NTFS drive in and it will be automounted read/write with an icon on the desktop. For MacOS, I never did get around to installing ntfs-3g. I was about to when I upgraded to Snow Leopard (when SL first came out) only to discover there was a major incompatibility with ntfs-3g. But that was several months ago. I'm sure it's been sorted out by now.

But I do advise you to use NTFS only if you have Windows available for repair and maintenance.

---

### Post by drabina on 2010-03-10
This drive would be used as a backup for my HTPC as I just recently ripped all my movies and CDs. Don't want to lose them so I will just copy onto an external hard drive and keep it there. But just in case HTPC fails, I would like to be able to restore it onto my Mac so that's why I need dual OS capability.

I see that new version of ntfs-3g had been released in Jan 2010 so I guess most of the bugs are sorted out. I will definitely test the drive to make sure it is going to work on both systems.

Thanks.

---

### Post by coffeecat on 2010-03-10
> **drabina said:**
> I see that new version of ntfs-3g had been released in Jan 2010 so I guess most of the bugs are sorted out. I will definitely test the drive to make sure it is going to work on both systems.

Just to confirm - I've at last got around to installing ntfs-3g in Snow Leopard and it seems to be working just fine. I downloaded from:

[http://mac.softpedia.com/get/System-Utilities/NTFS-3G.shtml](http://mac.softpedia.com/get/System-Utilities/NTFS-3G.shtml)

You need to install MacFUSE Core first - a link is on that page.

It's worth reading the PDF manual in the ntfs-3g dmg. It explains about the pros and cons of caching when using ntfs-3g in MacOS and why performance is not as fast as in Linux.

---

### Post by drabina on 2010-03-11
Yesterday, I have formatted the drive NTFS and created a backup of my HTPC. It worked great from Linux. I can hold off on the ntfs-3g because I forgot that my Mac is dual boot and I have Win2000 installed on it. Thanks for the tip and information.

---

### Post by chowder on 2010-05-05
Along the same topic.  If I use ext4 for an external drive, can Mac read or write to that?

---

