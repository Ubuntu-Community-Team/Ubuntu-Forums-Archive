---
title: "best setting for usb memory stick?"
date: 2012-09-09
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-09-09
What's the best permission and ownership parameters to use for an ext4 formatted usb memory module.

At this time I can access it in my own user account, but when I go to move some files from my user account to the super users account, it fails. 

If I change the ownership to 'superuser', it works fine in the superusers account, but not in my account and visa versa.

Also, if I want to copy or move any file to or from the usb module, what's the best ownership and permission settings???

TIA

Art

---

### Post by 2F4U on 2012-09-09
In general, user permissions in Linux are divided into Owner, Group and Others. The owner is the account that created the file or folder and usually has read and write permissions. Group is everyone that is in the same group as the user account that created the file. You can set group permissions as you like. Other is everyone except the owner and accounts of the same group.
The superuser naturally can access any file. So, if you want several accounts being able to access the same files, create a new group and assign those group to the accounts you like. 
When you create a file or folder, set group permissions accordingly (read, write, execute).

---

### Post by goodbye-windows(tm) on 2012-09-09
Hi 2F,

I thought about the issue after reading your response last evening. It  appears that I need to create some test files and some test users. Then  I'll have a much better definition of the issue(s).

> So, if you want several accounts being able to access the same files,  create a new group and assign those group to the accounts you like. 

Does this mean I have to edit every single file to make it readable/writable by the third group (others).

It seems like permission for 'others' is what I need to be concerned with.

If I make folders and files with a permission of 6 for the 'others', will that include or exclude the 'owner' and/or the 'group' access???

If I want to take the usb stick to another computer to access the files stored on it, what do I have to do to make sure it's available on the other computer????

TY.

Art

---

