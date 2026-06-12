---
title: "Permissions issue"
date: 2011-02-07
forum: General Help
---

### Post by patberning on 2011-02-07
Hello,
I've been trying for some time to install Wordpress locally on my IBM Thinkpad T42 with Ubuntu 10.10. I finally managed to install LAMP and now I'm stuck because:

1. When I try to transfer the uncompressed Tar.gz Wordpress folder in the /var/www/ folder I'm told I don't have the permission to do so.

2. A result of previous failed attempts is that 2 folders are left in the /www/ folder which have broken links but refuse to be trashed also because of the permission issue. A right-click on these folders reveals no information on the permissions.

3. To further complicate my efforts, when I try to remove the folders in Terminal I get either the "no permission" notice or one saying "no such file or directory" and yet I can see it there.

I hope somebody out there can lend me hand.

Thanks.

---

### Post by mikewhatever on 2011-02-07
Modifying files and folders outside your home dir requires admin privileges, so if you use the file browser to copy, launch it with admin privileges with the **gksudo nautilus** command and copy away. If you use the terminal, use **sudo cp -r folder-name /var/www/**

---

### Post by patberning on 2011-02-08
Thanks Mikewhatever,
The gksudo helped to trash the broken file and copy the new one.
Now let's see if I can continue the installation.

---

