---
title: "Disk errors: SMART Status: disk is being used outside design parameters"
date: 2010-05-19
forum: General Help
---

### Post by 98cwitr on 2010-05-19
Just did a fresh install of Lucid on my new SSD and got this:

[IMG]http://img.photobucket.com/albums/v673/98cwitr/Screenshot-60GBSolid-StateDiskAT-1.png[/IMG]

---

### Post by 98cwitr on 2010-05-21
bump

---

### Post by philinux on 2010-05-21
I would install gsmartcontrol from synaptic and compare the results. There has been reported bugs with palimpsest.

---

### Post by 98cwitr on 2010-05-26
dont have any self tests in the list for gsmartcontrol :?

---

### Post by PinguinZeneize on 2010-09-12
Hello!!!
):P
I have similar question
I have ubu 10.04 net remix installed on a CF16GB in an acer Aspire ONE.
when I REad this message was afraid :confused:
but I see that the system seems to work well ...

I'm glad to read any suggestion!

Thanks 

Excuse me for my "italian-EnglisH" !  ;)

):P

---

### Post by 98cwitr on 2010-09-13
4 months in and still running like a champ...still no issues, but I still have the errors (so I just turned off the notifications).

---

### Post by psusi on 2010-09-13
Looks like your drive is retarded and reporting bogus smart information.  Check for a firmware update.

---

### Post by 98cwitr on 2010-09-14
Cant...has to be an NTFS or FAT format for the firmware updater software to read the drive. :(

---

### Post by psusi on 2010-09-14
> **98cwitr said:**
> Cant...has to be an NTFS or FAT format for the firmware updater software to read the drive. :(

Huh?  It shouldn't care if there is ANYTHING on the drive.  Maybe you mean it is a windows utility so you have to have a windows install to run it?

---

### Post by 98cwitr on 2010-09-15
No, the utility doesn't see the drive. I was in windows at the time (UBCD) and I had the drive mounted via ext2fs and it was readable. I agree with you though, it shouldn't care...but it does :(

[http://www.mushkin.com/Digital-Storage/SSDs/MKNSSDCL60GB.aspx](http://www.mushkin.com/Digital-Storage/SSDs/MKNSSDCL60GB.aspx)

---

### Post by philinux on 2010-09-15
> **98cwitr said:**
> No, the utility doesn't see the drive. I was in windows at the time (UBCD) and I had the drive mounted via ext2fs and it was readable. I agree with you though, it shouldn't care...but it does :(

What about the manufacturers disk utility?

---

### Post by 98cwitr on 2010-09-15
> **philinux said:**
> What about the manufacturers disk utility?

see link in above post...it's window prop.

Thread started over @ Mushkin Forums 

[http://mushkingames.com/phpbb2/viewtopic.php?f=28&t=17546&sid=639f08a392ef8c6ea3d0410f75fab589](http://mushkingames.com/phpbb2/viewtopic.php?f=28&t=17546&sid=639f08a392ef8c6ea3d0410f75fab589)

---

### Post by whitelinux on 2010-09-15
I also have this problem, I bought two new ocz ssd drives and installed ubuntu on two separate computers and both are giving the same issue that disks are going to fail.

Is this because the SMART parameters for SSD are not set in ubuntu?

---

### Post by psusi on 2010-09-15
I have a 64 gig OCZ Vertex drive running firmware 1.5 and it works fine.

---

### Post by psusi on 2010-09-15
> **98cwitr said:**
> No, the utility doesn't see the drive. I was in windows at the time (UBCD) and I had the drive mounted via ext2fs and it was readable. I agree with you though, it shouldn't care...but it does :(

[http://www.mushkin.com/Digital-Storage/SSDs/MKNSSDCL60GB.aspx](http://www.mushkin.com/Digital-Storage/SSDs/MKNSSDCL60GB.aspx)

What is UBCD?  The utility does not try to read or write files on the drive; it communicates at a lower level, so you must have the wrong utility or something else.

---

### Post by 98cwitr on 2010-09-15
> **psusi said:**
> What is UBCD?  The utility does not try to read or write files on the drive; it communicates at a lower level, so you must have the wrong utility or something else.

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by 98cwitr on 2010-09-16
bump, after talking with the dude from Mushkin...Im sending it back in for uncapping and a firmware update...woo freakin hoo

---

### Post by whitelinux on 2010-09-16
After updating my bios and re-enabling hdd smart it has stopped reporting incorrect errors on both ocz vertex 2 drives in ubuntu

---

### Post by 98cwitr on 2010-09-17
> **whitelinux said:**
> After updating my bios and re-enabling hdd smart it has stopped reporting incorrect errors on both ocz vertex 2 drives in ubuntu

BIOS at newest version

---

### Post by soldier1st on 2010-09-19
use partedmagic to get a second opinion on your smart staus [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by 98cwitr on 2010-09-20
I assume the errors are not legit, but I just want them to go away (yes, I've hidden the notification, but still....)

Anyway, the SSD is in the hands of UPS on it's way to Mushkin to get "upgraded" to "deluxe" (ie: uncapping and firmware update).

I really should have formatted the thing first :? But I forgot

---

### Post by bigsuccess on 2010-11-09
Hi,

Was this resolved or does anyone else know?

I've purchased a OCZ Vertex II drive and installed 10.10 - bammm, same errors as the OP.

I decided to remove Ubuntu related partitions for the drive in order to update the drive firmware as apparently it doesn't like having complicated partitions/ext4 or something, so the firmware utility won't detect the drive.

Anyone else have any ideas?

[edit: Resolved for me by upgrading to Vertex II 1.2.3 firmware. The utility only runs in Windows and required for me to run as administrator and remove my Ext4 partitions first. Not an option for everyone but there it is.. I saw one guide where someone simply imaged the drive with dd, then removed the partitions, firmware'd it and restored his dd'ed image back onto it.. might be a solution for some.]

---

### Post by dcstar on 2010-11-09
> **bigsuccess said:**
> Hi,

Was this resolved or does anyone else know?

I've purchased a OCZ Vertex II drive and installed 10.10 - bammm, same errors as the OP.
..........

The SMART subsystem used by Ubuntu relies on knowing what particular value a drive reports means, and unfortunately drive manufacturers don't all seem to use a common standard for all the attributes.

Basically this needs to be reported as a bug to the developers so they can update the SMART software to monitor these particular drives accurately.

---

### Post by 98cwitr on 2010-11-09
Nope. Got the drive back with the firmware update (assumed) and uncapped....no change in performance nor the SMART errors (a few were different, but they were still prevalent). Got a free 2GB flash drive and a hat outta the deal though :)

---

### Post by w1ll1am on 2011-12-04
I just had this same thing happen to me right after a BIOS update and realized that I had disabled the S.M.A.R.T. feature in my BIOS and that my hard drive controller mode had been switched back to the default of IDE and not ACHI mode. No more errors now. Hope this helps someone else.

---

### Post by imwithid on 2011-12-19
My BIOS is updated to the latest revision. I received a pop up warning to backup all data and replace the disk. When I had checked the System Monitor's S.M.A.R.T. status which had an overall assessment of "DISK IS BEING USED OUTSIDE DESIGN PARAMETERS" but when I checked the S.M.A.R.T. data, the Seek Error Rate was off the charts with a red warning. There were no other issues, however, my system was running exceedingly slow. I was copying almost 200 GB of data from one eSATA drive to another eSATA drive while browsing and scanning (from a Firewire connected scanner) at the same time. The drive itself is new (only 2.0 days in operation).

I think it was this last operation that pushed the system over the edge and caused a false S.M.A.R.T. error. Accessing the eSATA from two devices may have caused some overflow error. I did notice in the System Monitor that all my RAM was used up and over 25% of the swap space was being used and climbing slowly. As soon as I killed the "simple-scan" process, everything went back to normal rather quickly.

I hope this is helpful to someone.

---

