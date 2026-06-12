---
title: "Samba says that its install but none of the files are there and can't start service"
date: 2010-07-26
forum: General Help
---

### Post by KLStringer on 2010-07-26
I've been trying to install samba the last couple days, every time I do apt-get install samba it says that its the latest version but there's no samba folder in /etc/ and when I try /etc/init.d/samba start (or stop or restart) I get no such file or directory errors.

I've tried apt-get --purge remove samba to remove it and then reinstall but it does nothing and after the reinstall I'm still left with the above problem.

Please help I've never had this happen before and I need to get this working A.S.A.P.

---

### Post by CharlesA on 2010-07-26
Samba should be installed in /etc/samba

It has also been converted to an upstart job in the latest versions of Ubuntu.

What version are you using?

Try this:

```
locate smb.conf
```

```
sudo service smbd start
```

---

### Post by KLStringer on 2010-07-26
Thank you for the help, I think I've got it reinstall and working. I brought up aptitude and went through the list till I had removed everything, then I did a reinstall and now I have the samba folder in /etc.

Now if I could get the shared drive to mount I might just be able to start coping everything over.

---

