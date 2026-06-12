---
title: "Owner of all folders is &quot;root&quot;. How to change this?"
date: 2006-02-06
forum: General Help
---

### Post by globemast on 2006-02-06
Hello,

i have just installed Ubuntu and for all the folders and files the owner is root. How can i change this for all of them, so as the owner will be me?

And additionally i cannot see the NTFS partition of my disk (hda1). It says that the owner is root. When i login as root i can open the file and if i try to change the owner is reports that the disk is Read Only. How can i change this??

Thank you in advance.

---

### Post by kaamos on 2006-02-06
It should be root except for the files under /home/username. If those are root as well, it can be fixed with
```
sudo chown username:username /home/username -R
```

ntfs -> [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by aysiu on 2006-02-06
Changing the ownership of all your system folders is **a really bad idea**.

Instead, read the third and fourth links of my signature.

---

### Post by garba on 2006-02-06
[QUOTE=globemast]Hello,

i have just installed Ubuntu and for all the folders and files the owner is root. How can i change this for all of them, so as the owner will be me?

Thank you in advance.[/QUOTE]

welcome to unix mate, enjoy your stay

this is the way it's supposed to work and the reason behind it is everything but silly as it might seem to be, just take my word for it 
;)

---

### Post by leo83 on 2008-05-19
> **aysiu said:**
> Changing the ownership of all your system folders is **a really bad idea**.

Instead, read the third and fourth links of my signature.
I want to change the Owner for one of my folders(presently :root) , so that i will be owner and also group name =abc, which i want to also change it..

I couldnt find anything in your signature..could you please post the links 

Thanks

---

