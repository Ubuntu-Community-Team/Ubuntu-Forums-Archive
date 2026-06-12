---
title: "ecryptfs filling up home partition?"
date: 2010-10-14
forum: General Help
---

### Post by globaljuggler on 2010-10-14
I have my home at a separate partition about 130 GB big which I thought would be sufficient but I recently noticed that I only have 6 GB left which puzzled me. I turns out that there is a hidden folder called /home/.ecryptfs/myusername/.Private with 52 folders and 56 315 items weighing a total of 121.6 GB. The folders have names like ECRYPTFS_FNEK_ENCRYPTED.FWZxhlLHzzw.KkQsyOuV9NZAydF4-sm15sF9E27W0Y0yBm2EnXL-3knZPk--

This can't be normal, can it?

I am running Ubuntu 10.10 and I have chosen to encrypt my home which I'm sure is of relevance here.

Please help a semi-newbie :)

---

### Post by DZ* on 2010-10-14
The minimum encrypted file size is 12 kb. This can be reduced to 4 kb if "ecryptfs_xattr_metadata" mount option is used, 

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=17398957aa0a05ef62535060b41d103590dcc533](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=17398957aa0a05ef62535060b41d103590dcc533)

but this is not a default option.

---

### Post by globaljuggler on 2010-10-15
Thanks for the reply but I don't think that's the issue here.

I have two user accounts and the two user folders weigh together 762 MB with 55 items. 

Then I have the folder /home/.ecryptfs/username/.Private which weighs 121.6 GB with 56 283 items.

---

### Post by mike2357 on 2010-10-15
For files in the .Private directory, there should be corresponding unencrypted virtual files in the Private (no leading period) directory.  You can run the following command from each user's home directory to verify this:
```
du -s .Private Private
```
You should get the same size.  Assuming you do, then you can check files in the Private directory and delete ones you don't want.  Pay particular attention to "hidden" files and directories, i.e. those that begin with a period.  For instance, my Private directory has a sub-directory called ".Trash-1000" which is where other files I've deleted from Private are temporarily stored.  To truly get files deleted, I need to first delete the file, and then when I'm done and sure I haven't accidentally deleted something, wipe out the contents of /home/<username>/Private/.Trash-1000.  Of course, take the usual precautions before doing so -- make sure you're deleting the correct files since once you do so, they're gone for good.  So you might want to make a backup copy before beginning.

---

### Post by globaljuggler on 2010-10-15
Thanks, but I have chosen to encrypt my entire home directory. Not just the private-folder.

---

