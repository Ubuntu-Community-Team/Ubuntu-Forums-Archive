---
title: "sudo segmentation fault"
date: 2010-03-15
forum: General Help
---

### Post by yawnmoth on 2010-03-15
I was trying to edit my sudoers file but wanted to save my original.  So, I renamed the original sudoers to sudoers.org and tried to edit it in vi, only to find that I couldn't.

I then quit and decided I'd rename my sudoers back and found that I couldn't, as demonstrated:

```
user@ubuntu:/etc$ sudo mv sudoers sudoers.orig
[sudo] password for user:
user@ubuntu:/etc$ vi sudoers
user@ubuntu:/etc$ sudo mv sudoers.orig sudoers
sudo: can't stat /etc/sudoers: No such file or directory
Segmentation fault
```
Any ideas?

---

### Post by n0dix on 2010-03-15
You have to use visudo to change your sudoers file.

To solved the problem do: 
Enter to a root session with: su -
then try to rename the sudoers file.

---

### Post by soltanis on 2010-03-15
Next time use visudo only. Don't move the sudoers file.

If you were lucky/smart enough to set a root password:
```

su -
# (you will need to enter the root password)
mv /etc/sudoers.orig /etc/sudoers
exit

```

Then swear never to do that again.

If you didn't set a root password, insert a live CD; mount your drive; then attempt to return the file to its rightful place. And again never do that again.

In this example I assume /dev/sda2 is your linux / partition. Change this to whatever your linux partition happens to be.
```

# in live CD session
sudo su
mkdir -p /media/drive
mount /dev/sda2 /media/drive
cd /media/drive/etc
mv sudoers.orig sudoers
exit

```

If you want to find out where your linux partition is, from your normal session (not liveCD) do:
```

mount

```

The relevant line will look like
```

/dev/sda1 on / type ext4 (rw,errors=remount-ro)

```

---

### Post by yawnmoth on 2010-03-16
That worked - thanks!

---

