---
title: "Is cp /dev/zero bigfile safe?"
date: 2010-12-25
forum: General Help
---

### Post by horseatingweeds on 2010-12-25
I'm installing Ubuntu over an XP installation for someone, who plans to give this system to someone else. So, the first person would like all their data to be actually deleted. 

I figured, after installing Ubuntu, I would fill the rest of the drive with a big zero filled file, then delete it:

cp /dev/zero bigfile
rm bigfile

Will this cause any problems with the system running if I have Ubuntu in one partition? I'm just a little worried I'll make this huge file then not be able to delete it.

---

### Post by noah++ on 2010-12-25
To take the guesswork out of this:

For really, really secure deletion, use a specialized tool like [Eraser]("http://eraser.heidi.ie/").

For deletion about as secure as the method you proposed, you should let Ubuntu format the disk *without *using quick formatting. I think quick is the installer's default.

---

### Post by Irony on 2010-12-25
```
sudo shred -vfz -n 1 /dev/sdc
```

The command above does 1 pass of randomisation and then one pass of zeros, replace sdc with whatever your device actually is. Google shred for alternative commands.

---

### Post by horseatingweeds on 2010-12-25
The files are already 'deleted', and Ubuntu is already installed, allowing it to format the whole disc automatically. So, unless I'm confused, I don't want to use **shred** on anything. 

Is using this command ok?

cp /dev/zero bigfile
rm bigfile

---

### Post by diagram30 on 2010-12-25
/dev/zero is an entity, it is not a file by itself, therefore copying it would do nothing related to your purpose.

albeit it's rather foolish to do as you wish, considering dd works much better, I believe the correct command is "cat /dev/zero > bigfile && rm bigfile".

---

### Post by horseatingweeds on 2010-12-25
> **diagram30 said:**
> /dev/zero is an entity, it is not a file by itself, therefore copying it would do nothing related to your purpose.

albeit it's rather foolish to do as you wish, considering dd works much better, I believe the correct command is "cat /dev/zero > bigfile && rm bigfile".

That's what I'm trying to determine, diagram30. I want to overwrite anything that may be on the disk, in space that is currently 'empty'. How do you suggest using dd to do that?

---

### Post by dcstar on 2010-12-25
> **noah++ said:**
> To take the guesswork out of this:

For really, really secure deletion, use a specialized tool like [Eraser]("http://eraser.heidi.ie/").
.........

Yes, we really must pander to the unproven paranoia over this issue, don't we?

Notice how these places now claim: "The file remains on the disk until another file is created over it, and even after that, it **might** be possible to recover data by studying the magnetic fields on the disk platter surface"

The "might" is there because there has been no cases I know of reported of anyone actually been able to "recover data", and the ambiguous scare tactics previously used to convince people to use these basically pointless methods can run foul of the truth in advertising laws.

One pass of any pattern is more than enough to "wipe" a drive, if you want more then use the built in ATAPI "Secure Erase" function that is in all modern hard drives.

---

### Post by Habeouscorpus on 2010-12-25
Ditto to Dcstar. If the person you're giving it to has access to a forensic crime lab and a lot of motivation to get the stuff back, then worry about extreme obliteration. Just do a quick format; delete and recreate the partition. Easy peasy.

---

### Post by horseatingweeds on 2010-12-25
That's what I did: quick reformat. I had also deleted the sensitive data and probably ran back over whatever loose space there was a couple time screwing around trying the get the XP partition to reinstall, I really kind of abused that HDD. (Failed, went with full Linux)

I just wanted to try out an obliteration technique to be thorough and to have used it once, but wasn't sure if filling the partition with the above command would break the system. It's too late now - the system just went out the door - but I'm still interested to know.

---

### Post by Andrew.Z on 2010-12-26
> **horseatingweeds said:**
> 
cp /dev/zero bigfile
rm bigfile

You are thinking of

dd if=/dev/zero of=/tmp/bigfile bs=1M count=100000 && rm /tmp/bigfile

You would need to do this for each partition (maybe / and /home, for example) and maybe the swap partition too.  However, this wouldn't wipe the inodes.  You can use [BleachBit to wipe](http://bleachbit.sourceforge.net) all these for you:

bleachbit --delete system.memory system.free_disk_space

(after you define your target partitions via the GUI)

As mentioned, [one overwrite pass is enough](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk)---if you do it right.

> **horseatingweeds said:**
> That's what I did: quick reformat.

Quick format is not adequate to erase previously deleted files. It erases the metadata (filenames, etc) but not the data.

---

