---
title: "Rescue / testdisk / ddrescue help"
date: 2010-03-23
forum: General Help
---

### Post by kleptik on 2010-03-23
Hello,
my configuration
drive 1 = 500 gb hard drive - failing
drive 2 = 1tb external usb hdd (NTFS) - target drive for restoring to

Not understanding GNU ddrescue I have put my external at risk now.
The 1tb external allready have about 500 gigs of good data on it. (From previous backups).

I was running ddrescue and somehow I have now messed up my 1TB drive.

The command I ran was similar to:
sudo ddrescue -r 3 /dev/sda /media/usbdrive/image /media/usbdrive/logfile

the error I got was that the drive is full. :)  What it appears to have done is partition my 1tb drive in to two 500gig drives in preperation for writing data to it. This is not what I thought it would do, I thought it would create a large log file that I could then restore data out of. Now I have two empty 500gig partitions.

Can someone please elaborate on what the state of my 1tb drive is, and provide some guidance in using testdisk to restore it back to what it was, 1 TB partition with all of my older data on it.

Hope this made sense.

Thank you so very much.

---

### Post by kleptik on 2010-03-23
Hmm, possibly this is the incorrect forum for an answer. I didn't have much luck finding a popular recovery forum, anyone know of one?

Thanks!

---

### Post by mechro on 2010-03-23
I'm not familiar with ddrescue so I'm not sure what's happened. I've had a quick read about ddrescue and the only thing that springs to mind is that there wasn't enough space for it to work. Bearing in mind you have 500GB of good data, that leaves only 500GB to copy a 500GB drive so a few Gigs either way is going to be a close run thing.

I'd give testdisk a go but first can you post the result of **sudo fdisk -l** with the external drive connected?

---

### Post by kleptik on 2010-03-23
> **mechro said:**
> I'm not familiar with ddrescue so I'm not sure what's happened. I've had a quick read about ddrescue and the only thing that springs to mind is that there wasn't enough space for it to work. Bearing in mind you have 500GB of good data, that leaves only 500GB to copy a 500GB drive so a few Gigs either way is going to be a close run thing.

I'd give testdisk a go but first can you post the result of **sudo fdisk -l** with the external drive connected?

Thank you for the response.

Yes, I also looked and can't seem to get much detail with how ddrescue works. My estimates on space were rough. I think I had ~600gig free space on the destination drive. The source contained about 400gigs.

What I think may have happenned is the command I used might have attempted to clone the hard drive onto the external, ie, partitions etc.

I have started testdisk on the external drive and it has been 'recovering' the files to another external drive for about 5 hours at this point. It appears to actively be copying, but damn, seems slow.

I will provide an fdisk -l as soon as this stops, but I presume I will be okay at this point.

Thanks again.

---

### Post by mechro on 2010-03-24
I can understand ddrescue "cloning" but the command you said you used suggests creating a file rather than cloning a device.

If you're already using testdisk then no need to bother with the sudo fdisk -l. I only wanted that to get an idea of what ddrescue had done to your drive.

Hope all goes well with the testdisk recovery.

---

