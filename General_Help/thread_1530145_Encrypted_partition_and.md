---
title: "Encrypted partition and"
date: 2010-07-13
forum: General Help
---

### Post by wiktor00 on 2010-07-13
I have a problem, which I describe on my language ubuntu forum, but no one can help me.

I created encrypted ext4 partition with gnome-disk-utility.
It is only password, no encryption-keys etc.

I want this partition to mount automatically, but only for one user (not administrator). A window for typing password should be after login on this user (not a booting system). I want also to hide this partition, no one except this one user won't see it. (I can't make this ext4 partition hide, I've tried with GParted and gnome-disk-utility, but with no effect.) I've tried a lot of programs: pysdm, MountManager, I've read manuals and some articels about fstab and mount. 

Maybe is another solution to my problem or there is easier way to do it?
Thank you in advance for help :)

---

### Post by restorator on 2010-07-13
Sounds like truecrypt will do most of that except it will not mount automatically in ubuntu. Read more about it here: [http://www.truecrypt.org](http://www.truecrypt.org)

---

### Post by wiktor00 on 2010-07-14
Thanks to restorator,
I solved only a problem of hiding and encrypting partition, but it's only a half of problem. Unfortunately Truecrypt don't support ext4, but I created ext3.

**[SIZE=4]EDIT: [/SIZE][SIZE=4]I solved whole problem.[/SIZE]** I've read a lot of threads and some manuals and I've found the solution. **I'm giving full HOW-TO if somebody will want do it in the future.**

**[SIZE=4]1.[/SIZE]** I created hidden partition in Truecrypt. (with graphical interface it's ridiculously simple)

**[SIZE=4]2. [/SIZE]**If you want to mount this partition at start, you'll add this to Startup Programs
```
truecrypt /dev/nameofpartition /media/device
```Name of partition are different and mounting point depends to you.
This command has a lot of attributes, you can read about it here [http://www.truecrypt.org/docs/?s=command-line-usage](http://www.truecrypt.org/docs/?s=command-line-usage)

**[SIZE=4]3. [/SIZE]**Now you must solve the problem of administrator privileges:
(There are 2 possibilities)

[LIST]
[*]run ```
sudo visido
```
[/LIST]
OR

[LIST]
[*](it'll open the same file as in first  option, but in other editor)```
sudo gedit /etc/sudoers 
```
[/LIST]
and at the end of file paste ```
%admin ALL=NOPASSWD: /usr/bin/truecrypt
```(This will allow anyone in the admin group  to run truecrypt without having to enter  the administrative password.** You can replace %admin with your username (without the %) to only give  yourself this privilege. A reboot is necessary for it to take effect**.)

I hope this HOW-TO will help some people in the future :)

---

