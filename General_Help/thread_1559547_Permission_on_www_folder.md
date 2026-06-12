---
title: "Permission on www folder"
date: 2010-08-23
forum: General Help
---

### Post by micha8l on 2010-08-23
Hello, my question is about the permission on the www Apache directory, as I'm completely new to Ubuntu/Linux. The problem is I'm having trouble editing files within the directory, although i can view them. Must I use the sudo command in some way to edit the files and what's the easiest way to do this please?

Kind Regards

---

### Post by triunenature on 2010-08-23
> **micha8l said:**
> Hello, my question is about the permission on the www Apache directory, as I'm completely new to Ubuntu/Linux. The problem is I'm having trouble editing files within the directory, although i can view them. Must I use the sudo command in some way to edit the files and what's the easiest way to do this please?

Kind Regards

```

cd /path/to/www
sudo chmod -R 777 *

```


What that does, is it gives anyone permission, to read write execute all files within www.

You should be able to edit to your hearts content

Be SUPER careful.  Do NOT do this on your root directory, or you will be crying. Only do it when you are actually in your www directory.

When you get a chance, check out: [https://wiki.ubuntu.com/FilePermissions](https://wiki.ubuntu.com/FilePermissions)

---

### Post by lmarmisa on 2010-08-23
I suppose that the www folder is located in the /var directory of your Ubuntu system.

I like to have the www files within my home folder. If you wish a similar solution, follow the next steps. 

Open a terminal and type these commands:

> 
sudo etc/init.d/apache2 stop
cd
mkdir www
cp -r /var/www/. www/
sudo mv /var/www /var/www.old
sudo ln -s $HOME/www /var/www
sudo etc/init.d/apache2 start
The new directory for www will be $HOME/www where you have full CRMD (create-read-modify-delete) privileges.

Kind regards,

Luis

---

