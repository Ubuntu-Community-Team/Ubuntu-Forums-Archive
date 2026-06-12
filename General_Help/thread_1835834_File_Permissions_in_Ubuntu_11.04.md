---
title: "File Permissions in Ubuntu 11.04"
date: 2011-08-30
forum: General Help
---

### Post by itsmewindxx on 2011-08-30
Good day! 

I just wanna ask, how can i change the file permission of my back up drive?

when i go to the file permissions tab-group panel, it doesn't work even though I replaced it with administrators/admin. i cannot even change the folder and file access of the group. only the owner (itsmewindxx) can access this drive.

what should i do?

thanks in advance for the reply. sorry for my bad english.

---

### Post by raja.genupula on 2011-08-30
```
sudo chmod 777 File/folder
``` 

gives complete access to all members who are using that system.


for more reference you should have a look at this 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by wyzarddoc on 2011-09-15
I just do it the easyway!! install pysdm from their website and then you can successfully change attributes for all the drives. On the website download the version to match your ubuntu install. If you are unfamiliar with the different file permissions just search the ubuntu website for setting file permissions. I always have to search since I don't change them that often. Also if your having trouble using a usb flash drive use the pysdm program to change the attributes from 277 to 777 so you can read and write. After you install pysdm - start the program then install your usb-flash drive. Click on the black triangle next to the flash drive then click on the partition. It will say " not configured" next click on Set defaults then Assistant. When the window opens find the file and folder permissions set them to the desired 777 from 277 apply then close.
enjoy
Doc

---

