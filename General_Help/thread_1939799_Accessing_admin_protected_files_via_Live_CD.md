---
title: "Accessing admin protected files via Live CD"
date: 2012-03-12
forum: General Help
---

### Post by Tornikee on 2012-03-12
Hello,

My 11.10 doesn't load past loading screen ([thread]("http://ubuntuforums.org/showthread.php?t=1939635")) anymore, so I have decided to reinstall it (wanted to install 64-bit version anyway, so it's not a big issue). So I booted via Live CD to back my files up to Windows partition, but can't access about half of the files due to lack of admin permissions.

How can I access this Ubuntu partition with admin rights so that I can copy all files from there?

Thanks in advance.

---

### Post by winh8r on 2012-03-12
You should be able to use:

```
sudo chown -R /path/to/directory ubuntu
```

in the live cd.

---

### Post by Tornikee on 2012-03-12
> **winh8r said:**
> You should be able to use:

```
sudo chown -R /path/to/directory ubuntu
```in the live cd.
Thanks for the response. I used

```
sudo chown -R /home/tornike ubuntu

```According to the directory I need to access, but the return was:
```
chown: invalid user: `/home/tornike'

```So I probably got something wrong?

Edit: I understand that using that command pointed to the Live CD root folder, but what should I change to point it to the Ubuntu installation partition I need to access?

---

### Post by winh8r on 2012-03-12
If you are going to reinstall anyway then just run the command with the name of the partition .

like this :
```

sudo chown -R /dev/sda ubuntu
```

where /dev/sda is the name of the partition on your machine.

you can find out what it is by running the Disk Utility and identifying the linux partition which should be formatted as ext4 and marked boot

---

### Post by Tornikee on 2012-03-12
NVM, I did it through accessing Nautilus with admin permissions:

```
gksudo nautilus
```

P.S. Thanks for the explanation anyway.

---

### Post by winh8r on 2012-03-12
Glad you got it sorted out.

It would have been so much easier if I had thought about Nautilus first!!!!

---

