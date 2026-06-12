---
title: "Determining mount points for variables in script"
date: 2009-08-01
forum: General Help
---

### Post by jm8254og on 2009-08-01
Hello,



I have a very simple script that I wrote that takes user input "Source Drive" and "Destination Drive" and stores them as variables for use in the dd command.

I want to automated this so instead of asking the user the source and destination I want to figure it out for them in the script.

Is the only way to do this with conditionals such as check if mount point /dev/sda1/ exist then based on that use /sda or whatever as source or is there a way to directly extract this information?

I though maybe I could read the output of the fdisk -l command and extract the mounts as strings but it seems there must be a better way than any of my ideas.  The script I am using now I wrote in perl but I don't have to use perl.

---

### Post by kidders on 2009-08-02
Hi there,

There's not a lot of detail in your post about what you're trying to achieve. For instance, you might be trying to automate some sort of backup procedure, where something like /dev/sdc might be the source, and wherever /dev/sdh1 happens to be mounted (let's suppose it's an external hard disk) might be the destination. Then again, you might be up to something totally different.

What sorts of constraints would you want to place on the source & destination devices? For instance, if you were writing a script to copy DVDs onto your hard disk, the source would have to be an optical drive. I suppose what I'm asking is how your script should determine what disks to use as the source & destination. To avoid asking the user questions, it might need to be reasonably clever ... depending on what you're trying to do.

---

### Post by jm8254og on 2009-08-03
Sorry for not explaining it well.

I am automating hard drive image acquisition for e discovery.  The local internal disk will be the source and the external will be the destination.  I just want to build in some fail safes in case.  I can't afford to write from the external to the internal drive and overwrite the end user's hard drive.  The disk will be used by the end user so the determination of source and destination needs to be automated.

---

### Post by jm8254og on 2009-08-03
Well I do have an idea:  The source drive will always be NTFS and the destination will always be FAT32.  If I use the df -t command I can determine the drive.  I just have to figure out how to pipe the output of a command to a string, then truncate it.

---

### Post by kidders on 2009-08-04
There are a few ways of distinguishing between internal and external devices. For example ...```
#!/bin/bash
declare -a EXTERNAL_DISKS
declare -a INTERNAL_DISKS

for disk in /dev/[sh]d[a-z]; do
	eval `udevinfo -q env -n $disk`
	[ "$ID_BUS" = "usb" ] && EXTERNAL_DISKS=( ${EXTERNAL_DISKS[@]} $disk )
	[ "$ID_BUS" = "scsi" ] && INTERNAL_DISKS=( ${INTERNAL_DISKS[@]} $disk )
done

echo "Internal disks: ${INTERNAL_DISKS[@]}"
echo "External disks: ${EXTERNAL_DISKS[@]}"
```Just for the sake of demonstration, that would go through all your disks and classify them as internal/external based on the I/O bus they're connected to.

There would be a few edge cases you probably wouldn't be able to handle sensibly without user intervention:[LIST]
[*]${#EXTERNAL_DISKS[ *]} or ${#INTERNAL_DISKS[ *]} is zero - No internal hard disk, external device not connected, etc.
[*]${#EXTERNAL_DISKS[ *]} is greater than 1 - You could use model information from udevinfo to ask the user which device to use. That might be better than asking someone "Do you want to back up onto /dev/sdd or /dev/sde?", which might be hard for some users to answer.
[*]${#INTERNAL_DISKS[ *]} is greater than 1 - One obvious option in this case would be to back them all up, but you may not want that.
[/LIST]

Incidentally, won't using FAT32 backup destinations limit the size of the hard disks you copy?

One drawback to using df to identify filesystem types is that the filesystems have to be valid (ie can't contain errors) and mounted when your script runs. Since most users of your script will most likely instinctively unmount the backup source before running it (to avoid corrupting the backup), that technique is unlikely to work well. In any case, /etc/mtab might be a better source for the same information, since it's easier to parse, and more predictably formatted. For example, to discover the filesystem type of /dev/sda1, you could try ...```
$ grep ^/dev/sda3 /etc/mtab | cut -d" " -f3
jfs
```As I said, I'm not sure I'd do it this way, but I wanted to try to answer your question about mangling the output of commands. Other useful utilities include sed  (easy to use) and awk (hard to use).

Another option for determining filesystem type would be to access the block device directly, and ask it...```
# dd bs=1024 if=/dev/sdc2 count=4 |file -
4+0 records in
4+0 records out
4096 bytes (4.1 kB) copied, 4.4978e-05 s, 91.1 MB/s
/dev/stdin: Linux rev 1.0 ext3 filesystem data (needs journal recovery) (large files)
```That command reads the first 4k off /dev/sdc2 and uses "file" to identify the raw data.

Anyhow, I hope there's *something* helpful in there.

---

### Post by jm8254og on 2009-08-05
I am going to work with what you gave me all day, thank you!  I had almost given up on my question.

As far as the FAT 32 goes, I use the split option in dd and split at 4 gig .img files.  It improves write time greatly.

Yeah, df will not work on a live cd well and to agree with your point, what happens if they delete a partition?  So I agree with you first method I just didn't know where to start.

---

### Post by jm8254og on 2009-08-05
Well, I am having trouble with you first suggestion.  I am not very familiar with bash yet.  

I get "declare not found" 
and
Syntax error: "(" unexpected (expecting "done")

I will play around with it I just wondered if you knew why.

---

### Post by kidders on 2009-08-05
> **jm8254og said:**
> I am not very familiar with bash yet.That's no problem ... the important bit is **udevinfo -q env -n $disk** anyhow, where $disk is something like /dev/sdb. It'll tell you how the device is connected to the PC, and who made it (so you can use reasonably friendly device descriptions, in the event you need to resort to user interaction).

The stuff you're having problems with is Bash's array support, which is not important, since you're using Perl. Unfortunately, I'm not that hot with Perl :-(

---

### Post by jm8254og on 2009-08-05
I think I figured it out using perl, thanks.  I will post the final code incase someone else ever needs its and comes across this thread.  Thanks again.

Here is what I came up with 

@array = (a..z);
$i=0;

until ($diskID1 eq "ID_BUS=scsi")
{
$src = "sd".$array[$i];
chomp ($diskID1 = `udevadm info -q env -n /dev/$src | grep ID_BUS=scsi`);
$i=$i+1;
}
print "$src\n";

udev info is the command for distros older than 8.10.  Thanks for your help.  Just replace "scsi" with "usb" if needed.

---

