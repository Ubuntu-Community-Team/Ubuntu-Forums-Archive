---
title: "Problems with CIFS shares"
date: 2010-08-27
forum: General Help
---

### Post by mindless1973 on 2010-08-27
Hi,

My system: Ubuntu 10.04 up to date

Since a few weeks I have the following problems with CIFS shares from my (Samba based) NAS device:

All CIFS shares have an entry in /etc/fstab:

```


//192.168.130.13/software	/media/software		cifs	user,credentials=/home/marcus/cifs_credentials,iocharset=iso8859-1,uid=502,gid=502	0	0

```

All shares are correctly mounted during boot and I can work on them.

However, I experience to major problems:
1.) Automount for later attached USB devices or SD/MMCards are not working an more (I can mount them on Nautilus/Computer/SDCard)
2.) In Nautilus I have double entries for all CIFS shares in the left panel, but only one entry per share is working. When I click the (not working) entry, I get an error message that his share is already mounted.

When I am not connected to my home network, so my CIFS shares are not reachable, automount of removeable drives works like a charm, so I expected something to break during the mounting of the CIFS shares in the boot process. 

So, I put a "noauto" to the mount options in /etc/fstab. 

Now, automount of removeable drives works fine - I only have single entry per share in my Nautilus left panel - BUT when I click on this entry, or try to mount the CIFS shares as a user, I get again an error message "Unable to mount".

It seems that you can't mount CIFS shares as a user even if you have that specified in the mount options of /etc/fstab. Adding the SetUID bit to /sbin/mount.cifs did also not work.

So, here I am, any help welcome!

bye
Marcus.

---

### Post by andrew5152 on 2010-08-27
Hello 

 I am andrew As the relationship progresses, however, it becomes clear that     there is a lot going on beneath the candy-coated surface.  This is     particularly true of the CIFS protocol suite.  The Network     Neighborhood icon that appears on the Windows desktop hides a great     deal of gear-churning and behind-the-scenes fussing.      
The large installed base of Microsoft's Windows products has     granted *de facto* standard status to CIFS.  Unfortunately,     implementation documentation and detailed protocol specifications are     scarce, incomplete, and inconsistent.  This is a problem for network     administrators, third-party CIFS implementors, and anyone else who     wants to know more about the ingredients than is described on the     bottom of the box. 





___________________________________________________
   [Earn an Extra   $1000 to $1200 per month doing Part Time Data Entry Jobs! Work from home data   entry jobs to post simple data submissions on Internet. Make $1 per entry.   Easy form filling, data entry and ad posting jobs. No selling, No phone   calls, No Marketing. No Investment. Bi-weekly payments. Full Training   Provided. Pls   visit: [url=http://www.dataentrywork.net/?id=26201] Data-Entry ]("http://www.dataentrywork.net/?id=26201")[/URL]

---

