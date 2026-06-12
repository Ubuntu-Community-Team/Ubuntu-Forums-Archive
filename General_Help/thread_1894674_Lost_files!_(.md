---
title: "Lost files! :("
date: 2011-12-13
forum: General Help
---

### Post by FuneralQueen on 2011-12-13
Hi friends

Hopefully someone can help me in this very saddening event :(

Basically I took some great photos with my DSLR, realized I had run out of space on the SD card and used my netbook (Running Ubuntu) to grab all the photos off as it was closer than my PC.

Once in Ubuntu, I then seperated the images into 2 folders - one as general pics, the other as super awesome photos that I thought were pretty awesome.

So I then transferred them onto a USB (both folders) and it went fine.

I then put the USB into my PC (Windows 7) and it recognized both folders, but when I clicked on the super awesome folder it said "Folder can't be accessed" or words to that effect. I safely removed the USB, put it back in my netbook, and now the folder isn't even there?!

How do I get my images back? I'm assuming they have to be somewhere on the system??

Thanks to anyone who can help :))

(They were photos of the eclipse recently in Perth so I'd love to get them back!!)

---

### Post by MartijnNL on 2011-12-13
I believe all ways to recover files are highly technical.

You could look at this page: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But one tip for future cases like this: if you transfer the files from the netbook to the USB, leave them on the netbook as well. And only delete them there when they are safely on your normal pc.

Are you sure the folders no longer exist on the netbook? Did you delete them after you copied them to the USB? Are they perhaps in the trash?

---

### Post by Mark Phelps on 2011-12-13
If the USB was formatted FAT or NTFS, and you're willing to spend some money to get the files back ... then read on:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) In Win7, download and install the trial version of GetDataBack for NTFS from Runtime Software.
2) Plug in the USB stick to this Windows PC.
3) Run GetDataBack in deepest discovery mode -- could take hours, so be patient
4) When done, check the recovery logs and see if GetDataBack was able to find your lost files.
5) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by pretty_whistle on 2011-12-13
Maybe they're not lost but just aren't showing up.

Did you try unplugging from USB, waiting 30 seconds or a little longer, then plugging it back in?

Sometimes this will fix it.

---

