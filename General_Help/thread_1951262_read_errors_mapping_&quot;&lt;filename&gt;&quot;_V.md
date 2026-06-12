---
title: "read errors mapping &quot;&lt;filename&gt;&quot;: Value too large for defined data type (75)"
date: 2012-04-02
forum: General Help
---

### Post by plut0 on 2012-04-02
I am getting this error when trying to copy/move/rsync a few files.  What is going on here?

> cp: read errors mapping "<filename>": Value too large for defined data type (75)

I checked out the source files and they seem fine to me.

---

### Post by Paddy Landau on 2012-04-02
Please let us know the system you are using. In a terminal, type the following two commands and post the output:
```
lsb_release -d
uname -m
```I think we also need to know more about the source and target. Can you give  one example of an actual command you used, also letting use know the  file system (e.g. NTFS, FAT16, FAT32, ext4) of both the source and target. Also let us know the size of the file.

---

### Post by plut0 on 2012-04-02
```
# lsb_release -d
Description:	Ubuntu 10.04.4 LTS
# uname -m
x86_64

```

I'm copying from ntfs via fuse to xfs.  This is affecting multiple files of various sizes, from 150mb to 30gb.

---

### Post by matt_symes on 2012-04-02
Hi

Can you open the files normally ? What type of files are they ?

How many files are there that are giving you trouble ?

Have you ran chkdsk on the NTFS filing system to ensure it's not corrupted ?

Have you tried to copy them to a filing system other than xfs such as ext4 ?

Kind regards

---

### Post by plut0 on 2012-04-02
These are video files.  I am having trouble reading these NTFS source files from Linux.  However, doing so from Windows, the files are perfectly fine.  I did run a chkdsk, no errors.  I did try copying to another file system, same issues.  It looks like the destination doesn't matter, I can't read the source.

---

### Post by matt_symes on 2012-04-02
Hi

I'm not sure why it's not copying. Did you format the NTFS partition using an unusual method ?

Have you tried to use dd to copy the files ? You can set different block sizes and such to copy each file. Copy a file somewhere first, as a dry run, to an empty disc or partition.

Be very careful if you try this and make sure you get the command correct but that may copy it.

Also, see what others think.

Kind regards

---

### Post by plut0 on 2012-04-02
I've been using this file system for ~6 months, only now is it giving me trouble.  dd fails as well, same error.

---

### Post by matt_symes on 2012-04-02
Hi

Is there anything on the log files when you try to copy ?

Open a terminal and type

```
tail -f /var/log/syslog
```

Then try to copy a file. Is there any more useful information about what the problem may be displayed in the terminal ?

Kind regards

---

### Post by Paddy Landau on 2012-04-03
> **plut0 said:**
> I am having trouble reading these NTFS source files from Linux.
That is a problem. Ubuntu should have no problem whatsoever reading from and writing to NTFS.

Please check that you have both [FONT=Lucida Console]ntfs-3g[/FONT] and [FONT=Lucida Console]ntfsprogs[/FONT] installed.

Google the error you had, and you'll see that it is usually to do with having too large a file; but that should not be a problem in your case (unless Fuse has restrictions of which I am unaware).

Try copying one of the problematic files to nowhere, as follows:
```
cp [FONT=Verdana]*filename*[/FONT] /dev/null
```What happens?

---

### Post by plut0 on 2012-04-03
I was able to get around the issues only with the help of Windows.  What I did was copy the file to a new name.  I ran a md5sum check and the source and destination are exactly the same.  After that I logged into Linux and was able to read the new file just fine.

What does this mean?  Is this a corrupt file system or a ntfs-3g issue?  Like I said earlier, chkdsk didn't find any issues with the file system so I'm not sure what is going on.

@Paddy Landau
@matt_symes

I will try your suggestions tonight and get back to you.

---

### Post by plut0 on 2012-04-03
@matt_symes
I see this in the logs:

Apr  3 17:10:35 sarpedon ntfs-3g[2175]: Failed to decompress file: Value too large for defined data type
Apr  3 17:10:35 sarpedon ntfs-3g[2175]: ntfs_attr_pread error reading '/00030.m2ts.old' at offset 120979456: 4096 <> -1: Value too large for defined data type


@Paddy Landau
Fails with same error.

---

### Post by Paddy Landau on 2012-04-04
I'm sorry, at this point I do not know what is happening. It seems as though the file is compressed on your NTFS source, although as far as I know ntfs-3g can cope with that.

---

### Post by plut0 on 2012-04-04
I don't believe these files are compressed, I will double check later.

---

### Post by matt_symes on 2012-04-05
Hi

Can we check the version as well.

Please post the output of.

```
ntfs-3g --version
```

This is my version on 12.04

```
matthew@matthew-Aspire-7540:~$ ntfs-3g --version
ntfs-3g 2012.1.15AR.1 external FUSE 28
matthew@matthew-Aspire-7540:~$ 
```

If the version is lower on 10.04 then download 12.04 and create a CD/USB and then try to copy the files from a LiveCD/USB session.

This may be a problem with ntfs-3g and the version you are using.

**EDIT:** Please post the output of commands between code tags like this

[noparse]```
output from command
```[/noparse]

to get output like this

```
output from command
```

Kind regards

---

