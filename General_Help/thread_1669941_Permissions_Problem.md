---
title: "Permissions Problem"
date: 2011-01-18
forum: General Help
---

### Post by natpat on 2011-01-18
Hey,

I recently had to restore my /home folder from a backup. I used SimpleBackup, and everything worked fine - except now everything in the home folder is now owned by root.
(just in case it means anything, my /home folder is actually another partition mounted)

I am the only user on this computer and don't know if that's normal, but PulseAudio and Wine don't seem to be working. Everything else is fine, and as the permissions is the only thing that's changed, I'm assuming it's something to do with that.

The error I get with pulseaudio is this:
E: core-util.c: Home directory /home/nathan not ours.
W: lock-autospawn.c: Cannot access autospawn lock.
E: main.c: Failed to acquire autospawn lock

I've searched around a bit and eventually came to this page: [http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727) I've followed the steps but it didn't work - after I restarted, it had the same problem.

Any help?

---

### Post by coffeecat on 2011-01-18
> **natpat said:**
> except now everything in the home folder is now owned by root.

Everything? :-s

To fix that you need to:

```
sudo chown -R nathan: /home/nathan
```Which will do a recursive change of ownership throughout the whole of your home directory tree. Make sure you include the trailing colon after your account name in that command - that ensures that everything is owned by your default group.

You may still have some permissions problems with the home folder and the .dmrc file (as distinct from ownership) for which you need the chmod command. The link you posted should sort that out for you.

---

### Post by natpat on 2011-01-18
Yup, everything... well, the only thing on there at the moment is my nathan folder, so yup, everything.

And ah! That colon might work... I'll try that now. :)

---

### Post by coffeecat on 2011-01-18
> **natpat said:**
> Yup, everything... well, the only thing on there at the moment is my nathan folder, so yup, everything.

If your nathan folder is empty, then you haven't done a restore from a backup. Or if you deleted all the default folders, don't forget that there are a whole load of hidden configuration folders and files which need to be owned by you and not root.

This might be a permissions problem with a mounted separate home partition, but hopefully that command will work anyway. Post back if it doesn't.

---

### Post by natpat on 2011-01-18
Ah, no, all my files are in the folder (even the hidden ones).

And unfortunately, that command didn't work either :/ everything is still owned by root.

I've included an attachment showing what I mean by it being owned by root... all of the folders and files look like that.

---

### Post by coffeecat on 2011-01-18
I'm glad you posted a screenshot, because we could have spent ages tracking this down otherwise. The 'System Volume Information' folder reveals the problem. That is a Microsoft filesystem - probably NTFS. MS filesystems do not support Linux permissions which means:

1 - The commands chown and chmod will not work on files in a MS filesystem.

2 - You cannot have your home folder on a MS filesystem, although you can store personal files on a FAT32 or NTFS partition. 

You can change the "ownership" of folders and files on a NTFS filesystem with mount options, but you will still have the central problem of not being able to have your home partition formatted NTFS. Perhaps if you describe more of your setup we can take it from there.

---

### Post by WorMzy on 2011-01-18
I have a sneaking suspicion that you are using an NTFS partition as your home partition. NTFS partitions do not support Linux file permissions, hence the chown command not having the desired effect.

Please use a Linux filesystem (e.g. ext4) for /home.

However, you can use an NTFS partition for storing data between Windows and Linux, if that is your desire. You can even link the NTFS partition's folders to your home folders using symlinks or "mount --bind"s, so that ~/Documents leads to the NTFS partition's Documents folder.

It's a technique that I employ which allows me to access my documents and whatnot no matter which one of my nine (currently) operating systems I boot into.

Just say if you want to set this up, and I'll write up a tutorial on how to do that for you. If you'd prefer to keep using a NTFS partition as your home partition, then you're on your own. :P

---

### Post by natpat on 2011-01-18
Oh, I see. Yes, it is a NTFS partition - I wanted these documents to be able to be accessed by both my Vista and Ubuntu.

I have a dual boot Vista and Ubuntu, and the hard drive has 6 partitions:

1) Vista Recovery
2) Vista Data/Boot
3) Linux Boot
4) An extended partition, including:
   5) A swap partition
   6) The NTFS data partition that /home is mounted as.

There isn't much on that last partition, so I'd be willing to say, split it in half and have one half as an ext4 partition (for my home folder) and another as an NTFS for sharing between Ubuntu and Vista.

Would that setup work? Or can you suggest a better solution?

Edit: Looking WorMzy's post, I can see he's suggested pretty much that.

...could I request that tutorial? :)

---

### Post by WorMzy on 2011-01-18
No problem, however it may take several minutes to get it posted, depending on the forum's willingness to work. :)

Stay tuned..

---

### Post by natpat on 2011-01-18
> **WorMzy said:**
> No problem, however it may take several minutes to get it posted, depending on the forum's willingness to work. :)

Stay tuned..

Ah, thank you very much. I shall be waiting :P

---

### Post by coffeecat on 2011-01-18
> **natpat said:**
> I have a dual boot Vista and Ubuntu, and the hard drive has 6 partitions:

1) Vista Recovery
2) Vista Data/Boot
3) Linux Boot
4) An extended partition, including:
   5) A swap partition
   6) The NTFS data partition that /home is mounted as.

There isn't much on that last partition, so I'd be willing to say, split it in half and have one half as an ext4 partition (for my home folder) and another as an NTFS for sharing between Ubuntu and Vista.

Would that setup work? Or can you suggest a better solution?

Yes. You're already setup for the easiest solution. Don't split the data partition. Simply have your /home as normal on the root partition and organise your personal files into Music, Video, Whatever folders on the NTFS partition. Now simply set up symlinks in your home folder to each of the Music, etc folders in the data partition. Done. You can even set up shortcuts in Vista for the same effect.

WorMzy may have an even simpler way. :)

---

### Post by coffeecat on 2011-01-18
> **natpat said:**
> I have a dual boot Vista and Ubuntu, and the hard drive has 6 partitions:

1) Vista Recovery
2) Vista Data/Boot
3) Linux Boot
4) An extended partition, including:
   5) A swap partition
   6) The NTFS data partition that /home is mounted as.

There isn't much on that last partition, so I'd be willing to say, split  it in half and have one half as an ext4 partition (for my home folder)  and another as an NTFS for sharing between Ubuntu and Vista.

Would that setup work? Or can you suggest a better solution?

Yes. You're already setup for the easiest solution. Don't split the data  partition. Simply have your /home as normal on the root partition and  organise your personal files into Music, Video, Whatever folders on the  NTFS partition. Now simply set up symlinks in your home folder to each  of the Music, etc folders in the data partition. Done. You can even set up shortcuts in Vista for the same effect.

WorMzy may have an even simpler way. :)

---

### Post by WorMzy on 2011-01-18
The /home partition and storage partition don't need to be of a similar size. Since all the bulky items (e.g. Documents, Pictures, Music, Videos, etc) will be on the storage partition, the /home partition will mostly contain .config files, firefox cache/bookmarks, etc, so it's fine to allocate just a few GB of space to the /home partition, or even merge it with your actual Ubuntu partition.

Out of the two techniques I mentioned, I personally use binds, rather than symlinks; the difference between the two is minimal, but binds is easier to set up.

[LIST]
[*]**PARTITIONS**

Firstly you need to sort out the partitions. I'll leave this up to you since I can't really tell you what size to make each partition. However, I advise that you boot into a LiveCD to do the partition work, simply because you need to unmount the /home partition and turn swap off before you can edit the partitions in question, and unmounting /home may be difficult while you're logged in. Once you've created the new partitions, don't forget to set up the folders for each one. Your /home partition will need a folder with your username, and you should probably copy the contents of /etc/skel to it. You can change the ownership of the your home folder from the LiveCD by using the terminal command "chown" with your username's ID number. e.g.
```
sudo chown 1000:1000 /media/home/nathan
```
[COLOR="White"]<linebreak>[/COLOR]

[*]**UPDATE UBUNTU**

Once the partitions have been made, (and assuming you're using a LiveCD), mount your Ubuntu partition. You need to edit the Ububtu partition's /etc/fstab, so
[LIST]
[*]press Alt+F2
[*]type
```
gksu gedit /media/Ubuntu/etc/fstab
```
[*]and press enter
[/LIST]
In the opened file you'll need to do two things. Firstly, the information about /home is now out-of-date. You'll need to modify this line to make sure that Ubuntu mounts the right partition when you next boot it. (Or alternatively, if you decided to merge /home with your Ubuntu partition, just remove this line entirely)

To update the line we need some new information: the new partition's UUID (you can use the /dev identifier if you prefer). You can find this out by opening a terminal and running
```
sudo blkid -c /dev/null
```
Assuming it's the first partition on the extended partition, you'll need to look at the information for the line beginning "/dev/sda5", the UUID will be listed after that, and should look something like
```
UUID="1a79c868-55e9-44cf-a902-0a89cc3ad114"
```
(You need to remove the two quote marks from the fstab line.)
Once you have the UUID for the partition sorted out, you still need to change the rest of the line, since Ubuntu was previously mounting an NTFS partition, not an ext4 partition. Here's what the final line should look like:
```
UUID=1a79c868-55e9-44cf-a902-0a89cc3ad114   /home   ext4   defaults   0   2
```

[*]**ADDING THE STORAGE PARTITION**

Don't close fstab yet, you still need to add the extra lines in to automount the storage partition and bind the various folders. Hopefully you still have the terminal with blkid's output open, but if not, open a new terminal and rerun the command. The NTFS storage partition should also have a UUID (again, you can use the /dev identifier if you prefer), but this UUID is much smaller than the ext4 partition's. It should read something like
```
UUID="7A5C94995C94522D"
```
(Once again, remove the quote marks from the fstab line)

As I mentioned in one of my previous posts, NTFS partitions do not support Linux file permissions. This would severely limit the usability of a data partition if not for a few special mount options we can declare in fstab to get around it (kinda). As you noticed before, everything was owned as root, this is because when it was mounted, the mount program defaulted the permissions to root. We can make the mount program set the ownership and permissions using the uid, gid, and umask arguments. I'm not going to go into depth about these options here, but basically, these options allow you to set the blanket permissions for the entire drive. Assuming you're using the first user on Ubuntu, (the user you created when you installed), your UID and GID will be 1000. You'll probably be fine with a umask of 002. (This gives user 1000 read-write-and execute permissions on everything, and everyone else can just read and execute)

The completed line for mounting the storage partition should look something like:
```
UUID=7A5C94995C94522D   /media/Storage   ntfs-3g   auto,uid=1000,gid=1000,umask=002   0   0
```
[*]**SETTING UP THE BINDS**

This is the easy part. You need one fstab line per folder, and these lines need to be after the storage and home partition's lines. Each line is simple, you just need to specify a folder to bind and a place to bind it, the rest of the line is always the same. e.g.
```
/media/Storage/documents/   /home/nathan/Documents   none    bind   0   0
```
[/LIST]

Now, a completed fstab should look something like this:

```
proc                                      /proc          proc    nodev,noexec,nosuid   0   0
UUID=ccb0fc41-c49b-42bd-b432-c18a8ef164f4 /              ext4    errors=remount-ro   0   1
UUID=1a79c868-55e9-44cf-a902-0a89cc3ad114 none           swap    sw                 0   0
UUID=1a79c868-55e9-44cf-a902-0a89cc3ad114 /home          ext4    defaults           0   2
UUID=7A5C94995C94522D                     /media/Storage ntfs-3g auto,uid=1000,gid=1000,umask=002 0 0
/media/Storage/music/                     /home/nathan/Music      none    bind            0 0
/media/Storage/pictures/                  /home/nathan/Pictures   none    bind            0 0
/media/Storage/documents/                 /home/nathan/Documents  none    bind            0 0
/media/Storage/downloads/                 /home/nathan/Downloads  none    bind            0 0
/media/Storage/videos/                    /home/nathan/Videos     none    bind            0 0

```
(excuse the poor indentation, I've made it as readable as possible without making it perfect)
Hopefully yours resembles it.

If you have any questions, ask away. I'm not sure that I've been as clear as I'd hoped. Just don't panic if you restart the PC and boot into Ubuntu and get a bunch of error messages. Your Ubuntu installation is fine, but you must have made a mistake in fstab. Just boot into a LiveCD, mount the Ubuntu partition, and fix the mistake in fstab. Post it here if you're not sure what mistake you've made and I (or someone else) will point you in the right direction.

---

### Post by WorMzy on 2011-01-18
Double post

---

### Post by natpat on 2011-01-18
I actually love you.

Thank you so much! It worked perfectly! I am now owner of all my documents, everything is mounted perfectly, etc.

Thank you once again! You fixed all three of my problems - the fact pulseaudio wasn't working, Wine wasn't working, and my permissions problem. Thank you!

---

### Post by WorMzy on 2011-01-18
Glad to hear everything's working now. :)

One thing to bear in mind though is that fragmentation can build up on NTFS partitions, so you should let Windows defragment your storage partition every once in a while.

---

