---
title: "ls command not working properly in encrypted home dir"
date: 2011-03-01
forum: General Help
---

### Post by zeigerpuppy on 2011-03-01
I have installed Ubuntu 10.10 to a live USB stick and created a new user with an encrypted home directory.

Everything is working fine apart from a weird problem.

when I create a new file or directory in the encrypted home it does not show up in directory listing.

eg:
cd ~/Documents
touch test.txt

ls -al
drwxr-xr-x  2 USER USER  4096 2011-03-02 14:12 .
drwx------ 32 USER USER  8192 2011-03-02 13:03 ..

if I try editing the file by entering the path, it works, even though ls does not list it!

eg: nano ./test

ls as root makes no difference and the file is not hidden.

If I create a file in nautilus, it shows there but still does not show in the terminal or any other app.

rebooting makes the files visible.
sudo sync does not change anything.

Weird, any ideas?

I think it is related to the encrypted home because the 'ubuntu' user is not affected by the problem in its home.

---

### Post by Smart Viking on 2011-03-01
Hm that is a really interresting problem!

Does the "dir" command work? Does it behave differently of you do ls and pass the full path as an argument?

Can you give more general information about the system, do you use ext4 etc.

---

### Post by zeigerpuppy on 2011-03-02
dir and ls with the full path cause the same problems.

looks like the partition format is eCryptfs

the filesystem is loop mounted as
/home/USER/.Private     1.9G  455M  1.4G  25% /home/USER

in the filsystem there is a symlink to 

.Private -> /home/.ecryptfs/USER/.Private

this document seems to detail the method more but there's no mention of this problem there.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[http://ecryptfs.sourceforge.net/ecryptfs-faq.html](http://ecryptfs.sourceforge.net/ecryptfs-faq.html)


I found one problem similar on the ecryptfs-user forums
[http://sourceforge.net/mailarchive/forum.php?thread_name=4255c2570811170800u7f954131h8f661fc1c5894656%40mail.gmail.com&forum_name=ecryptfs-users](http://sourceforge.net/mailarchive/forum.php?thread_name=4255c2570811170800u7f954131h8f661fc1c5894656%40mail.gmail.com&forum_name=ecryptfs-users)

looks like it may be a 'feature' to hide files from ls,
surely this shouldn't happen to files created by the user while looged in and authenticated to the partition however, still confused!

is it possible that it's something to do with it being on a USB flash drive?

---

