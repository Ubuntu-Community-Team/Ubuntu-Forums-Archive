---
title: "Wierd permissions puzzle"
date: 2009-10-31
forum: General Help
---

### Post by hg21 on 2009-10-31
I recently downloaded a .zip and unzipped. I subsequently tried to edit one of the contained text files with kate. It came up read only. Even kdesudo kate did not allow editing. 

I checked ownership and permission > self and  -rw-rw-rw-. I even sudo chmod and re-did them - no change. 

As a last resort I tried vi (haven't used it for years) - still read only. Re-named the file - still couldn't edit. 

In the end I did a copy and paste into an empty kate and saved to another name then I could edit.

I'd be glad if someone could suggest what might be the reason. Have I overlooked something blindingly obvious? 

(I am using 9.10 - great so far)

---

### Post by lilbill on 2009-10-31
Check the permissions for the directory containing the file...could be read only for you

---

### Post by hg21 on 2009-10-31
> **lilbill said:**
> Check the permissions for the directory containing the file...could be read only for you

I had done that but forgot to say - it's drwxrwxrwx and so is the one above that.

---

### Post by lilbill on 2009-10-31
I don't know then...free bump for someone who does ;)

---

### Post by seeker5528 on 2009-10-31
Every time I have run across a file I could not edit, delete, etc... as the superuser it turned out to be a file system issue.

The easier option is to boot off of the Ubuntu CD or other live CD and run fsck from there:

fsck /dev/sdX

: replacing sdX with the actual partition you want to check for errors.

Alternatively you could choose the recovery boot option from the Grub menu to get into single user mode, hit the enter key if it asks for the root password, then issue the command:

```
mount -o remount,ro /
```

The output of:

```
cat /etc/mtab
```

or

```
cat /proc/mounts
```

should show something along the lines of:

```
rootfs / rootfs ro 0 0
```

so you can see the 'ro' in there indicating the partition is actually remounted read only.

Then you can do your fsck and reboot the system when it's done.

EDIT: The above examples assume you have a single partition, if the file is located on a separate partition you have to adjust the locations accordingly and you could unmount them instead of remounting read only when booted into single user mode.


Reading the situation  again, since this file was extracted from a zip file there could be some quirk with that. If you could copy the contents of the file into a new file and delete the original that would be even easier, but I would still be tempted to fsck.

Later, Seeker

---

### Post by hg21 on 2009-11-02
Thanks for your response seeker5528.

Forgive me if I'm being stupid but I don't see how it can be a file system mount problem. I only applies so far as I know to 4 files from a .zip.  

I can get round it by a cut and paste copy but I am intrigued about how it could happen.

---

### Post by seeker5528 on 2009-11-02
> **hg21 said:**
> Thanks for your response seeker5528.

Forgive me if I'm being stupid but I don't see how it can be a file system mount problem. I only applies so far as I know to 4 files from a .zip.  

I can get round it by a cut and paste copy but I am intrigued about how it could happen.

It's an odd problem.

File system problems can cause you not to be able to work with a file normally, the only issue with mounting would be if you wanted to boot to the boot recovery menu, go into single-user mode and then run fsck because you don't want to run fsck on a partition that is mounted in read/write mode.

If there is only an issue with these 4 files extracted from the .zip and it happens consistently on multiple attempts to extract the files......

Could be an issue with the .zip file, if it is an option you might try to acquire the file again.

Doesn't really do much for figuring out why this happened but for testing purposes it would be interesting to see if you copy one of the files in question, if the copy can be edited and also see if you can use cat to copy the stuff to a new file and edit the resulting file.

```
cat oldfile > newfile
```

later, Seeker

---

