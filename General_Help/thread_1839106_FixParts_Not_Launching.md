---
title: "FixParts Not Launching?"
date: 2011-09-05
forum: General Help
---

### Post by BanannaButt on 2011-09-05
Hi, I just came from a failed Hackintosh install and want to re-install Windows but Windows won't install as my partition table is in GPT.  So I have looked at [this page]("http://www.rodsbooks.com/fixparts/"), but I still have no idea why Fixparts isn't launching.

Here is my proof:

```
gptfdisk: command not found
root@sean-P-7805u:/home/sean# fixparts
fixparts: command not found

```

I know that gptfdisk is installed because there's a check mark and I installed it through Ubuntu Software Centre.

Please bear with me as I am new to Linux.

Thanks for any help you can provide.

---

### Post by BanannaButt on 2011-09-05
> **BanannaButt said:**
> Hi, I just came from a failed Hackintosh install and want to re-install Windows but Windows won't install as my partition table is in GPT.  So I have looked at [this page]("http://www.rodsbooks.com/fixparts/"), but I still have no idea why Fixparts isn't launching.

Here is my proof:

```
gptfdisk: command not found
root@sean-P-7805u:/home/sean# fixparts
fixparts: command not found

```

I know that gptfdisk is installed because there's a check mark and I installed it through Ubuntu Software Centre.

Please bear with me as I am new to Linux.

Thanks for any help you can provide.

Ok, so I have quickly discovered what you need to do: use the command **gdisk** to get to the program and type in the drive, as specified in the tutorial (for me it was /dev/sda) and then do what you need.

I hope this helps some people!

---

### Post by srs5694 on 2011-09-05
First, if the package you've got installed is earlier than 0.7.0, FixParts isn't included; that program was added with version 0.7.0.

Second, if your disk is GPT, FixParts, won't do you a bit of good, since it terminates when it detects that you're trying to work on a GPT disk.

Is there any data at all you want to preserve on your disk? If not, you should use parted or GParted to create a fresh MBR partition table. These tools will wipe the GPT data structures when you create a fresh MBR partition table, thus enabling you to safely re-use a GPT disk as MBR. If you've got GPT partitions that you want to preserve in MBR form, your best bet is to use gdisk to convert from GPT to MBR form, as described [here.](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by sum1nil on 2011-09-05
If typing 'fixparts' does not launch the program, it may have been installed in an unusual place. Look for it in '/usr/local/bin' if it is there and '/usr/local/bin' is not in your path, then you must type the full path eg. /usr/local/bin/fixparts' or '/this/is/the/path/fixparts'

---

### Post by BanannaButt on 2011-09-05
> **srs5694 said:**
> First, if the package you've got installed is earlier than 0.7.0, FixParts isn't included; that program was added with version 0.7.0.

Second, if your disk is GPT, FixParts, won't do you a bit of good, since it terminates when it detects that you're trying to work on a GPT disk.

Is there any data at all you want to preserve on your disk? If not, you should use parted or GParted to create a fresh MBR partition table. These tools will wipe the GPT data structures when you create a fresh MBR partition table, thus enabling you to safely re-use a GPT disk as MBR. If you've got GPT partitions that you want to preserve in MBR form, your best bet is to use gdisk to convert from GPT to MBR form, as described [here.](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
Thanks for getting back so soon.  It's really cool to get help from the programmer of the program itself :).

The version I have installed is **gdisk 0.6.14.1**.

There is no valuable data on the disk.

And though it can be wiped completely, I experience the following error when trying to create a new MBR table (in MSDOS):

```
Error while creating partition table.
```

Any help would be appreciated.

Thanks.

---

### Post by srs5694 on 2011-09-05
> **BanannaButt said:**
> Thanks for getting back so soon.  It's really cool to get help from the programmer of the program itself :).

The version I have installed is **gdisk 0.6.14.1**.

That version is fine for most GPT manipulation purposes, including wiping all GPT data (via the "z" option on the experts' menu), if that's what you want to do. If you want to convert from GPT to MBR, though, the latest version has improved code for that task. Check [here](http://www.rodsbooks.com/gdisk/download.html#obs) for a matrix of download options for various distributions.

> And though it can be wiped completely, I experience the following error when trying to create a new MBR table (in MSDOS):

```
Error while creating partition table.
```

If that's an error produced by the DOS FDISK program, I'm afraid I can't help; it's been so long since I've used DOS's FDISK that I can't comment on it. The error message itself is so non-specific as to be nearly useless, too. Perhaps you should post the context, such as the exact command that produced the error and information on the size of the disk and what version of DOS you're using. (Old DOS versions might not react well to large modern disks.)  Also, it might help to understand why you're trying to use DOS. Depending on your goals, there might be ways to accomplish it without using DOS, either completely or just when creating your partitions.

---

