---
title: "folder permissions in a samba share"
date: 2010-03-22
forum: General Help
---

### Post by ozPATT on 2010-03-22
hi all, i have an old desktop that i have decided to use as a central point for localhost/website files. I have 2 laptops, a ubuntu and vista, and i want them both to be able to see the public_html folder on my desktop, and be able to create/update folders and files. 

I have set up the samba sharing and that's working fine, but when i create folders using my laptop, they are not writeable to the desktop or other laptop because my laptop is the creator. 

Is there a way that I can set it so that whenever folders/files are created from either laptop, they have full permissions? 

Thanks

Patrick

---

### Post by mikewhatever on 2010-03-23
Check out /etc/samba/smb.conf, especially the following section:

> # File creation mask is set to 0700 for security reasons. If you want to create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


I suppose uncommenting **create mask = 0700** and changing the value to 0750 should do the trick.

---

### Post by pcjunkie on 2010-03-23
If the desktop is Ubuntu just go floder/properties/share and change the permissions for YOUR user account to read and write. Leave guest as is.

When you log into Samba you log in as you. myusername password = you

The other issue with using a http server is the server is owned by root, not by you. You need to claim that public_html and add it to your account.

desktop$ sudo chown yourname:yourname /public_html/

or something like that.  

All that does is allocates your user account to the user account in root for that particular folder. Now when you log in using windows it will ask for the password, once that is accepted then windows automatically becomes part of that user group. that being you...

Don't change the permissions as root from 644 to 744 or you will screw up the websites. 


I hope that made sense as I am nearly in crash mode..

---

