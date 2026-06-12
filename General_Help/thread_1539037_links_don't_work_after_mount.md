---
title: "links don't work after mount"
date: 2010-07-26
forum: General Help
---

### Post by davidbr on 2010-07-26
Hello,

I work in a lab when all the guys use PCs with Windows and access the lab linux servers via ssh.

I prefer linux, so I have a local installation of ubuntu 10.4 on my PC. I mount the home of our lab server using mount server:/home /mnt/home/. I can then access the files on the server (I had to change my local UID to match the one assigned to me on our server in order to be able to write to my home dir).

The problem is all the (symbolic) links I have on the server don't work when I access them through the mounted location. I guess the system simply tries following the link in my local /home instead on server:/home.

Is there a way to make the links work?

Thanks,
Dave

---

### Post by lmarmisa on 2010-07-26
Try to use Samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by prodigy_ on 2010-07-26
Could you please explain the issue more clearly? Perhaps, you can provide an example of a link that stops working? What error messages do you receive when you try to follow this "broken" link? What is the output of **sudo mount** command?

---

### Post by davidbr on 2010-07-26
An example for a symbolic link:

server side: lrwxrwxrwx 1 dave ldap users 43 Jul 25 14:31 code -> /home/dave/workspace/proj1/code/ (in green) client side: lrwxrwxrwx 1 dave dave-users 43 Jul 25 14:31 code -> /home/dave/workspace/proj1/code/ (in blue)

the link does not work on the client side, I guess it just looks for /home/dave/workspace/proj1/code/ in the local home, not on the mounted home (/mnt/home/dave...).

---

### Post by prodigy_ on 2010-07-26
Your guess is correct. Unfortunately I don't see any easy workaround short of changing the mount point from **/mnt/home** to **/home**. Obviously this way you won't be able to access your local profile. And I'm not even completely sure this will work because I haven't tried this myself.

---

