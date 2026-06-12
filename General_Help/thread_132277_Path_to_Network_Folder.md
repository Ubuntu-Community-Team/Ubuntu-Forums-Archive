---
title: "Path to Network Folder"
date: 2006-02-18
forum: General Help
---

### Post by anandrd on 2006-02-18
I connected to a remote server via SSH and I get an icon on my desktop, which takes me to the contents of that server. Can anybody tell me how can I access these contents via command line?

Some applications (for example Kile) cannot see this network connection while some (like OpenOffice) can. Any idea about why this is so?

---

### Post by cronholio on 2006-02-18
> Can anybody tell me how can I access these contents via command line?

```
sftp username@hostname
```

Enter password. You should now see a CLI similar to ftp.

---

### Post by anandrd on 2006-02-18
The main problem is making Kile and other KDE apps see this network folder. How to do it?

---

### Post by SWAT on 2006-02-18
You shouldn't be able to access it from elsewhere since it is NOT mounted. [You should give SSHFS a try](http://www.zwhlug.nl/content/sshfs_howto_use_the_ssh_filesystem), but use it with caution. I only use it for a few minutes (as long as I need it) and then disconnect the mount :D

---

