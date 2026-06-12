---
title: "You do not have the permissions necessary to view the contents of &quot;&quot;."
date: 2010-06-01
forum: General Help
---

### Post by Harout tuoraH on 2010-06-01
Hello, I am having problems accessing my files which I have stored on a backup partition. Here is the story. I had the latest version of Ubuntu installed 10.04, and it was giving me problems so I decided to downgrade to 9.10. Before doing a clean install of 9.10 I moved all of my files onto a backup partition I have which is ext3 type. After doing the clean install, some files in the backup drive have become inaccessible, while some of them still are. For example, I would open up the Pictures folder in the backup partition, I can open the folder named "fun" and view all of its contents, but I cannot open the folder named "Chelan 2009". There seems to be no apparent reason why one folder is allowed to be opened over the other. The folders which I cannot access have an X at the top right of the icon. When I try to open one of these folders I get the message "You do not have the permissions necessary to view the contents of ""." I tried using ```
sudo cp -r
``` to copy the files onto my linux partition, but with no success. The folder gets copied, but still has an X on the icon, and is still inaccessible. 

Any ideas on how to solve this would be great! I have many important files which I cannot access right now so please, any input is good.

---

### Post by Vishal Agarwal on 2010-06-01
what is the output of ls -al ?

---

### Post by Harout tuoraH on 2010-06-01
total 264
drwxr-xr-x 32 harout harout  4096 2010-05-31 22:42 .
drwxr-xr-x  3 root   root    4096 2010-05-31 21:35 ..
drwx------  3 harout harout  4096 2010-05-31 21:50 .adobe
-rw-------  1 harout harout    83 2010-05-31 22:24 .bash_history
-rw-r--r--  1 harout harout   220 2010-05-31 21:35 .bash_logout
-rw-r--r--  1 harout harout  3180 2010-05-31 21:35 .bashrc
drwx------  4 harout harout  4096 2010-05-31 22:44 .cache
drwxr-xr-x  6 harout harout  4096 2010-05-31 22:42 .config
drwx------  3 harout harout  4096 2010-05-31 21:42 .dbus
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 Desktop
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 Documents
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:43 Downloads
-rw-------  1 harout harout    16 2010-05-31 21:42 .esd_auth
-rw-r--r--  1 harout harout   167 2010-05-31 21:35 examples.desktop
drwx------  4 harout harout  4096 2010-05-31 21:47 .gconf
drwx------  2 harout harout  4096 2010-05-31 22:44 .gconfd
-rw-r-----  1 harout harout     0 2010-05-31 22:25 .gksu.lock
drwx------  6 harout harout  4096 2010-05-31 21:42 .gnome2
drwx------  2 harout harout  4096 2010-05-31 21:42 .gnome2_private
drwx------  2 harout harout  4096 2010-05-31 21:42 .gnupg
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 .gstreamer-0.10
-rw-r--r--  1 harout harout   142 2010-05-31 21:42 .gtk-bookmarks
dr-x------  2 harout harout     0 2010-05-31 21:42 .gvfs
-rw-------  1 harout harout   350 2010-05-31 21:42 .ICEauthority
drwxr-xr-x  3 harout harout  4096 2010-05-31 21:46 .kde
drwx------  3 harout harout  4096 2010-05-31 21:43 .local
drwx------  3 harout harout  4096 2010-05-31 21:50 .macromedia
drwx------  4 harout harout  4096 2010-05-31 21:43 .mozilla
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 Music
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 .nautilus
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 Pictures
drwx------  3 harout harout  4096 2010-05-31 21:46 .pki
-rw-r--r--  1 harout harout   675 2010-05-31 21:35 .profile
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 Public
drwx------  2 harout harout  4096 2010-05-31 21:42 .pulse
-rw-------  1 harout harout   256 2010-05-31 21:42 .pulse-cookie
-rw-------  1 harout harout  1315 2010-05-31 22:42 .recently-used.xbel
drwx------  2 harout harout  4096 2010-05-31 21:42 .ssh
-rw-r--r--  1 harout harout     0 2010-05-31 21:44 .sudo_as_admin_successful
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:42 Templates
drwx------  4 harout harout  4096 2010-05-31 22:27 .thumbnails
drwxr-xr-x  2 harout harout  4096 2010-05-31 21:44 .update-manager-core
drwx------  2 harout harout  4096 2010-05-31 21:42 .update-notifier
drwxr-xr-x  3 harout harout  4096 2010-05-31 22:20 Videos
-rw-------  1 harout harout 96530 2010-05-31 22:44 .xsession-errors

---

### Post by xfearxnxloathing on 2010-06-01
its like you dont have root access to all files or folders on the backup drive.  im looking for an answer..

---

### Post by Vishal Agarwal on 2010-06-01
As a user harout are you able to access all the files. Because all the files are having the "group:owner" as harout.

If you can then login as harout (also can be [su - harout]) and then try to copy the files.

---

### Post by xfearxnxloathing on 2010-06-01
read something about repairing permissions using disk utility and are the "x'd" folders write protected???

---

### Post by Harout tuoraH on 2010-06-01
I am logged in as harout. I restarted my computer and logged in as harout to be sure. 

And about repairing permisisons using disk utility, all I could find was mac stuff. And what do you mean "write protected"? I am not sure, but under properties the contents says "unreadable" and it cannot tell me how much big the folder is. Also, on the file I tried to copy to my linux partition using sudo cp -r, there is not only an x on the icon, but also a lock above the x. Don't know if that helps much.

---

### Post by xfearxnxloathing on 2010-06-01
> **Harout tuoraH said:**
> I am logged in as harout. I restarted my computer and logged in as harout to be sure. 

And about repairing permisisons using disk utility, all I could find was mac stuff. And what do you mean "write protected"? I am not sure, but under properties the contents says "unreadable" and it cannot tell me how much big the folder is. Also, on the file I tried to copy to my linux partition using sudo cp -r, there is not only an x on the icon, but also a lock above the x. Don't know if that helps much.

just because you can login as harout doesnt mean you are administrator.  by default you are not administrator.  go to, System>Administration>Users & Groups, click yourself (probably the only user avail) and look at Account type.  if not administrator, click change.  let me read up on the other stuff but try whats been said.

---

### Post by Harout tuoraH on 2010-06-01
Additional info:

My backup partition was empty before I moved all of my folders except for one folder called "lost+found". I did not make this folder, it was always there. This folder also has an x on the icon and does not let me view the contents although I am not sure what could be in there.

When I moved my files into the backup partition I had to use sudo cp -r because it would not let me drag and drop.

---

### Post by Harout tuoraH on 2010-06-01
> **xfearxnxloathing said:**
> just because you can login as harout doesnt mean you are administrator.  by default you are not administrator.  go to, System>Administration>Users & Groups, click yourself (probably the only user avail) and look at Account type.  if not administrator, click change.  let me read up on the other stuff but try whats been said.

In Users & Groups, there are two users, myself and root. Root cannot be managed at all, it is dimmed out. When I click on harout I can go to properties, and cannot change anything but my "real name", "contact info" and password. It does not tell me the account type anywhere that I can access.

---

### Post by xfearxnxloathing on 2010-06-01
you were right about the disk utility not being able to fix permissions.  

try reading this, mainly the second page but if you need navigation help read some of the first page.  
[http://www.associatedcontent.com/article/1588637/changing_permissions_of_locked_folders.html?cat=59](http://www.associatedcontent.com/article/1588637/changing_permissions_of_locked_folders.html?cat=59)

---

### Post by xfearxnxloathing on 2010-06-01
> **Harout tuoraH said:**
> In Users & Groups, there are two users, myself and root. Root cannot be managed at all, it is dimmed out. When I click on harout I can go to properties, and cannot change anything but my "real name", "contact info" and password. It does not tell me the account type anywhere that I can access.

it appears to me that you are not administrator.  as this may be your problem i do not know how to help you any further as i am not knowledgeable enough in that area.  can someone please help this guy further.

---

### Post by Vishal Agarwal on 2010-06-01
your ls output says that harout has all the ownership of the files.  the group is harout and owner is also harout; that's why i suggested to copy your files as harout. did you try that ?

---

### Post by Harout tuoraH on 2010-06-01
> **xfearxnxloathing said:**
> you were right about the disk utility not being able to fix permissions.  

try reading this, mainly the second page but if you need navigation help read some of the first page.  
[http://www.associatedcontent.com/article/1588637/changing_permissions_of_locked_folders.html?cat=59](http://www.associatedcontent.com/article/1588637/changing_permissions_of_locked_folders.html?cat=59)

Beautiful! Thank you!! I cannot access the folders in backup, but I can copy them to my linux partition and then unlock them with what that website says. Thank you! And thanks to every one else who helped to!

---

### Post by Harout tuoraH on 2010-06-01
> **Vishal Agarwal said:**
> your ls output says that harout has all the ownership of the files.  the group is harout and owner is also harout; that's why i suggested to copy your files as harout. did you try that ?

Yes like I said I can copy them but they are locked even after copying, but its all good now that I can unlock them. Great thanks!

---

