---
title: "SAMBA config missing"
date: 2011-10-17
forum: General Help
---

### Post by xioSlayer on 2011-10-17
Ok I installed samba with
```
sudo apt-get install samba
```

I then played with the settings for about an hour trying to make security enabled shares work.

After no luck with that I decided I would go back to non-secured sharing, which isn't what I want but at least it worked.

So I then used 
```
sudo apt-get purge samba
```

and I deleted my /etc/samba directory to remove the configuration files.

When I went to reinstall samba I noticed it would not recreate the samba directory.

What do I do now?  Is there a special command to make 'install' rebuild the config directory?

Thanks.

---

### Post by Morbius1 on 2011-10-17
smb.conf doesn't come from the "samba" package it comes from the "samba-common" package.

---

### Post by collisionystm on 2011-10-17
Read this

[https://help.ubuntu.com/11.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/11.04/serverguide/C/windows-networking.html)

You have to add a samba user to use them in security enabled shares.

Must be an existing user.

Open terminal

sudo smbpasswd -a username

---

### Post by xioSlayer on 2011-10-17
thank you, that solved it.

---

