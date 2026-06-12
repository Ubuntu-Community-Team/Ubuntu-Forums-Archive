---
title: "Do not have permissions for a drive"
date: 2011-05-02
forum: General Help
---

### Post by lumify on 2011-05-02
I cannot access a 1 TB external hard drive from Ubuntu 11.04. It does not show up in the desktop left toolbar, nor does it show up in the file system browser. It does show up in the Disk Utility. In the disk utility, when I click "unmount" the first time after booting, I am suddenly logged off Ubuntu. I can log back in, but I find that really strange. The drive was formatted as ext4 (one partition) by GParted in Puppy Linux.

When I try to access the mount point in the file system browser, I get the error: "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "caa006b4-3b3a-4943-a0be-6a522bb3273a"." In terminal, when CDing to the mount point: "bash: cd: caa006b4-3b3a-4943-a0be-6a522bb3273a: Permission denied"

I cannot just reformat the drive because I have it filled with important data, and I do not have anywhere to back this data up. Any ideas?

---

### Post by lumify on 2011-05-02
Also, I CAN access this drive when I'm trying Ubuntu with the live CD. I like saving files though...

---

### Post by garvinrick4 on 2011-05-02
When you see what is in media as such does it show your drive:
rick@rick-HP:~$ cd /media
rick@rick-HP:/media$ ls -la
total 16
drwxr-xr-x  4 root root 4096 2011-05-02 20:31 .
drwxr-xr-x 23 root root 4096 2011-04-05 23:36 ..
drwxr-xr-x 23 root root 4096 2011-04-28 16:00 lucid
drwxr-xr-x 23 root root 4096 2011-03-14 23:59 maverick
rick@rick-HP:/media$

---

### Post by lumify on 2011-05-02
Yeah, caa006b4-3b3a-4943-a0be-6a522bb3273a is the drive I'm trying to get to. When I cd to that drive, I get an error (that I don't have permissions).

cody@cody:/media$ cd /media
cody@cody:/media$ ls -la
total 12
drwxr-xr-x  3 root root 4096 2011-05-02 22:51 .
drwxr-xr-x 22 root root 4096 2011-05-02 21:43 ..
drwx------  8  999  999 4096 2011-05-02 02:10 caa006b4-3b3a-4943-a0be-6a522bb3273a
cody@cody:/media$

---

### Post by lumify on 2011-05-02
Ideas anyone?

---

### Post by lumify on 2011-05-03
Buuuuuuuuuummp

---

### Post by lumify on 2011-05-03
Is this the right place to post this question? It is a new installation, so would this go in the installation section? Also BUMP.

---

### Post by lumify on 2011-05-03
Tik tok on the clock, but the party don't stop, no.

Anyone know how to make this hard drive more useful than the average brick?

---

### Post by lumify on 2011-05-03
I just figured out how to access it in terminal. I used sudo -s to access it as root. How do I make it so that I don't have to do that though?

Please answer... I have candy...

---

### Post by lumify on 2011-05-03
Using the command "mount", I found this line, which I believe shows the device that I'm trying to access (access without root is what I'm trying to get): /dev/sdc1 on /media/caa006b4-3b3a-4943-a0be-6a522bb3273a type ext4 (rw,nosuid,nodev,uhelper=udisks)

I'm not a programmer; I don't read code. Would anyone with a clue be able to tell me what this means (good, bad, irrelevant?) or point me in some constructive direction?

---

### Post by garvinrick4 on 2011-05-03
rick@rick-HP-testing:~$ cd /media
rick@rick-HP-testing:/media$ sudo chown -R cody:cody /media/caa006b4-3b3a-4943-a0be-6a522bb3273a

---

