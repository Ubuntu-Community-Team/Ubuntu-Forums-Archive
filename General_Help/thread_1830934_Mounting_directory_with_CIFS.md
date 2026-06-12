---
title: "Mounting directory with CIFS"
date: 2011-08-22
forum: General Help
---

### Post by peterson43 on 2011-08-22
I'm trying to figure out how to correctly mount my laptop running Ubuntu to my home directory at work. After a bit of work, I was able to edit my /etc/fstab file so that the directory mounts. However, I cannot access the directory. 

My /etc/fstab file includes the lines

```

//smbhost.MYWORK.COM/WORK_USERNAME /home/LINUX_USERNAME/WORK_USERNAME cifs credentials=/home/LINUX_USERNAME/.logincredentials,uid=12345,gid=123,dir_mode=0700,file_mode=0700

```

and my .logincredentials contains
```

username=WORK_USERNAME
password=WORK_PASSWORD
domain=WORK_DOMAIN

```

When I mount the directory, the permissions are set so that the owner is 12345 (my uid for my work account) and the group is sambashare. 

I believe the problem might lie in the fact that my LINUX_USERNAME is not the same as my WORK_USERNAME since this same fstab configuration seems to work for other people in my department. I only set up my /etc/fstab file by copying what other people at work had done on their computers, so I really don't know what all the options do. Is there a way to modify my fstab file so that I'll be able to access the directory once it is mounted?

---

### Post by bodhi.zazen on 2011-08-22
You should not use samba over the internet, too insecure.

Use ssh (winscp from windows, sshfs from linux).

---

### Post by allwimb on 2011-08-22
you have to change the uid and gid values put uid=your_username,gid=your_username and that'll work

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by peterson43 on 2011-08-22
I'm not sure if what I'm trying to do is "too insecure" in your opinion or not. I'm using an ethernet connection at my work to mount my work directory. The computers that my work provides aren't as good as my laptop, so I want to use my laptop instead. However, it would be convenient to be able to access the work directory from my laptop. That is why I'm trying to use samba to mount my work directory to my computer. 

Is this still insecure?

---

### Post by peterson43 on 2011-08-22
> **allwimb said:**
> you have to change the uid and gid values put uid=your_username,gid=your_username and that'll work

Ok, that did it. Thanks a lot.

---

### Post by bodhi.zazen on 2011-08-22
> **peterson43 said:**
> I'm not sure if what I'm trying to do is "too insecure" in your opinion or not. I'm using an ethernet connection at my work to mount my work directory.

Well, in that case:

1. Should be "OK" over a LAN.

2. Do you not have an IT department to help ?

---

### Post by peterson43 on 2011-08-25
> **bodhi.zazen said:**
> Well, in that case:

1. Should be "OK" over a LAN.

2. Do you not have an IT department to help ?

Yes, I do have an IT department. However, since I want to maintain my own computer with my own operating system (otherwise I can't add programs that I want to my computer without a huge hassle) they don't give a lot of support. Basically they have enough staff to manage the network, but they don't have enough staff to fix everyones unique problems that come up if they decide to run a different operating system. 

Anyway, thanks for your thoughts.

---

