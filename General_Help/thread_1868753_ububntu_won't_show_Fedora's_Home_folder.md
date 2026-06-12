---
title: "ububntu won't show Fedora's Home folder"
date: 2011-10-24
forum: General Help
---

### Post by olysseusjourney on 2011-10-24
Hi 
Today, I switched from Fedora 15 to Ubuntu 11.10. through the installing progress, i shared fedora's home partition with ubuntu, but now after installing, i can not use my fedora's home folder. i do not need fedora any more, but i really need my files on fedora's home folder.
sorry for my bad language.
and plz help me.

---

### Post by mikejonesey on 2011-10-24
ensure all partitions are mounted and search for a file?

---

### Post by AlphaLexman on 2011-10-24
It has been a while (1+ yr) since I did a new install of either Ubuntu or Fedora

[COLOR="black"]**IMPORTANT**[/COLOR]: Did you enable encryption on the Fedora install ??

But if my memory serves me well, the default Fedora encryption secures the **entire** '/home' directory for **every** user! Whereas Ubuntu just encrypts the **user's** directory ('/home/username)' or just the **Private** directory (~/Private)'

If you did use encryption, you will probably have to use a live Fedora disc to recover the files, as Red Hat (Fedora) and Debian (Ubuntu) use different encryption programs / methods.

---

### Post by dcstar on 2011-10-25
> **AlphaLexman said:**
> It has been a while (1+ yr) since I did a new install of either Ubuntu or Fedora

[COLOR="black"]**IMPORTANT**[/COLOR]: Did you enable encryption on the Fedora install ??

But if my memory serves me well, the default Fedora encryption secures the **entire** '/home' directory for **every** user! Whereas Ubuntu just encrypts the **user's** directory ('/home/username)' or just the **Private** directory (~/Private)'

If you did use encryption, you will probably have to use a live Fedora disc to recover the files, as Red Hat (Fedora) and Debian (Ubuntu) use different encryption programs / methods.

As well the UIDs (User IDs) of the various accounts will have to match up if your are not using sudo rights to try and access the folders. Ubuntu's default account UID is 1000, I don't know what Fedora uses.

---

### Post by decrepit on 2011-10-25
I've no problem accessing my fedora 12 files from ubuntu 10.4.

I have the old fedora partition mounted through /etc/fstab.

---

### Post by fantab on 2011-10-25
> **olysseusjourney said:**
> Hi 
Today, I switched from Fedora 15 to Ubuntu 11.10. through the installing progress, i shared fedora's home partition with ubuntu, but now after installing, i can not use my fedora's home folder. i do not need fedora any more, but i really need my files on fedora's home folder.
sorry for my bad language.
and plz help me.

> **dcstar said:**
> As well the UIDs (User IDs) of the various accounts will have to match up if your are not using sudo rights to try and access the folders. Ubuntu's default account UID is 1000, I don't know what Fedora uses.

Common Sense would dictate that you do a back up for the important files that you do not wish to lose. 

Yes there is UID issue between Ubuntu and Fedora 15, upto Fedora15 UID=500... they adopted UID=1000 in Fedora16. I suggest you try changing the permissions of the Fedora Home folder.

You can try this:


[LIST]
[*] **Alt+F2** and type *gksu nautilus*
[*] Right click on the Fedora Home Folder and select **Properties**
[*] Try to **change the Permissions** in your favor.
[/LIST]
 
If the above does not help... then **boot with Fedora15 live CD and access the Folder in Question**... and BACK UP your Data.

---

