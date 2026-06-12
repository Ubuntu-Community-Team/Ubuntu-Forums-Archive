---
title: "Installing 'Google Earth for Linux'"
date: 2010-04-20
forum: General Help
---

### Post by brujo32 on 2010-04-20
I downloaded  'google earth for linux', and now  I have a .bin file that won't open.
How do I install? When I double click on the filename, the message says "must open with an application. What application?
Would appreciate any help.
Thanks, brujo32

---

### Post by 405jayb on 2010-04-20
I think this is how I did it. Open terminal type: cd Folder (folder being where it downloaded to) enter then type: sudo ./GoogleEarthLinux.bin.

---

### Post by sab3156 on 2010-04-20
Open your terminal, go to the location of where you downloaded the .bin file, and do:

[B]chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin

[/B]-sab3156

---

### Post by pmlxuser on 2010-04-20
+1 above, but sometimes it helps to also ```
$ chmod +x filename.ext 
``` to make it executable.. and then do the ./filename.extension. sometimes it requires you to do it as sudo if you want chnages to be system wide (other users should be able to use it too.)

damn beaten by -sab3156

---

### Post by Dayofswords on 2010-04-20
google earth in the medibuntu repo(its currently down for some reason)

---

### Post by brujo32 on 2010-04-20
> **sab3156 said:**
> Open your terminal, go to the location of where you downloaded the .bin file, and do:

[B]chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin

[/B]-sab3156

That worked perfectly. Thanks, and thanks to the other contributors.
brujo32 :)

---

### Post by dcstar on 2010-04-21
It must be sooo hard to use a search engine:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

