---
title: "Downloaded .docs are read-only"
date: 2011-02-09
forum: General Help
---

### Post by CommuneOfLoon on 2011-02-09
Whenever I download a .doc file I send to myself and open it in OpenOffice via Ubuntu 10.04, it opens as a read-only that I "do not have the rights" to alter. This is obnoxious, because then I have to copy and paste the entire thing, which can lead to format issues, before I can continue to work on the document. Any ideas what the issue is or how I can fix this? Thanks.

---

### Post by wojox on 2011-02-09
Can you right click the file and configure the permissions?

---

### Post by Old *ix Geek on 2011-02-09
> **CommuneOfLoon said:**
> Whenever I download a .doc file I send to myself and open it in OpenOffice via Ubuntu 10.04, it opens as a read-only that I "do not have the rights" to alter.Where are you downloading the files? What permissions are set on this directory?
> This is obnoxious, because then I have to copy and paste the entire thingNo you don't. Your lack of understanding of what's happening doesn't make it obnoxious! If you're downloading the file(s) into a directory with proper permissions, you'll be able to do whatever you want to them. If you're NOT putting them in a directory with proper permissions, you should be.
> Any ideas what the issue is or how I can fix this?Yes, download into a directory that gives you the appropriate permissions. If you don't know how to do this, post again!

---

### Post by matt_symes on 2011-02-09
Hi

It's only a small learning curve. You would have had the same one under windows. Linux was built with safety from the start using permissions.

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

All the operations in that link can be performed through the file browser.

In the file browser (Nautilus), right click on the file or folder and select properties. Select the permissions tab and change the permissions there.

When you understand what is going on you will be glad of permissions.

Kind regards

---

### Post by CommuneOfLoon on 2011-02-09
Okay, thank you. 

I knew about changing permissions, but when I tried to save the file to access "properties" I got this message:    

    Error saving the document *****:
    Object not accesible
    The object cannot be accessed
    due to insufficient user rights.

Then I realized I was just opening the file when I downloaded; I guess I need to "save file" when I download it.

---

