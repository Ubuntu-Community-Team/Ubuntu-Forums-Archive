---
title: "Mounting UDF Volume"
date: 2010-10-15
forum: General Help
---

### Post by colintivy on 2010-10-15
Hi Folks!

I have run into a problem when attempting to to open and view the contents of DVD containing data from an Excel/Windows program. This states that it is apparently in UD Format which does not seem to be digestible to Open Office 2.4.I have not met this before and other Excel stuff does work correctly.

Any clues as to how to open and run this???

---

### Post by TeoBigusGeekus on 2010-10-15
Have you tried copying the contents of the dvd to your hd and accessing them from there?

---

### Post by colintivy on 2010-10-18
Thanks for that. The problem (see title) is that I cannot mount the disk and hence cannot do anything with it. Older Excel files are in.xls format and are no problem at all. My guess is that Bill has changed the extension in Vista and/or Win 7 so that users of older versions have to stump up for the newer one....maybe I am cynical? 

I hope to try the DVD in a newer machine this week and see if that helps. I will then try to save the contents to .xls and burn a new disk; unless Bill has made sure that cannot happen. All a bit sad as the contents are the accounts of an organisation of which I am Chairman and our new Treasurer wants to get on with this month's numbers!

Ho Hum, no peace for the wicked.

---

### Post by srs5694 on 2010-10-18
The *filesystem* format (ISO-9660, UDF, ext3, ext4, etc.) has absolutely nothing to do with the *file format* of the files it contains (.xls, .tif, .mp3, etc.). (Although there can be file-size issues, filename issues, and some other subtleties related to file metadata.) Mounting is a filesystem-level operation carried out by the mount utility (or GUI front-ends) and the kernel. File access is handled by applications like OpenOffice.org.

Your message title refers to mounting, but the details in both your messages refer to file-level operations. I believe you need to review and clarify.

If you can't mount the disc, then try specifying the filesystem type explicitly, as in:

```

sudo mount -t udf /dev/dvd /mnt

```

This example mounts the optical disc /dev/dvd at the /mnt mount point, using filesystem type udf.

If you can see a listing of files on the disc using ls or a GUI file browser, then it's almost certainly mounted correctly, and any remaining problems relate to the file format. (In some cases, file formats can be corrupted depending on mount options, but I've never heard of this happening with UDF.)

---

### Post by colintivy on 2010-10-19
Understood, wrist slapped for being obscure. I had not met this file type before. I will try your possible fix when I have some time...it looks promising. My clue to the problem is that when I try to access the drive, an error message comes up immediately "Cannot mount UDF Volume", which is not seen when accessing anything else, all of which behave quite normally. I am sure that the disk was burnt on a recent machine using one of the recent versions of Windows, but I am using 8.04 right now pending the time to try 10.04 or its later download. Separate Home needed before tackling that!!

---

### Post by WanderingAlbatross on 2010-10-25
I have the same problem.  I tried your suggestion.  I get:

mount: no medium found on /dev/sr0

(My device is sr0 on my system.  It does recognize it's existence.)
The DVD I have in there is a commercially produced DVD.  Perhaps it is encoded.  The really weird part to me is that VLC will play it without mounting it.  Since that was all I was trying to do I am happy, but I can understand why you would want more.

Other DVDs mount fine.

---

