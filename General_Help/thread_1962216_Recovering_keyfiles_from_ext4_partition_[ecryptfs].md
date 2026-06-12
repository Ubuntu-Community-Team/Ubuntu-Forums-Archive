---
title: "Recovering keyfiles from ext4 partition [ecryptfs]"
date: 2012-04-20
forum: General Help
---

### Post by Qazjap11 on 2012-04-20
Hello,
I did a terrible mistake by running a script that wiped up my user's files, and even more terrible mistake by not backuping the files. :(
I managed to recover about 60GB of my home partition, using extundelete, but the files are mostly encrypted, and I couldn't find the key file among them.
If I am not wrong, the keyfile is /home/user/.ecryptfs/user/.ecryptfs/wrapped-passphrase
Am I right? Are there more relevant files?
The problem is I couldn't manage to recover it till now.

Some technical information:
Ubuntu 10.04 / ext4
```

/dev/sda8            2213       26529   195311616   83  Linux 
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype e xtent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize 
Filesystem flags:         signed_directory_hash  
Default mount options:    (none) 
Filesystem state:         not clean with errors 
Errors behavior:          Continue 
Filesystem OS type:       Linux 
Inode count:              12214272 
Block count:              48827904 
Reserved block count:     2441395 
Free blocks:              47976917 
Free inodes:              12206004 
First block:              0 
Block size:               4096 
Fragment size:            4096 
Reserved GDT blocks:      1012 
Blocks per group:         32768 
Fragments per group:      32768 
Reserved GDT blocks:      1012 
Blocks per group:         32768 
Fragments per group:      32768 
Inodes per group:         8192 
Inode blocks per group:   512 
Flex block group size:    16 
Filesystem created:       Mon May  2 16:50:04 2011 
Last mount time:          Mon Apr 16 14:43:04 2012 
Last write time:          Mon Apr 16 21:17:52 2012 
Mount count:              25 
Maximum mount count:      37 
Last checked:             Thu Apr  5 11:56:17 2012 
Check interval:           15552000 (6 months) 
Next check after:         Tue Oct  2 10:56:17 2012
 Lifetime writes:          1089 GB 
Reserved blocks uid:      0 (user root) 
Reserved blocks gid:      0 (group root) 
First inode:              11 
Inode size:               256 
Required extra isize:     28 
Desired extra isize:      28 
Journal inode:            8 
Default directory hash:   half_md4 
Directories:              1154

```The relevant folder through debugfs:
```

 5242882   40755 (2)   1000   1000    4096 16-Apr-2012 20:40 .  
5242881   40755 (2)      0      0    4096  2-May-2011 16:59 .. 
<     0>      0 (2)      0      0       0                   .ecryptfs  
5242884   40700 (2)   1000   1000   32768 16-Apr-2012 20:59 .Private

```I managed to recover this folder as a file (61440 bytes) throught extundelete --recover-file. Does it help some way?

Thanks in advance, Qazjap11.

---

### Post by iponeverything on 2012-04-20
> eCryptfs requires that the user's mount passphrase be inserted into
the user session keyring in order to access the files under the
~/Confidential/ mount point. The mount passphrase is wrapped
(encrypted) with the user's login passphrase and is stored in the
~/.ecryptfs/wrapped-passphrase file. When the user logs in, the
eCryptfs PAM module intercepts the user's login passphrase, uses it to
decrypt the wrapped mount passphrase, and inserts the unwrapped mount
passphrase into the user session keyring.


Do you have your mount passphrase?  If you do, re-create the environment on a clean system - copy the encrypted directory over along with the file from your .ecryptfs directory.

---

### Post by Qazjap11 on 2012-04-20
Unfortunately, this is what I am trying to recover...
So if I understand well, the files are encrypted with that passphrase which is stored encrypted at the wrapped-password file?

---

### Post by iponeverything on 2012-04-20
Every time you accessed the data did you have input the passphrase?

---

### Post by Qazjap11 on 2012-04-21
I logged into my user...

---

### Post by Qazjap11 on 2012-04-22
Fortunately I managed to locate the file within the recovered files by extundelete. I used the fact that it weighted 48 bytes (though as I noticed it can be any multiple of 8).

---

### Post by iponeverything on 2012-04-22
One has to wonder about the usefulness of encryptfs, given the apparent ease that it can be defeated. 

I use whole disk encryption because I travel so much, loosing or getting my laptop stolen would not that big of deal since I would not have to worry about all credit card and bank information living on my machine..

---

