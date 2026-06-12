---
title: "Folder Permissions :: Access denied for user 'www-data'@'localhost'"
date: 2009-08-08
forum: General Help
---

### Post by own3mall on 2009-08-08
So, I'm trying to give a folder within var/www/GamePanelX full permissions so that anyone can access the folder via [http://IP.address/GamePanelX](http://IP.address/GamePanelX)  

I've tried:

```

eric@eric-desktop:~$ sudo -i
[sudo] password for eric: 
root@eric-desktop:~# chmod a+rwx /var/www/GamePanelX
root@eric-desktop:~# chmod a+rwx /var/www/GamePanelX
root@eric-desktop:~# sudo nautilus
root@eric-desktop:~# chmod 777 /var/www/GamePanelX
root@eric-desktop:~# 

```So, that didn't work, as it returns the following message when I try to access it via localhost through Firefox:

```

Access denied for user 'www-data'@'localhost' (using password: NO)

```I also tried editing the permissions using the gui by typing in sudo nautilus.

I write-clicked on the folder, went to the Permissions tab, and set the following:

```

Owner:                www-data
Folder Access:      Create and Delete Files
File Access:          Read and Write

Group:                 www-data
Folder Access:      Create and Delete Files
File Access:          Read and Write

Others:
Folder Access:      Create and Delete Files
File Access:          Read and Write

Execute:  YES

```I then clicked on Apply Permissions to Enclosed Files.  Tried accessing it again at [http://localhost/GamePanelX](http://localhost/GamePanelX)

Didn't work.

How is anyone supposed to access this folder?

---

### Post by cpetercarter on 2009-08-08
Are you working on the right folder? You say you want users to access a folder *within* /var/www/GamePanelX. I guess you mean a subdirectory of /var/www/GamePanelX. But you have changed the permissions in /var/www/GamePanelX, not the sub-directory.

---

### Post by mthalis on 2009-08-08
try this
**sudo chown -R <username>:www-data  /var/www/GamePanelX **

---

### Post by garikaib on 2009-08-08
Try chmod -R /var/www/GamePanelX

---

### Post by garikaib on 2009-08-08
Try -R 777 /var/www/GamePanelX

---

### Post by sub_acoustic on 2010-08-22
ok...so just a little bit more info as this page helped me, but I was symlinking from /var/www/ to /home/username/public_html
changing the permissions as suggested in this thread didn't work, because of the symlink, I had to change the permission in the folder that was linked to i.e.

```
sudo chown -R www-data:www-data /home/USERNAME/public_html
[sudo] password for USERNAME: 
hamish@machine:~$ sudo chmod -R 755 /home/USERNAME/public_html
```

and then it worked fine

---

