---
title: "VSFTPD user permission problem"
date: 2010-04-19
forum: General Help
---

### Post by the real omni on 2010-04-19
I have vsftpd running, have two users whose homedirs are, let's say, /home/user1 and /home/user2 and two directories, let's say /web/dir1 and /web/dir2 which each have 775 perms. 

/web/dir1 is owned by the dir1 group and /web/dir2 is owned by the dir2 group. 

In both /home/user1 and /home/user2 there are two symlinks that point to /web/dir1 and /web/dir2 (ie, 2 symlinks in each home dir, so both users have links to either web dirs) and both users are members of the dir1 and dir2 groups. 

User1 is able to log in through SSH or FTP and change dirs into /home/user1/dir1 (mapped to /web/dir1) and user2 can do the same through SSH but not through FTP. User2 can log in through FTP, but is unable to change into either of the directories in /web/

As far as I can tell, both users and dirs are set up exactly the same - so why would SSH work for user2 but not FTP?

---

### Post by the real omni on 2010-04-19
Correction:

It turns out both user1 and user2 are able to connect via SSH, but NEITHER are able to use FTP properly.

Both users can connect to FTP but neither can change directories from / to /dir1 or /dir2

(remember both /dir1 and /dir2 from the FTProot dir are mapped to the actual dirs /web/dir1 and /web/dir2)

---

### Post by the real omni on 2010-04-19
Okay looks like it was the chroot_local_users option in /etc/vsftpd.conf

So this brings me to the next question: is there a way to enable chroot_local_users but also have links in a user's homedir that allows them access to a single directory outside of the chroot dir?

---

