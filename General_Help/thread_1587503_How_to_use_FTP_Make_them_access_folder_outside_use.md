---
title: "How to use FTP? Make them access folder outside users home"
date: 2010-10-03
forum: General Help
---

### Post by ZnoteOT on 2010-10-03
I am using Ubuntu Server. (terminal only). 10.04

I want to run a shared box. But I want the individual persons to only grant access to their own allocated space. 
user1: user1 home dir + /var/www/user1/ folder
user2: user2 home dir + /var/www/user2/ folder
user3: user3 home dir + /var/www/user3/ folder. 

But nothing in between. 

By default, it looks like you only got access to /home/ dir of the user you login with. <--- learned from a lil previous experience. 

On windows it all seems so easy, download filezilla server, add user & pass, add witch dir he got access to. And done.

Please help me out. :) Witch FTP _server_ program is suited? I tested vsftp last time, and it looks like i couldn't add users, they used same username as the comp has. I don't like that. D: I like to add specific FTP users, etc "user1www" "user1storage" allocating them to different dirs outside any particular home dir.

---

### Post by spiky001 on 2010-10-03
You can get filezilla on ubuntu look in synaptic manager

---

### Post by ZnoteOT on 2010-10-03
I am looking for FTP **server**. I heard there does not exist any filezilla _Server_ for Linux. :O

---

### Post by drdos2006 on 2010-10-03
Check this out.

[http://ubuntuforums.org/search.php?searchid=76344712](http://ubuntuforums.org/search.php?searchid=76344712)

regards

---

### Post by ZnoteOT on 2010-10-04
> **drdos2006 said:**
> Check this out.

[http://ubuntuforums.org/search.php?searchid=76344712](http://ubuntuforums.org/search.php?searchid=76344712)

regards

Hmm, this is what I got to when clicking that link:
[quote=Results]
vBulletin Message
Sorry - no matches. Please try some different terms.[/quote]

---

### Post by Wtower on 2010-10-04
Check vsftpd. Site is [http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)

Regards

---

### Post by t0p on 2010-10-04
If you install the OpenSSH server

```
sudo apt-get install sshd
```

on your server, users will then be able to access the server via sftp.

---

