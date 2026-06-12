---
title: "Grub help"
date: 2010-02-12
forum: General Help
---

### Post by Rhodderz on 2010-02-12
Hi i have Win7 on my lappy and devcided to create a new partition and install Ubuntu9.10
the only problem i have is grub wont show at beginning and when i do get it to show (esc) it does not have any windows options. 
only
ubuntu 9.10
ubuntu 9.10 recovery
memtest
memtest
any help would be appreciated thanks.
(Windows is still installed as i can access the drive in ubuntu)

---

### Post by ChrisB111 on 2010-02-12
I am assuming you have grub 2 installed (standard for ubuntu 9.10). First check if it has fallen of the end of the list, if it hasn't you should be able to boot in to ubuntu and update grub to include your windows partition. Check [here]("https://help.ubuntu.com/community/Grub2") for more info.

Chris

---

### Post by ajgreeny on 2010-02-12
In simplest terms, just boot to ubuntu and run ```
sudo update-grub
``` in terminal.  That should add windows to the menu, and you can then read more about grub from the link given by ChrisB111 and get the menu back by default each boot.

---

### Post by Rhodderz on 2010-02-13
ok i got somewhere i looked around the site and got grub to load and not autoboot.
problem is windows was not there and when i added it using this method ([http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/))
Windows threw me the message that bootmgr is missing. so i need to add bootmgr

---

### Post by Rhodderz on 2010-02-15
okay this is enoying as win7 recov disc cant detect it and when i use the cmd it wont "cd" to my windows partition so i cant to the fix command
plz help as i am not going to reformate

---

