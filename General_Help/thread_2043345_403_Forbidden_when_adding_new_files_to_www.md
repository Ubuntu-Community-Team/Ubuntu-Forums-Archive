---
title: "403 Forbidden when adding new files to www"
date: 2012-08-16
forum: General Help
---

### Post by tylerc66 on 2012-08-16
I am trying to run a intranet on appache for the first time. My issue is that when ever I add a new file to the WWW folder the permissions default too -rw------ . I would like anyone to be able to view the files.  I can change the permissions but I was hoping to default the folder to let new files become readable. Thanks for your help.

---

### Post by spjackson on 2012-08-16
How are you creating the files and copying/moving them to /var/www ? If you are using the terminal, what is your umask?
```

umask

```You might want to change it to 0022.
```

umask 0022

```

---

### Post by tylerc66 on 2012-08-16
Ftping new files into the www directory

---

### Post by rukiaEnix on 2012-08-16
Then change your umask in the FTP configuration

---

### Post by spjackson on 2012-08-16
What ftp client are you using? What is the ftp server? Do both support the umask command? Are you permitted to change the configuration of the ftp server?

---

### Post by tylerc66 on 2012-08-16
> **rukiaenix said:**
> then change your umask in the ftp configuration

yes this worked thanks so much !!!!!!!!!!!

---

### Post by rukiaEnix on 2012-08-16
You're welcome

---

