---
title: "Superblock has invalid journal after aborting files system check"
date: 2012-07-12
forum: General Help
---

### Post by gerryg on 2012-07-12
Hi there,

after cancelling a file system check during system startup (by pressing "c"), I cannot mount an ext4 partition (on an external hard disk) anymore.

dumpe2fs tells me that:
"Journal superblock magic number invalid!"

I was trying to specify different superblocks ("dumpe2fs -o superblock=xxx"), obtained by "mke2fs -n", but all of them lead to the same error message.

fsck.ext4 gives the following output:
-----
Superblock has an invalid journal (inode 8).
Clear<y>? no
fsck.ext4: Illegal inode number while checking ext3 journal for home5
-----
Again, I get the same message if I specify a different superblock.

I was browsing the internet to find out whether I should say yes to fsck.ext4's "clear" question, but I am still not sure if this is the right thing to do. It seems that this would destroy the journal and leave the file system as ext2. Is that true? Would all files survive this action?
And is it possible to upgrade to ext3 or ext4 afterwards?

Are there any other options or approaches for my problem?

Many thanks in advance for your help!
Gerald

---

### Post by oldfred on 2012-07-12
I do not know details but have some links.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by gerryg on 2012-07-13
oldfred,

thanks for those links.
Everything points into the direction of clearing inode 8, which is the filesystem journal.

E.g. in the last link, the following is suggested:
-----
# debugfs -w /dev/sdb10
debugfs 1.39 (29-May-2006)
debugfs:  clri <8>
debugfs:  quit
Then, we need to run fsck again, let it fix the cleaned inode.
# nohup fsck -y /dev/sdb10 &
# tune2fs -j /dev/sdb10
Now, the file system has been fixed.
-----
This is similar to what fsck.ext4 wants to do as stated in my first post.

Using backup superblocks doesn't help in my case, they are all equally corrupted.

Since I have no experience with such things: Is it dangerous to clear the journal inode and then restore journaling with tune2fs?
What problems or data loss may be expected?

Thx a lot,
Gerald

---

### Post by gerryg on 2012-07-13
What I forgot to mention: With debugfs (command ls) I am able to see my files.
So maybe they are not lost...

Thx,
Gerald

---

### Post by oldfred on 2012-07-13
I have never done anything more than standard e2fsck, so I do not know. See post #49 by matt_symes on redoing the superblocks.

Some more links 

Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by gerryg on 2012-07-15
Hi again,

after performing "e2fsck" (I recommend to use the "-y" flag to avoid answering "y" a million times), I was able to mount the partition again. "e2fsck" also installed a new journal file, so that I didn't have to invoke "tune2fs" afterwards.
The lost+found folder was full of files which were lost. Since those files also lost their file name, it was a bit cumbersome to transfer them back to their original place, but it worked. (The "file" command was quite helpful to determine the file type.) In the end, it seems that I have recovered nearly everything!

Regards,
Gerald

---

### Post by oldfred on 2012-07-15
Glad it worked out. :)

---

