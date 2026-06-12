---
title: "pen drive write protected"
date: 2011-07-23
forum: General Help
---

### Post by rahulbest on 2011-07-23
i want to make pen drive as write protected for ubuntu and windows.....how to do that???
and if i want to write on it then how to make remove write protection....
help me out....

---

### Post by Herman on 2011-07-23
UbuntuSolutions- [How To Create an Encrypt USB Drive]("http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html")

---

### Post by rahulbest on 2011-07-23
but i cant install anything on windows machine....because i dont have printer at my place so i have to go out for print outs...so there is anything u can suggest?

---

### Post by Herman on 2011-07-23
Okay, I think I might have another idea. 
What if you made your directory full of files and then when it's finished, run a genisoimage command on it to turn it into an .iso. 
An .iso file would be read-only.

It would be easy to mount in Ubuntu to read it but I don't know how you mount an .iso in Windows. Maybe there's a program you can buy for that? 

When you want to write to it you need to copy it all into a folder again and make your desired changes and run genisoimage to create a new .iso.                                

Would that idea be any good to you?

---

### Post by fdrake on 2011-07-23
for windows there is a free iso-mounter program: Daemon tools lite
[link to download]("http://disc-tools.com/request?p=93cdade08108b264e61b8edb3d781e9b/DTLite4402-0131.exe")

---

### Post by fdrake on 2011-07-23
> **Herman said:**
> Okay, I think I might have another idea. 
What if you made your directory full of files and then when it's finished, run a genisoimage command on it to turn it into an .iso. 
An .iso file would be read-only.

It would be easy to mount in Ubuntu to read it but I don't know how you mount an .iso in Windows. Maybe there's a program you can buy for that? 

When you want to write to it you need to copy it all into a folder again and make your desired changes and run genisoimage to create a new .iso.                                

Would that idea be any good to you?

i don't get it even if you can convert it into an iso you can still delete the iso file, not? so how is supposed to be write protected?

---

