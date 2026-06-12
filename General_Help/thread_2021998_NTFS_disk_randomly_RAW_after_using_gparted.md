---
title: "NTFS disk randomly RAW after using gparted"
date: 2012-07-10
forum: General Help
---

### Post by captaintorche on 2012-07-10
Hi everybody !

I have installed two new disks on my computer : one 128Gb SSD, and one 1.5Tb HDD.
I installed both Vista and Ubuntu on the SSD.

Under Vista, the second drive wasn't detected at full capacity (Only 900Gb were detected), so I used gparted to extend the NTFS partition.

Soon after that, I randomly had issues : when starting Windows, the disk is sometimes not recognized, and shows as RAW.
When I start Ubuntu, and then go back to Windowss the situation goes back to normal.

Gparted told me I had a problem with the clusters : I had three error messages telling "Missing cluster in $Bitmap".
I did a chkdsk /f on windows and these errors seem to be corrected, but I still have the same problem : when booting Windows, the disk is sometimes not recognized.

What could I do to fix the problem (Apart formatting, of course) ?

---

### Post by HermanAB on 2012-07-10
Note that when you dual boot, ensure that the Windows and Linux systems will never suspend/hibernate.  Otherwise the file system will be messed up when it was modified by the other system in between suspend and resume.

Dual booting is a rather archaic idea dating back to the previous century - rather use Virtualbox.

With NTFS, the only way to fix errors is with the Windows checkdisk program, so boot Windows and run that ASAP.

---

### Post by captaintorche on 2012-07-10
I never use hibernate on both of the systems.

And I already did a checkdisk.

---

### Post by Nixarter on 2012-07-10
> **captaintorche said:**
> 
And I already did a checkdisk.

... well there's yer problem!

That program is probably the single biggest cause of lost files and drives that exists!  It just corrupts stuff randomly.  Hope you had a backup lol

If not, that program just gave you hours upon hours of play time with recovery software.  And that's if you are lucky.

For future reference, any time you suspect corrupt data or partitions, whatever you do, do NOT run that program.  Google about it... it's horrible.  Always do a dd of it and work on the image.  Then you can run check disk on that if you want.  In the unlikely event that it works and doesn't kill files or corrupt the drive, do it on the original.

Unfortunately this is one of those lessons that people learn only after they have screwed up... and every windows user learns it eventually :(

---

### Post by captaintorche on 2012-07-10
Well, there were two problems : one linked to checkdisk (Missing cluster in $Bitmap), that seems to be corrected, and another one (The disk randomly appearing as being RAW on Vista), whick was there before and after I ran checkdisk.
That's this second problem I want to solve.

---

### Post by SlugSlug on 2012-07-10
If possible move the data off the 1.5 and reformat it.

Otherwise you could try testdisk and re-write the partition table -- but BACK UP!

I've used chkdsk a lot and never had any problems with it

---

### Post by jmore9 on 2012-07-10
I have used chkdsk alot on winxp and win 7 .  Always worked for me.  Never any problems.  But i did have problems when win 7 would give blank screen and then the machine would just shut off and not leave any error logs.  It did not unmount the partitions like it was supposed to ( but it crashed ) and when i went into ubuntu it had problems with the NTFS partitions.

I don't use any wndows stuff any more ( 2 days ago ) all machines are linux now , but windows being shut off with the power button or random shut down will cause linux as well as windows itself , to have problem with the NTFS file systems.

And you always should use the proper disk checker from the os when problem occur , in my opionin.

---

### Post by captaintorche on 2012-07-10
> **SlugSlug said:**
> If possible move the data off the 1.5 and reformat it.

Otherwise you could try testdisk and re-write the partition table -- but BACK UP!

I've used chkdsk a lot and never had any problems with it
Ok, I'll try to backup the most important files before doing so.

---

### Post by Nixarter on 2012-07-10
> **captaintorche said:**
> Well, there were two problems : one linked to checkdisk (Missing cluster in $Bitmap), that seems to be corrected, and another one (The disk randomly appearing as being RAW on Vista), whick was there before and after I ran checkdisk.
That's this second problem I want to solve.

The thing is, check disk consults the partition tables and MFT, so if they are corrupt (reading that the data is RAW), check disk is like.. ohh, this data shouldn't be here.  Delete.  Problem solved.  Then you have to go find data with missing headers, if it didn't corrupt the data in the first place.  If everything is good, then itworks... but if there is damage or corruption in certain major areas, check disk wreaks havoc.  Hopefully you were spared...

But yeah, get as complete of a backup as possible from dd.  Then reformat... but it is important to do a "complete" reformat.  This ensured that if there are any bad sectors they don't come back to bite you later with the same problems.

I made that mistake once... I "quick" reformatted and installed and thought everything was peachy, but true bad sectors corrupted my stuff again.  It was a PAIN to get back.  sometimes bad sectors are the first sign of a failing drive. If you have them I say bite the bullet and get a new drive.  You can get 2tb's for under $100 now, so it's not that bad.

---

