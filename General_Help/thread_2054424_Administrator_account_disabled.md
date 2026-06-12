---
title: "Administrator account disabled"
date: 2012-09-07
forum: General Help
---

### Post by Royalist on 2012-09-07
I am unable to change my password even in root (recovery mode), or to unlock it. I can still access my account, but without password protection. In GUI Administrator account 'disabled' is displayed.

This is what I have done so far:

```
In root:# <usermod -U roy>
usermod:cannot lock /etc/passwd; try again later

~#<passwd roy>
<Enter new Unix password:done>
<Retype new Unix password:done>
passwd:Authentication token manipulation error
passwd:password unchanged

<passwd -a -S>
roy L 09/05/2012 0 99999 7 -1

<passwd -d roy>
passwd:cannot lock /etc/shadow; try again later
```

Two days later again root shell:

```
<mount -o rw,remount />

<chmod 0440 /etc/sudoers>
<ls -l /etc/sudoers>
-r--r----- 1 root root 574 2011-09-11 (todays date is 2012-09-07).
```

I think that I have to admit that "I am in out of my depth".

Would anyone please help??

:confused:

---

### Post by CharlesA on 2012-09-07
Try changing the password after you made the file system read/write:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by muteXe on 2012-09-07
[http://0x109.tuxfamily.org/ubuntu-authentication-token-failure/](http://0x109.tuxfamily.org/ubuntu-authentication-token-failure/)

any use?

---

### Post by Royalist on 2012-09-10
Yes Thanks Done all that!

---

### Post by CharlesA on 2012-09-10
Why did you need to chmod the sudoers file?

Try running a fsck from a livecd, if the partition isn't being mounted as read/write, it is likely it has errors on it.

---

