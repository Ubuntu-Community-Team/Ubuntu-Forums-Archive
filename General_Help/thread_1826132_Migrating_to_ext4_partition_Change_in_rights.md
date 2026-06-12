---
title: "Migrating to ext4 partition: Change in rights?"
date: 2011-08-16
forum: General Help
---

### Post by T.E.N. on 2011-08-16
To migrate Ubuntu 10.04.3 LTS to a new hard disk, ext4 partitions have been created there, e.g. the new "/" (named root so it will be recognizably mounted as /media/root when double-clicked) as seen in the screenshot below:
[img]http://ubuntuforums.org/attachment.php?attachmentid=200087&d=1313417201[/img]
Also visible are several padlock symbols on the directories ("folders") copied by user "root" (given a passwd) mirroring the old partition's files (i.e. "15 GB file system", where these locks do not appear) from a Desktop Live CD.

Is this effect due to user "ubuntu" taking ownership of the partitions when formatting them (the respective box was ticked by default in Disk Utility), or is there anything deficient about "cp -ax /media/293e12cd-fa3f-44c5-9c1a-f8cb84ba5497/* /media/root" etc. ?

(Incidentally, the system transferred that way won't work properly either, as discussed in [http://ubuntuforums.org/showthread.php?t=1778937#post11154130](http://ubuntuforums.org/showthread.php?t=1778937#post11154130) - not letting anyone (log) in but user "root")

No difference between the source and target directories is seen in ls -l.

Would any specific invocation of rsync or tar (limited to stay within one file system) be the better way?
(Avoiding [Ghost-like](http://ubuntuforums.org/showthread.php?t=1825395) dd or partimage and friends though for the reasons in [http://ubuntuforums.org/showthread.php?t=1682150&page=2#post11154485](http://ubuntuforums.org/showthread.php?t=1682150&page=2#post11154485)...)

---

### Post by raja.genupula on 2011-08-16
hey i got this from one of the thread in forums . try this 

```
If you only use the machine, I mean only one user is there on the machine, I would suggest you to own the partition and give permissions to read and execute to the others, by doing:
Quote:
sudo chown /media/<name of the partition> -R ; sudo chmod 755 /media/<name of the partition> -R
If you have more than one user on your machine and you want to share the partition with everyone permitting each one to do read, write and execute on this partition, you may do:
Quote:
sudo chmod 777 /media/<name of the partition> -R
```

---

### Post by T.E.N. on 2011-08-16
> **raja.genupula said:**
> hey i got this from one of the thread in forums . try this 

> If you have more than one user on your machine and you want to share the partition with everyone permitting each one to do read, write and execute on this partition, you may do:
sudo chmod 777 /media/<name of the partition> -RThanks for your swift reply, which would mean a recursive granting of rights to everything on the partition (and probably all other file systems it has links into) - or to all there is (i.e. next to nothing) before copying while it's still empty.

This might suggest though that contrary to default, the formatting (non-super) user should not take ownership of partitions in the first place.

I'll reboot into the copy and let you know if granting rwx (777) to the root directories of all partitions on it will let me boot it all the way into Gnome. Of course I'd rather preserve all users, groups and their respective rights as they are, i.e. migrate the entire system as-is while changing just the hard disk for a more recent model.

BTW three different meanings of "root" required in one thread already (and a short one at that still) - I realize this is getting complicated. ;)

---

### Post by coffeecat on 2011-08-16
> **T.E.N. said:**
> 
I'll reboot into the copy and let you know if granting rwx (777) to the root directories of all partitions on it will let me boot it all the way into Gnome. Of course I'd rather preserve all users, groups and their respective rights as they are, i.e. migrate the entire system as-is while changing just the hard disk for a more recent model.

I think what you need is to change the ownership of the filesystem itself to root (meaning root account!), but retain all the ownerships and permissions as they are of all the folders and contained files. If you do a recursive chown or chmod on a root (meaning root partition!) partition, you will break the system, so you were right to query a recursive modification.

I think your original problem stems from using Disk Utility and its default of owning a Linux filesystem, which in the live session is "ubuntu" - UID=999. If you use Gparted, the new filesystem will be owned by root (account :)) and everything will be as it should be. Disk Utility's ability to own a filesystem is very useful for external drives, but not appropriate for a new root (!) partition. :)

Do you want any help changing the ownership and permissions of the root (!) of the filesystem without changing any folders and files within it?

---

### Post by T.E.N. on 2011-08-16
> **coffeecat said:**
> I think your original problem stems from using Disk Utility and its default of owning a Linux filesystem, which in the live session is "ubuntu" - UID=999. If you use Gparted, the new filesystem will be owned by root (account :)) and everything will be as it should be. Disk Utility's ability to own a filesystem is very useful for external drives, but not appropriate for a new root (!) partition. :)Many thanks, looks like I was right to question Disk Utility's default the moment I saw it (and wrong only to keep it ticked). That one probably should be changed in general.

Is there anything (additionally) amiss about using "cp -ax /media/oldroot/* media/root", or would that (including the asterisk, or might that still miss a few hidden file names starting with a dot?) be the standard way to completely mirror an entire tree with all access rights preserved?

> Do you want any help changing the ownership and permissions of the root (!) of the filesystem without changing any folders and files within it?

Everything in Unix being a file of some sort, I would assume I (as root, the super-user) could chown&chmod a file system (without the -R) just like everything else, i.e. (as super-user root from a Live CD / rescue disk)> chown root:root /media/root
chmod 755 /media/root
Should this be done on the mounted one(s) such as /media/root, or would it even work on the device (which would surprise me a bit since I'd consider access rights part of the directory/file system structures) ?
Should all partition roots (i.e. their top-level directories) "belong" to root (the super-user) and have drwxr-xr-x (except drwx------ for lost+found) ?

---

### Post by coffeecat on 2011-08-16
> **T.E.N. said:**
> Many thanks, looks like I was right to question Disk Utility's default the moment I saw it (and wrong only to keep it ticked). That one probably should be changed in general.

Is there anything (additionally) amiss about using "cp -ax /media/oldroot/* media/root", or would that (including the asterisk, or might that still miss a few hidden file names starting with a dot?) be the standard way to completely mirror an entire tree with all access rights preserved?

That's very close to what I do. I use:

```
sudo cp -av /media/source/* /media/target/
```

You don't need the -x option because your oldroot (what I call source) won't have anything mounted inside it. I believe hidden (leading dot) files within the root of the filesystem are not copied - you probably don't have any anyway - but hidden files within folders will be copied. Of course, what you mustn't do is:

```
sudo cp -av /* /media/newroot
```

...from "inside" your system. Even with the -x option, something will go wrong. The -a option preserves everything you need to preserve, and the -v option is useful to re-assure you the whole thing hasn't frozen on you!

[> **T.E.N. said:**
> 
```
chown root:root /media/root
chmod 755 /media/root 
```
Should this be done on the mounted one(s) such as /media/root, or would it even work on the device (which would surprise me a bit since I'd consider access rights part of the directory/file system structures) ?
Should all partition roots (i.e. their top-level directories) "belong" to root (the super-user) and have drwxr-xr-x (except drwx------ for lost+found) ?

OK, one important, and little-understood, detail. You need to mount the filesystem you want to chown and/or chmod and then chown and chmod the mountpoint. What happens is that the root of the filesystem gets modified, not the mountpoint. So your code is correct. If you do a "ls-l" on the mountpoint before mounting, after mounting, after chmodding and then after unmounting, you'll see what I mean. The top-level directories including lost+found are not affected because they are not top-level directories. In a very real sense the root of the filesystem *is* the top-level directory and this is what is being chmodded and chowned.

Assuming the filesystem you want to change is mounted on /media/mountpoint, then:

```
sudo chown root:root /media/mountpoint
sudo chmod 755 /media/mountpoint
```

Which is what you said anyway! :)

It's probably best to do this before you copy all your files across, but it *should* be OK if they are there already because you are not using the recursive option.

---

### Post by T.E.N. on 2011-08-16
> **coffeecat said:**
> That's very close to what I do. I use:

```
sudo cp -av /media/source/* /media/target/
```

You don't need the -x option because your oldroot (what I call source) won't have anything mounted inside it.Well, the root partition / for one thing is expected to have links that might go to other partitions, such as:
lrwxrwxrwx   1 root root    30 2011-08-14 16:57 vmlinuz -> boot/vmlinuz-2.6.32-33-generic
...hence the -x just to be sure it won't try to follow any of these.
Of course, unlike on the system booted up and running from the "source" hard drive, nothing should be mounted to that partition's boot subdirectory while working from a Live CD / rescue disk, hence all cp ought to see would be inside one file system anyway (but then again a link with a leading slash might be set to something that does exist on the Live CD system, and copy loads of unwanted stuff from there?).

> I believe hidden (leading dot) files within the root of the filesystem are not copied - you probably don't have any anywayIndeed I haven't seen any in ls -artl on the root directories of my partitions, but not knowing for sure what the default globbing behavior for * is supposed to be, felt I ought to ask.

> the root of the filesystem gets modified, not the mountpoint. So your code is correct. [...] In a very real sense the root of the filesystem *is* the top-level directory and this is what is being chmodded and chowned.Many thanks again for your explanations!

---

### Post by coffeecat on 2011-08-16
Good luck with that!

---

### Post by T.E.N. on 2011-08-17
> **coffeecat said:**
> Good luck with that!All went well. :)
Now while I'm at it, since cp has no verify option, is there a "surefire" way to compare the copies of entire trees for both completeness (all files and attributes/rights) and integrity (as in cmp: all bits ;)) ?

diff -qr from [http://ubuntuforums.org/showthread.php?t=474035#post4570991](http://ubuntuforums.org/showthread.php?t=474035#post4570991) might be a candidate, md5deep from [http://ubuntuforums.org/showthread.php?t=474035#post2847794](http://ubuntuforums.org/showthread.php?t=474035#post2847794) probably less so for being rather computationally expensive (and not readily available by default in rescue systems).
However, as described at the above URL, diff will complain e.g. on every symlink pointing to files unreachable with the partitions mounted elsewhere from the Live CD, even though properly copied.

---

### Post by coffeecat on 2011-08-17
I'm glad it all worked. I don't know of a verification method in these circumstances. I've simply trusted that the cp command will do what I tell it to do (that's the trouble with terminal commands - they do what you tell them to do, not what you want them to do! :p) and that the hardware is OK.

As you've now discovered, cp is a good quick-'n'-dirty way to "clone" systems. I've often used it when swapping hard drives around and so long as I changed the UUID in the new partition to what it was in the old one - or edited /etc/fstab and did something with grub - it's never failed me.

The other way which also gives you an archive as a backup is to use good old tar. Simply "sudo tar -czvf filename.tgz /media/whatever/*" to create the archive. As with cp, this needs to be from "outside" the system you're copying. Then "sudo tar -xzvf filename.tgz /media/new-whatever/". You don't have to --exclude all the folders such as /dev and /proc with virtual files as I've often seen posted. And tar has a...

[quote="man tar"]
-d, --diff, --compare
           find differences between archive and file system
[/quote]

Although I've never used it.

---

### Post by T.E.N. on 2011-08-17
> **coffeecat said:**
> so long as I changed the UUID in the new partition to what it was in the old one - or edited /etc/fstab and did something with grub - it's never failed me.Migrating UUIDs as in reading them with blkid /dev/sdb5 and then setting them by tune2fs /dev/sdc5 -U "49149403-34b5-4058-a80a-aa09baf689a9" etc. (which could probably be made into a one-liner with some RegEx on the blkid output) ?

Are UUIDs (regrettably also changed each time a partition is reformatted) completely random and independent of the underlying hard drive, i.e. doesn't that change risk any side effects?
I've always found patching /etc/fstab and re-installing grub (due to the new UUIDs) from a Live CD chroot environment on the new hard disk to be a rather cumbersome process, but thought this was recommended all over the place because UUIDs might cause some trouble if they ever did show up twice on different devices.

> the trouble with terminal commands - they do what you tell them to do, not what you want them to do!Which is a good thing compared to what I experienced with Disk Utility and GParted (also wiping labels on format BTW, though it would have a field to set/keep them), so for some command line magic that might be useful to the next reader facing these same questions, here's what actually happens behind the scenes on the latter (and could easily be one step if the empty quotes following -L were used on the first line):
> mkfs.ext4 -j -O extent -L "" /dev/sdc9
e2label /dev/sdc9 "var"BTW tune2fs -l will list both the "Filesystem volume name:   " and the "Filesystem UUID:          " in case anyone wants to construct a one-liner to migrate entire partitions with both of them to a new hard disk.

---

### Post by coffeecat on 2011-08-17
> **T.E.N. said:**
> Migrating UUIDs as in reading them with blkid /dev/sdb5 and then setting them by tune2fs /dev/sdc5 -U "49149403-34b5-4058-a80a-aa09baf689a9" etc. (which could probably be made into a one-liner with some RegEx on the blkid output) ?

Yes, that's what I do, but being careful as you point out that having two identical UUIDs is not going to cause problems in the setup I am in.

> **T.E.N. said:**
> Are UUIDs (regrettably also changed each time a partition is reformatted) completely random and independent of the underlying hard drive, i.e. doesn't that change risk any side effects?

I've never experienced a problem after changing a UUID with tune2fs, and there's nothing that I know of in the documentation that would say this is wrong. That's not to say there's a potential issue that I'm not aware of!

> **T.E.N. said:**
> 
Which is a good thing compared to what I experienced with Disk Utility and GParted (also wiping labels on format BTW, though it would have a field to set/keep them)

Yes, I find that irritating in Gparted. If I create a new partition with a filesystem, I can specify a label all in one go. But if I reformat an existing partition, I have to go back a second time to relabel it. I'm sure the Gparted devs could fine-tune the user interface to cope with this if they knew that it was a problem. Perhaps I'll look on the upstream Gparted website to see if this has been suggested, or if there is any mechanism to suggest design enhancements.

---

### Post by T.E.N. on 2011-08-17
> **coffeecat said:**
> that's what I do, but being careful as you point out that having two identical UUIDs is not going to cause problems in the setup I am in.

I've never experienced a problem after changing a UUID with tune2fs, and there's nothing that I know of in the documentation that would say this is wrong. That's not to say there's a potential issue that I'm not aware of!

Many thanks again for your help and these opportunities to benefit from your experience! :) I recalled duplicate not-so-Universally-Unique-IDs were sometimes causing unhandled errors in RAIDs, as well as back when they were introduced to Ubuntu, cf. [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/64909](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/64909) and one thread around here that for some reason I only get display from cache at this time: [http://webcache.googleusercontent.com/search?q=cache:LFg21WJ-vEcJ:ubuntuforums.org/archive/index.php/t-492813.html](http://webcache.googleusercontent.com/search?q=cache:LFg21WJ-vEcJ:ubuntuforums.org/archive/index.php/t-492813.html)

At any rate, the original (source) hard disk is going to be removed from the system (and possibly reformatted somehow if still deemed a SMART move ;)), so the UUIDs won't be duplicate locally at least.

I'm sure I won't be the only one to very much prefer a few invocations of tune2fs -U (especially as they can be nicely crafted from e.g. "ls -l /dev/disk/by-uuid > /media/USB\ DISK/dev_disk_by-uuid.2011-08-17") to the grub re-install hassle, and will simply reboot into the Live CD one more time (possibly unnecessary precaution) without the original HDD to make sure nothing ever encounters duplicate UUIDs on that machine.
Or do I have to re-install GRUB anyway for it still needs to be made aware of a possibly different drive geometry even though using UUIDs?

Having this thread should also be quite useful over time if it helps a few people avoid migrating partitions in the considerably more time-consuming and error-prone way by dd with subsequent resizing and/or file system conversion.

---

### Post by coffeecat on 2011-08-17
> **T.E.N. said:**
> Having this thread should also be quite useful over time if it helps a few people avoid migrating partitions in the considerably more time-consuming and error-prone way by dd with subsequent resizing and/or file system conversion.

You are considerably more optimistic than I. :p Until your thread appeared I was beginning to think I was a lone voice crying in the wilderness. I've lost count of the times I've suggested using cp or tar to migrate an installation or partition only to be studiously and comprehensively ignored. I now let people get on with their clonezillas and dd's and only respond when I find someone like you who has seen the light!

Good luck! :)

---

### Post by T.E.N. on 2011-08-17
> **coffeecat said:**
> Until your thread appeared I was beginning to think I was a lone voice crying in the wilderness. I've lost count of the times I've suggested using cp or tar to migrate an installation or partition only to be studiously and comprehensively ignored. I now let people get on with their clonezillas and ddThanks all the more! There's one further piece of advice that might complement this thread:
tune2fs -U won't work (expectedly) on the swap partition, but which other utility will?
Not sure "man mkswap" is trying to tell me it will (just) **set** the swap's UUID when invoked with
> -U uuid
              Specify the uuid to use. The default is to generate UUIDs.

I've resorted to simply mounting the new root partition and editing the UUID given to the swap space (on formatting) into /etc/fstab (figuring GRUB couldn't care less about that one), and successfully rebooted from the new HDD since - but it's not a 100% compatible clone without that yet. :)

BTW one application found incompatible with changing UUIDs on-the-fly from the Live CD was GParted which reproducibly crashes afterwards (until reboot).

---

### Post by coffeecat on 2011-08-17
> **T.E.N. said:**
> tune2fs -U won't work (expectedly) on the swap partition, but which other utility will?
Not sure "man mkswap" is trying to tell me it will (just) **set** the swap's UUID when invoked with

I find mkswap to be just fine for changing the UUID of a swap partition:

```
sudo mkswap -U blah-blah-blah /dev/sdXY
```

I suppose mkswap is making a new swap space but that doesn't really matter since swap isn't a proper filesystem anyway, and it doesn't matter if it "reformats" the partition. You're not going to be wanting to read anything on it anyway.

A little-known feature of the live installer (probably the alternate installer as well, I guess.): :) If you choose the advanced option ("something else" in Natty), the installer picks up the presence of a pre-existing swap partitition and tells you it's going to reformat it. Whatever it does, you end up with a sap partition with the same UUID as before. I've never looked under the hood (wouldn't know where to look anyway) but I wouln't be surprised if Ubiquity is running "mkswap -U" at this point.

> **T.E.N. said:**
> BTW one application found incompatible with changing UUIDs on-the-fly from the Live CD was GParted which reproducibly crashes afterwards (until reboot).

Thanks for the warning! :)

---

### Post by T.E.N. on 2011-08-17
> **coffeecat said:**
> I suppose mkswap is making a new swap space but that doesn't really matter since swap isn't a proper filesystem anyway, and it doesn't matter if it "reformats" the partition.After a "swapoff /dev/sdb10" from the Live CD (since without even asking -like most- it will use any it finds; risky as that is for rescue operations in case of a hard disk "on its way out"), "fs2tune -U 1b...61 /dev/sdb10" and commenting the line for that "old" UUID back into /media/root/etc/fstab did the trick in a matter of milliseconds, i.e. this invocation of fs2tune, ambiguously documented as it is in its man page, would change the UUID without having to spend much time on re-initializing the swap space prior to a final sync & reboot.

---

