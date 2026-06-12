---
title: "Copy data from ubuntu to virtual box"
date: 2011-02-17
forum: General Help
---

### Post by karimkhan on 2011-02-17
Hi frnds..
I want to copy data from my ubuntu 10.04 to Virtual box , which is Windows XP .....
How can I do it ?

---

### Post by rvchari on 2011-02-17
have you set up shared folder in virtual box ? if not then in the virtual box window, you will find an option for shared folders. add the folders you want to access from vbox. but first you should have installed guest additions. if u didnt then with xp booted, choose from the top menu and install guest additions. then shut down xp and do the shared folder addition.

another pre-check, see that the folders you want to be accessed has the permissions for sharing and accessing with read/write permissions. if not then give permissions by right clicking on the properties.

to access from vbox, you have to go to network places and you ll find vboxsrv or something like that. click on that and ur shared folders should be visible for you to access.

this way you can access ubuntu host folders from vbox.
another way is to add network with host only options... but thats another way of accessing, the first options should work.

---

### Post by coldraven on 2011-02-17
In Ubuntu I have the folder /home/your_user_name/Share_to_VM
In my virtual XP I have the folder \\Vboxsvr\Share_to_UB
You set that up in VBox>Devices>Shared Folders
I have a link on the XP desktop to quickly access it.
I can move files between Ubuntu and XP as it's seen as the same folder.
It took a while for me to work it out but actually it is very easy.

---

### Post by t0p on 2011-02-17
Here are a couple of links relating to copying and sharing files between VBox host and guest: [[link 1]]("http://ubuntuforums.org/showthread.php?t=602241") [[link 2]]("http://ubuntuforums.org/archive/index.php/t-1052016.html").  They helped me sort it out.

---

