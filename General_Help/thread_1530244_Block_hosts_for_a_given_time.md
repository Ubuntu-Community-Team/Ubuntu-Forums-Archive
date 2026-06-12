---
title: "Block hosts for a given time"
date: 2010-07-13
forum: General Help
---

### Post by vikram_v1990 on 2010-07-13
Hello,

Is there anyway that I can prevent access to the hosts file, or any file for that matter, for a time that I can specify, so that within that time no one will be able to open and edit the said file?

---

### Post by dcstar on 2010-07-14
> **vikram_v1990 said:**
> Hello,

Is there anyway that I can prevent access to the hosts file, or any file for that matter, for a time that I can specify, so that within that time no one will be able to open and edit the said file?

You are free to write scripts to change the permissions of files and then schedule them.

---

### Post by vikram_v1990 on 2010-07-14
But can't you use sudo to overwrite them even if we don't have permissions? Even I should not be able to change them during that time. Thanks in advance.

---

### Post by K.J. on 2010-07-14
> **vikram_v1990 said:**
> But can't you use sudo to overwrite them even if we don't have permissions? Even I should not be able to change them during that time. Thanks in advance.

I'm not sure I follow. If a user has root access, they have the keys to the kingdom (in the words of my former OS professor) and you can't stop them from doing anything.

I think what you want is a simple script to chmod/chown the file and set it up to run at specific times with crontab.

---

### Post by vikram_v1990 on 2010-07-15
Thanks a lot for your help. I don't get just one part, if we can use sudo then what is the point of root/su. We can do anything with sudo right? Can you tell me some place where I can get this doubt clarified? Thanks again

---

