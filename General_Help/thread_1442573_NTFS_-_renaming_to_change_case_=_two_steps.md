---
title: "NTFS - renaming to change case = two steps?"
date: 2010-03-30
forum: General Help
---

### Post by HotForLinux on 2010-03-30
When I try to rename a file in a mounted NTFS file system by only changing the letter case, I receive an error message saying that it is not possible because the file already exists. This must be because ntfs is not case sensitive as regards determining a file name. However, it can use and remember whatever case you want to use. So I can change the letter case in the file's name in two steps: saving the file with a different name first and then renaming it again with the original name and the letter cases I want to use.

I think this should be fixed.

---

### Post by ajgreeny on 2010-03-30
But surely that's an NTFS problem, not something that any linux/ubuntu devs can do anything about.

Or have I got the wrong end of your stick?

---

### Post by Mark Phelps on 2010-03-30
> **HotForLinux said:**
> ... This must be because ntfs is not case sensitive as regards determining a file name. 

You answered your own question.

---

### Post by falconindy on 2010-03-30
What driver are you using to mount the NTFS partition? ntfs or ntfs-3g? The latter should have no problems doing this.

---

### Post by HotForLinux on 2010-03-30
> **falconindy said:**
> What driver are you using to mount the NTFS partition? ntfs or ntfs-3g? The latter should have no problems doing this.

I would like to know what is the correct way to find out, in each case, what drivers are being used.

After looking in many places without finding a clue, I found this:

```

$ aptitude search ntfs|grep "^i"
i   libntfs-3g12                    - ntfs-3g filesystem in userspace (FUSE) lib
i A libntfs-3g23                    - ntfs-3g filesystem in userspace (FUSE) lib
i   ntfs-3g                         - read-write NTFS driver for FUSE  

```

So it seems that I'm using ntfs-3g.
The truth is I don't know now if Windows behaves the same way nor if this is unavoidable, but it is not nice. It's odd.

---

### Post by HotForLinux on 2010-03-30
> **Mark Phelps said:**
> You answered your own question.

What question??

---

### Post by HotForLinux on 2010-03-30
> **ajgreeny said:**
> But surely that's an NTFS problem, not something that any linux/ubuntu devs can do anything about.

Or have I got the wrong end of your stick?

Yes, of course. I believe this behavior must be common to many, if not all, Linux distros (as I have just said, I don't even know if it happens in Windos versions) and I don't know if it can be fixed. But if it should be be fixed, I'm shure many people here must know much better than me what should be done with this matter.

---

### Post by falconindy on 2010-04-01
With the partition in question mounted, please show us the output of the 'mount' command. You can trim the output down to the single relevant line, if you'd like.

It's been a while, but I don't believe this behavior exists in Windows, nor does it happen on my NTFS formatted flash drive.

---

### Post by HotForLinux on 2010-04-02
**[COLOR=Red]=================================[/COLOR]**[B][COLOR=Red]
Sorry... Sorry...Sorry...  Stupid mistake.
This behavior happens when using a FAT32 file system and it _does not_ HAPPEN when using the NTFS filesystem in this PC.[/COLOR][/B] 
[COLOR=Red]**====================================**[/COLOR]

But, all the same, the behavior is awkward.

Just in case, the **mount** output, for this FAT partition, is:
/dev/sda7 on /windows/D type vfat (rw,utf8,umask=007,gid=46)

For the NTFS partition is
/dev/sda1 on /windows/C type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)

---

### Post by dcstar on 2010-04-03
> **HotForLinux said:**
> **[COLOR=Red]=================================[/COLOR]**[B][COLOR=Red]
Sorry... Sorry...Sorry...  Stupid mistake.
This behavior happens when using a FAT32 file system and it _does not_ HAPPEN when using the NTFS filesystem in this PC.[/COLOR][/B] 
[COLOR=Red]**====================================**[/COLOR]

But, all the same, the behavior is awkward.

Just in case, the **mount** output, for this FAT partition, is:
/dev/sda7 on /windows/D type vfat (rw,utf8,umask=007,gid=46)

For the NTFS partition is
/dev/sda1 on /windows/C type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)

FAT is a case-insensitive file system. Linux is a case-sensitive OS that will pass on rename requests for the particular filesystem driver to implement (or not).

---

### Post by HotForLinux on 2010-04-03
> **dcstar said:**
> FAT is a case-insensitive file system. Linux is a case-sensitive OS that will pass on rename requests for the particular filesystem driver to implement (or not).

That's what I said: It is case insensitive, but it remembers the case. The same happens with NTFS, doesn't it?
So, you can rename a file to change the letter case in its name letters, but that has to be done in two steps for FAT32. It cannot be done in just one, as in NTFS. Got the point?
I ignore now whether it is like this in windos systems.

---

