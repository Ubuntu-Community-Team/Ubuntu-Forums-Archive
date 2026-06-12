---
title: "help with vbox"
date: 2009-10-23
forum: General Help
---

### Post by mattyg_89 on 2009-10-23
hey pplz i have set up a share folder in vbox by going into it pressing settings/shared folders then adding a share folder but i cant actually see it. can any1 help me find it?

---

### Post by flipper9 on 2009-10-23
First, you have to setup the guest additions into the operating system once you have the OS setup.

Next, open up the Networks icon in windows, and browse for Virtualbox.  You should be able to access the files now.  You might even want to map a network drive.

---

### Post by compiledkernel on 2009-10-23
[http://gwos.org/udsf/doku.php/software:virtualbox](http://gwos.org/udsf/doku.php/software:virtualbox)

---

### Post by earthpigg on 2009-10-23
assuming an ubuntu guest:

[http://sites.google.com/site/masonux/home/notes-to-myself#TOC-Setup-vbox-to-share-folders](http://sites.google.com/site/masonux/home/notes-to-myself#TOC-Setup-vbox-to-share-folders)

if that is not the case, can you give us more details on your setup?

---

### Post by mattyg_89 on 2009-10-23
i am running ubuntu 9.04 trying to run windows 7 via vbox. i cant see the share folder in ubuntu

---

### Post by akand074 on 2009-10-23
Open up virtual box, select your windows 7 virtual machine and click settings. The last option should be "Shared Folders", select that. Click on the folder with the + sign on the side (add folder) and you create a new folder. Choose the destination path and name, the folder will be found in Ubuntu wherever you decided the destination is in the last step. Now you can put any files into that folder, and you can access them in windows 7 and vice versa. 

Note: as I saw someone put before, Guest additions must be installed on your guest OS. You can do that by going to "Devices" and then selecting "Install guest additions" in the running OS. After that you can just go to your network places and you'll see a folder called "VBOXSVR(Name of folder you made) on VirtualBox Shared Folder. That is where the folder is in your guest OS, and again, in Ubuntu its wherever you made the destination folder. 

I hope that helped.

---

### Post by mattyg_89 on 2009-10-23
thats the problem though, the folder doesnt come up where i added the folder, i have tried to add it to the desktop and the documents folder and other places but it still wont show up.

---

### Post by mattyg_89 on 2009-10-23
come on pplz help me

---

### Post by flipper9 on 2009-10-23
You need to be clearer about what desktop and folder you are talking about.  Are you referring to the Windows or Linux desktop/folder/share, etc.???

---

### Post by mattyg_89 on 2009-10-23
sorry i mean the ubuntu desktop/share

---

### Post by mattyg_89 on 2009-10-23
thanx, i kno how to do it now

---

### Post by akand074 on 2009-10-23
Sorry I don't believe it gets automatically created. Try this, go to the destination where you want to have a share folder. Right click and select "New Folder". Name the folder whatever you like. Now in virtual box, go to settings -> share folders and click the "add folder" button on the right, choose "other" in destination and a box will pop up. Browse to the folder you just made and double click it and it will open. Now press "Ok" and it should be good to go. Let me know if that worked.

---

### Post by mattyg_89 on 2009-10-23
i did something like that and i right clicked on the folder in ubuntu and went to sharing options and clicked on share this folder. it works fine now

---

