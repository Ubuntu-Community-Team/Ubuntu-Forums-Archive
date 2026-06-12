---
title: "searching for files on an external hard drive"
date: 2012-05-04
forum: General Help
---

### Post by Mickser_52 on 2012-05-04
Hi,

I want to search through hard drives from old laptops for jpg files. I can connect the hard drives through a usb port and look through each folder for the files but it can be a tedious process.

Is there some way I can just find the folders containing the jpg files to speed up the process.

---

### Post by prshah on 2012-05-04
> **Mickser_52 said:**
> Is there some way I can just find the folders containing the jpg files to speed up the process.

```
find Pictures/ -iname "*.jpg" -exec dirname "{}" \; |sort -u
```

Try the above command in a terminal "Dash Home"-"Terminal". This will list ONLY directory names where jpg files are found, and then sort them to remove duplicates.

This will list the output on the screen; you can redirect it to a file if you like.

Replace "Pictures/" with the target location, eg "/media/laptophdd"

Please post back if you need more information.

 NOTE: May take a long time to run.

---

### Post by Mickser_52 on 2012-05-04
many thanks, that worked perfectly. I have been storing my photos on an external hard drive and then deleting the originals from my laptop over 6 years. Now the hard drive beeps a few times but won't open.

I am trying to locate copies of some of them from old family's laptops.
 
My knowledge of terminal commands is minimal so this has been very helpful. I had been trying the find command without success. 

Could you please explain the other parts e.g the -exec dirname "{}" \; and how I might copy these files to a new (hopefully more reliable) external hard drive

thanks again

---

### Post by prshah on 2012-05-04
> **Mickser_52 said:**
> Could you please explain the other parts e.g the -exec dirname "{}" \; and how I might copy these files to a new (hopefully more reliable) external hard drive

```
find Pictures/ -iname "*.jpg" -exec dirname "{}" \; |sort -u
```

find = find command, get more information with the terminal command "man find" (no quotes)

Pictures/ = folder to search (replace as suitable)

-iname = search file"name" "i"nsensitive to case (UPPER,lower,Mixed)

"*.jpg" = what to search

-exec = execute the following command for each file found

dirname "{}" = get directory name for file found ("{}" indicates file currently found by find)

\; = terminator; indicates that exec command ends here

|sort -u = send results to the "sort" command, which then only outputs unique results (-u).

To copy "found" files, you can probably try something like this; this is not bulletproof, it's just a off-the-top-of-my-head suggestion:

```
find ~/Pictures/ -iname "*.jpg" -exec cp --parents -v -t /backup/laptop1/ "{}" \;
```

The breakup for this (only changed parts explained):

cp = copy command
--parents = when copying source file to destination, include and create full path of source file in destination (explained further below)
-v = verbose (show what's being done)
-t = target directory; location to copy file to; make sure this path exists and is writeable

you need the "--parents" to prevent files with same names (but in different directories) from being overwritten. Eg if you have DSC00345.jpg in /Pictures/Holidays and the same filename DSC00345.jpg in /Pictures/Parties, one will overwrite the other if all files are copied to the same target directory. "--parents" will help prevent this by creating the directories "Holidays" and "Parties" under the target location, and copying each file to it's relevant location under the target location. (Sorry, can't explain it any clearer; just re-read it a couple of times, it will get clearer).

as for your target directories, I suggest you create a seperate backup path for each laptop (eg /backup/laptop1, /backup/laptop2, etc), again to prevent overwriting in case of same file names.

I hope this is clear; please post back if you need further explanations.

---

### Post by Mickser_52 on 2012-05-04
Again many thanks, your explanation is perfectly clear and will be very useful for this task and for my further studies of ubuntu terminal.

If your career is not in education at the moment you could consider it at some time in the future.

---

### Post by prshah on 2012-05-05
> **Mickser_52 said:**
> Now the hard drive beeps a few times but won't open.

Chuffed to know the tips were useful.

On a side note; are you sure your external drive is dead? 

External drives are usually only a casing and relevant circuits around a bog-standard internal drive; usually 3.5" SATA, or on older drives IDE.

Sometimes, only the casing and circuits are faulty; the internal drive may still be working fine.

If you don't much care about the non-working external drive anymore, you can consider opening it up, removing the internal drive and testing it in a system. Without knowing your tech level, it is difficult to be more specific, but post back with details about the drive (brand, make, model) if you would like to try this.

---

### Post by Mickser_52 on 2012-05-05
This is as much information as I can find about the external hard drive: Western Digital Caviar SE WD3200JB 320GB 7200 RPM 8MB Cache IDE Ultra ATA100 / ATA-6 3.5" Hard Drive -Bare Drive.

I have previously removed the drive from its casing and connected it, with a connection I have, to a usb port. When I power up the drive there is a series of three tones (almost musical) this is repeated about 4 times and then nothing happens. If I try Ubuntu Disk utility the drive does not show.

That is the extent of my capabilities to date. There are advertised companies which may be able to retrieve data from the drive but their prices are more than I am prepared to pay even for some pictures of sentimental value.:)

Any suggestions you might be able to make based on this information would be gratefully received.

Many thanks.

---

### Post by prshah on 2012-05-05
> **Mickser_52 said:**
> When I power up the drive there is a series of three tones (almost musical) this is repeated about 4 times and then nothing happens.

Dead and done. Toast. Bought the farm. Pushing up the daisies. Defunct.

Yes, it's dead. The "tones" ("clicking") usually indicate hardware damage.

I have read of people who have succeeded in briefly reviving the drive (long enough to copy stuff off) by showing it into a freezer for "n" days, and then hooking it up. It's never worked for me, but thought I'd just mention it to you. I wouldn't keep much hope for the drive.

---

### Post by Mickser_52 on 2012-05-05
This is what I thought was the case. I will try the cryogenic approach as a final straw.

Thanks for all you help.

---

