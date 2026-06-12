---
title: "Windows to Linux"
date: 2006-04-08
forum: General Help
---

### Post by Fatstink on 2006-04-08
I have accessed a windows box on my network, however it asks me for username and password.  I put them in, correctly, and it denies me access.  How do I get my files of a windows box???

---

### Post by Dianoga on 2006-04-08
You may have a domain setup. If that is the case, your username would be domain\user

---

### Post by TransitMan on 2006-04-08
[QUOTE=Fatstink]I have accessed a windows box on my network, however it asks me for username and password.  I put them in, correctly, and it denies me access.  How do I get my files of a windows box???[/QUOTE]

Make sure you have "Sharing" enabled on the Windows box for whatever drive and or folder/file you are trying to access. Also, when enabling "Sharing", make sure you specify if a password is required to access those drives or file/folders.
If so, as mine are, use your user name and the password you assign the "Share" is what is needed.
Also make sure you have mounted the drive correctly for READ/Write access if FAT32 or READ access only for NTFS from your Linux OS.
I learned this through trial and error, as well as reading reading posts here.

---

### Post by adamkane on 2006-04-08
The method that works in most cases is:

Places -> Connect to Server

Select Windows Share, then enter the IP address of the Windows machine you want to connect to. Enter Share name, User name and Password.

You sometimes get connection problems depending on how Windows networking is set up, so try this method first. If this method works, then you can try other methods.

---

### Post by N8MAN1068 on 2006-04-10
I have that happen sometimes on my win2k adv. server box as well.
Sometimes I'll click 'cancel' after the 3rd try, and it'll let me in. ](*,) 

When I get the time, i plan to remove win2k server and install Ubuntu on that box as well. :mrgreen:

---

### Post by vavoem on 2006-04-11
Do you have an advanced password on your windows box?

Windows expects that from you.
It should not be the same as your username and have at least one special character like an nummeric or something also there should at least be one capital letter.

Hope this helps

---

