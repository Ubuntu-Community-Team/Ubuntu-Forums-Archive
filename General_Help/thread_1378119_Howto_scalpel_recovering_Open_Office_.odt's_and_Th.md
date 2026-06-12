---
title: "Howto scalpel: recovering Open Office .odt's and Thunderbird Local folder data"
date: 2010-01-11
forum: General Help
---

### Post by jchedstrom on 2010-01-11
What follows are some anecdotes from my successful disk carving adventure and some tips for using 'scalpel' to retrieve Open Office (odt) and Thunderbird local mail files.

IMPORTANT: UNMOUNT YOUR DRIVE IMMEDIATELY OR RISK LOSING WHAT LITTLE CHANCE YOU HAVE AT RECOVERY. If you think your disk is failing, first make an image with a utility such as 'ddrescue' to perform forensic analysis on.

Useful recovery terminology:
  partition recovery - maybe your partition was corrupted or you repartitioned incorrectly, your partition tables are lost but hopefully not deleted, I recommend 'testdisk'
  carving - you are in big trouble and need every single byte of your disk analyzed and carved up into *guesses* at what files are there

After screwing up a backup and then botching an attempt at encrypting my laptop's hard drive I've spent upwards of 40 hours trying to retrieve one Open Office document, a 35 page manual that I had been working on, and some Thunderbird emails.

How I screwed up my backup and my primary, i.e. what not to do:
  1) Get only 2 hours of sleep and expect any scripting you do to work.
  2) Make "improvements" to your rsync backup script without thoroughly checking the results. I forgot to set the recursive flag and didn't notice my final copy contained empty directories. Note: a prior copy mostly worked but I had manually deleted it. This is what I ended up recovering in the end.
  3) Decide to repartition and encrypt your drive on a whim only to find out your backup consists of empty folders when you're finished.

During the quest to recover my files I tried the following linux utilities: 
  **testdisk** - looks like it would work great to recover partitions but the changes I made were too great (during some of the encryption steps I performed, large swaths of the hard drive were written over with random bytes making recovery impossible) 
  **photorec** (comes with testdisk) - recovered many files successfully but it didn't know how to recover Open Office documents and I failed to find a way to configure it manually
  **foremost** - scalpel is originally a derivative of this, some find that foremost works better
  **scalpel** - fast and easily configurable, after training it I was able to carve a 250GB ntfs hard drive in ~3 hours, recovering my .odt's and my Thunderbird data.

Windows utilities tried (note: if these would have worked I would have had to pay $50 - $120! ):
  **Arax Disk Doctor** - didn't work in wine, horrible even in Windows XP, couldn't find my files
  **Disk Doctor 2.0** - didn't work in wine, horrible even in Windows XP, couldn't find my files 
  **R-studio** - seemed to be working, scan took ~ 12 hours, while inspecting the results it crashed!, I gave up since I would have had to rescan and it didn't seem to be finding anything useful anyways

In the end I discovered that my laptop's ext4 partitions were too altered to recover the files I wanted and so the external ntfs backup drive became the focus of my forensic efforts. 

Install scalpel:
```
sudo apt-get install scalpel
```Scalpel, and other carvers like it, work by searching every byte on your drive for headers and footers that can identify a contiguous set of bytes as belonging to a specific kind of file. The configuration file found in '/etc/scalpel/scalpel.conf' contains this information and can be edited to search for nearly anything. Scalpel can analyze some example files for you, generating the header/footer information but I opted for the manual approach. 

All I did was open a few different files in vim, decided what was common to all in the beginning and end of the file, and came up with these configuration lines to be added to  'scalpel.conf'. Notice that I've made the sizes of Open Office odt's and Thunderbird files rather large (20MB and 100MB) which suited my case. Make sure you set these to reasonable numbers for your own files or your recovery location will fill and the carving process will crash. This is quite easy to do when carving a large drive which has led a long and varied life.
```

# Added to end of /etc/scalpel/scalpel.conf
#
#---------------------------------------------------------------------
# OPENOFFICE FILES
#---------------------------------------------------------------------
    odt y   20000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.textPK META-INF/manifest.xmlPK????????????????????
    ods y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.spreadsheetPK  META-INF/manifest.xmlPK????????????????????
    odp y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.presentationPK META-INF/manifest.xmlPK????????????????????
#    odg y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.graphicsPK META-INF/manifest.xmlPK????????????????????
#    odc y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.chartPK    META-INF/manifest.xmlPK????????????????????
#    odf y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.formulaPK  META-INF/manifest.xmlPK????????????????????
#    odi y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.imagePK    META-INF/manifest.xmlPK????????????????????
#    odm y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.text-masterPK  META-INF/manifest.xmlPK????????????????????
#    sxw y   10000000    PK????????????????????????????mimetypeapplication/vnd.sun.xml.writerPK  META-INF/manifest.xmlPK????????????????????
#---------------------------------------------------------------------
# THUNDERBIRD FILES
#---------------------------------------------------------------------
#    msf y   10000000    //\s<!--\s<mdb:mork:z\sv="1.4"/>\s-->?<\s<(a=c)>\s//\s(f=iso-8859-1)    //\s<!--\s<mdb:mork:z\sv="1.4"/>\s-->?<\s<(a=c)>\s//\s(f=iso-8859-1)    NEXT
#   actual Local Folder data files, no way to tell end so grab 100MB
    NONE    y   100000000 From????????????????????????????X-Mozilla-Status:\s?????X-Mozilla-Status2:    NEXT

```You may notice extra Open Office lines above. They were borrowed from Chris's Weblog: [http://www.logicalprogressions.net/blog/tag/odt/](http://www.logicalprogressions.net/blog/tag/odt/). Thank you Chris!

Now that the scalpel configuration file is set up to find odt's it's time to carve. First find out what the device name of interest is:
```
sudo fdisk -lh
```In my case I wanted to search /dev/sdb1 which was a usb external hard drive. Now run scalpel adding the '-b' flag so that it will even recover a file if it's missing a footer. This will recover junk but I REALLY wanted my files back, regardless of condition. DO NOT RECOVER THE FILES TO THE SAME PARTITION THAT IS BEING SEARCHED or you risk overwriting files before they are analysed or even falling into a recursive loop. This violates a primary rule of forensics, NEVER MOUNT THE DRIVE TO BE ANALYSED.
```
mkdir ~/Desktop/scalpel_recovered_files/
sudo scalpel /dev/sdb1 -b -o ~/Desktop/scalpel_recovered_files/
```If you're lucky you'll end up with less than a hundred odt's to search through, but this is a pain so lets use the command line instead of the mouse. If I had titled my manual 'FTL Drive Manual' I would find it by:
```
cd ~/Desktop/scalpel_recovered_files/; grep "FTL Drive Manual" *;
```In the case of the Thunderbird Local Folder data files there is no distinct footer to identify its end. For that reason the configuration script was told to just dump whatever 100MB comes after the header. I didn't try using Thunderbird to recover these until I had used vim to manually delete the junk off the tail of the file.

Good luck and please add your own scalpel configuration lines to this post to help the rest of us!

---

### Post by hobo14 on 2010-01-11
Scalpel isn't based on the most recent version of foremost.

I recently used scalpel to recover a heap of jpegs accidentally deleted; I used scalpel first, and some large jpegs were chopped up into several small pieces (small jpeg files in their own right).

I tried foremost after that, and it fared much better; foremost examines the header to determine the location of the footer, scalpel just took the first possible footers it found.

---

### Post by jchedstrom on 2010-01-12
Thank you for the info. I've edited my notes, removing my misleading information. Next time I do some recovery I'll definitely investigate foremost further.

---

### Post by fmurrieta on 2010-09-06
Just to say Thank you! you've saved me a ton of work in a spreadsheet with your post.

Thanks a lot!


Fernando Murrieta

---

### Post by trencanous on 2012-06-06
Thank you so much!!! Extremely useful post.

---

