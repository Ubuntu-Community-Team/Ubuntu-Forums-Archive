---
title: "deleting files over NFS"
date: 2009-07-06
forum: General Help
---

### Post by bwm71 on 2009-07-06
I'm seeing a really strange problem where a NFS mounted filesystem becomes read-only after attempting to delete a large number of files.  I'm not sure if it's related to the NAS box serving the filesystem or the Ubuntu machines where it's mounted.  I just did a "apt-get dist-upgrade" on the Ubuntu boxes and the problem just started happening.  And, I can reproduce it on both Ubuntu boxes.

On the NFS partition, I have some directories that contain large numbers of files, around 17,000.  If I try to remove one of these directories with "rm -rf dirname", it seems some files get deleted and then I start getting a bunch of read-only filesystem errors.  The only way to clear the errors is to reboot the NAS box where this NFS partition lives.  If I write a little script that pauses a second or so after deleting each file, the problem doesn't occur.

Also, when the problem occurs, the first error is an input/output error and the rest of the files show the read-only errors.  If I then try to rm(1) the file that gave the input/output, I get a permission denied error, but ls(1) won't list the file.  Something is getting in a confused state, but I'm not sure why or what.

I realize this is a vague description, but I'm hoping someone else maybe has seen an issue with the NFS code in the Linux kernel or something that would explain this.

I'm running Hardy stable with the stock 2.6.24-24 kernel.

Thanks.

---

### Post by LoneWolfJack on 2009-07-06
not exactly a fix for your problem, but rm used to be notorious for having problems when trying to delete many files. last time I ran into this was years ago though.

however, you shouldn't store 17k files in a single directory anyway because this can cause all kinds of problems, from massive performance issues to some commands (like ls for example) not working right.

a reliable solution for your problem would be restructuring your data so that you only have a couple thousand files in a single directory.

---

### Post by bwm71 on 2009-07-07
After posting I was able to reproduce the problem with only 1,000 files in a directory, so not really a reliable solution.

---

