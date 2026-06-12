---
title: "mounting windows share as user"
date: 2009-10-14
forum: General Help
---

### Post by gwpritch on 2009-10-14
I a little unclear as to permissions required to mount a windows share on a folder in my home directory.
I created a samba group with myself as a member. Then using I did the following:
```
sudo visudo
```
and added the following line
```
%samba All=(All) /bin/mount,/bin/umount,/sbin/mount.cifs,/sbin/umount.cifs
```

It was my impression that I should then be able to mount and unmount the folder on my windows box as a user. However I still get the message saying only root may do this. Am I misunderstanding the concept or is there something else I have to do?  Thanks.
I can mount using sudo from the command line but its just a PITA having to do that and entering a password all the time.

---

### Post by kanikilu on 2009-10-14
If you don't want to have to enter a password, I think you need to specify "NOPASSWD" in that line. I'm honestly not sure if it matters, but the only other thing I see is that in the examples there is a comma and a space between the commands...

[https://help.ubuntu.com/community/Sudoers#Common%20Tasks](https://help.ubuntu.com/community/Sudoers#Common%20Tasks)

Other than that, are you sure you are a member of the "samba" group? Maybe you didn't log off and back on for it to take effect? Type **groups** or **id** from the terminal to check.

---

### Post by gwpritch on 2009-10-14
Definitely a member of the samba group. You may be right, it might be a problem with the syntax of the sudoers entry.  I'm not precisely sure that the above is _exactly_ what I entered. Can't check that til I get home tonight.
Thanks.

---

### Post by gwpritch on 2009-10-15
Thanks...I edited the line like so:

```
%samba ALL=(ALL)  NOPASSWD: /bin/mount, /bin/umount...
```

Now works fine. Appreciate your help.

---

