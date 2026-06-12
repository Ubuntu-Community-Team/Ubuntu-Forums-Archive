---
title: "Only root can access DVD"
date: 2010-04-04
forum: General Help
---

### Post by mencargo on 2010-04-04
I can play several DVDs, but there is this special DVD, that I can only see the VIDEO/AUDIO folders, with nothing inside.
But I can see files if I browse as root. (Normal Video DVD with VOB files)
I think there's something wrong with permissions:

```
manuel@casa:~$ ls -l /dev/scd* /dev/dvd* /media/cdrom*
lrwxrwxrwx 1 root root    3 2010-04-04 08:42 /dev/dvd -> sr0
lrwxrwxrwx 1 root root    3 2010-04-04 08:42 /dev/dvdrw -> sr0
lrwxrwxrwx 1 root root    3 2010-04-04 03:42 /dev/scd0 -> sr0
lrwxrwxrwx 1 root root    6 2010-04-02 13:01 /media/cdrom -> cdrom0

/media/cdrom0:
total 0

/media/cdrom1:
total 0

```

Shouldn't scd0 be as root:cdrom ?
That's all I got... haha

Groups:

```
manuel@casa:~$ groups
manuel adm cdrom audio video plugdev fuse lpadmin admin sambashare

```

I'm clueless here...

---

### Post by TheHimself on 2010-04-04
You can make it your own by
```

sudo chown manuel:manuel /dev/scd0
```

---

### Post by mencargo on 2010-04-04
Quick solution, but I'm not the only user at this computer.

If I understand correclty, all users are part of the cdrom group, so if I make the group cdrom owner of the DVD device everyone could play it..?

I just did:
sudo chown root:cdrom /dev/scd0
sudo chown root:cdrom /media/cdrom*

But permissions remain untouched.
Other ideas?

---

### Post by theozzlives on 2010-04-04
```
sudo chown manuel:manuel /dev/scd0
sudo chmod 777 /dev/scd0
```

I get the following on mine:
```
ozzie@ozzie-laptop:~$ ls -l /dev/scd* /dev/dvd* /media/cdrom*
ls: cannot access /media/cdrom*: No such file or directory
lrwxrwxrwx 1 root root 3 2010-04-04 08:48 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-04-04 08:48 /dev/dvdrw -> sr0
lrwxrwxrwx 1 root root 3 2010-04-04 08:48 /dev/scd0 -> sr0

```

---

### Post by mencargo on 2010-04-04
Seems I can't:

> manuel@casa:~$ sudo chown manuel:manuel /dev/scd0
manuel@casa:~$ sudo chmod 777 /dev/scd0
manuel@casa:~$ ls -l /dev/scd* /dev/dvd*
lrwxrwxrwx 1 root root 3 2010-04-04 08:42 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-04-04 08:42 /dev/dvdrw -> sr0
lrwxrwxrwx 1 root root 3 2010-04-04 03:42 /dev/scd0 -> sr0


---

### Post by theozzlives on 2010-04-04
> **mencargo said:**
> Seems I can't:

well you have rwx permissions for everyone, are you in the CDROM group & do you have permissions to access the CDROM?

---

### Post by carlosgs91 on 2010-04-04
.

---

### Post by Pykler on 2010-12-30
They are all symlinks, the actual sr0 for me was like this.

```

% ls /dev/sr0*
brw-rw----+ 1 root cdrom 11, 0 30.12.2010 01:01 /dev/sr0

```

I have the same issue with a dvd I am trying to play, it nly works if I open totem as root

```

sudo totem

```

---

