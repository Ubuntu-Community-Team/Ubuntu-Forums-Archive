---
title: "Administrator login"
date: 2009-12-10
forum: General Help
---

### Post by sandy4linux on 2009-12-10
hi,
 I am using Ubuntu 9.10 on acer aspire one. I am unable to create any folders in usr/bin/lib folders. Its showing that I have no administrator rights. I tried to open an account as root, what does it do? I need to know. why am I getting denied?

Regards

---

### Post by hobit on 2009-12-10
File / folder permissions.  Have you tried using sudo?

---

### Post by cariboo on 2009-12-10
Press Alt-F2 and type:

```
gksudo nautilus
```

The above command runs the file manager as root, allowing you to manipulate files/directories.

---

### Post by sandy4linux on 2009-12-10
Yes I have tried using sudo in terminal and typed my password, its showing authentication failure.

Regards

---

### Post by snowpine on 2009-12-10
[Here is a visual guide to using sudo]("http://xkcd.com/149/").

---

### Post by sandy4linux on 2009-12-10
Can u help me to access sudo in terminal??

---

### Post by snowpine on 2009-12-10
> **sandy4linux said:**
> I tried to open an account as root, what does it do? 

The first account you created (when you installed Ubuntu) should be able to use sudo. If that doesn't work, possibly you broke sudo while trying to open a root account (which is not supported here).

Here are a couple of guides to repairing broken sudo:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by hobit on 2009-12-10
First be sure you are using the correct password, case sensitive.  Beyond that do you know the root or su password?  Is yours the only user account on this install?

---

### Post by sandy4linux on 2009-12-10
I have only 1 password and 1 user account. I tried to get in to su its authentication failure.
I tried to open root account by editing in user and account( just the name and password) to gain access as administrator, since I was not able to create a folder in usr/lib.
Then I checked the below mentioned link, and tried to open a root account, just to check whether I could perform this action.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Following commands
sudo -i
sudo passwd root
sudo usermod -p '!' root

---

### Post by sandy4linux on 2009-12-13
Hey snowpine could you pls help me.. I have tried to change edit software source to activate my gns3 network simulator, and it shows me the same message. can u pls help to gain my admin rights.

---

### Post by snowpine on 2009-12-13
> **sandy4linux said:**
> Hey snowpine could you pls help me.. I have tried to change edit software source to activate my gns3 network simulator, and it shows me the same message. can u pls help to gain my admin rights.

Sorry, I can't help (other than providing the link below), because I have never tried to enable a root account in Ubuntu. It is not something we support here on Ubuntu Forums.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

