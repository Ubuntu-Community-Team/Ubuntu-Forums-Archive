---
title: "Ftp server"
date: 2009-10-16
forum: General Help
---

### Post by BILLSITO on 2009-10-16
I can!t modify vsftpd.conf file.
Say "It doesn!t have permission to save a file"

---

### Post by KlinerDraken on 2009-10-16
did you open it as root?

```
gksu gedit /etc/vsftpd.conf
```

---

### Post by ackley on 2009-10-16
You need to be root to save it. If you're opening the file like this ```
gedit /etc/vsftpd.conf
``` you'll get that error.

However, if you do this:
```
sudo gedit /etc/vsftpd.conf
```You'll be able to save your file with no problem.

Or do what [KlinerDraken]("http://ubuntuforums.org/member.php?u=608185") said. :D

---

### Post by oldos2er on 2009-10-16
You need to have admin privileges to edit system files, e.g. ```
sudo nano /etc/foo.conf
```
If you're running gedit in Gnome, use ```
gksu gedit /etc/foo.conf
```

---

