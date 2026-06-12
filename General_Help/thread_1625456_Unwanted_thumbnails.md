---
title: "Unwanted thumbnails"
date: 2010-11-19
forum: General Help
---

### Post by Whistling Nixie on 2010-11-19
I've just bought a new desktop with Maverick installed. I've manually created some folders in Nautilus, but if I save something in them, a thumbnail of the saved file is added to the desktop. How do you switch this off?

---

### Post by TeoBigusGeekus on 2010-11-19
Where have you saved the files?
If you've saved them in the Desktop folder, they're bound to be present at the desktop.

---

### Post by Whistling Nixie on 2010-11-19
From the **Places** menu, I opened the **Home Folder**. From there, I selected **Bookmarks**>**Add Bookmark**, and created four bookmarks (Documents, Downloads, Images and Other). Put in a USB drive with pictures on it, and by drag-and-drop I copied an image to newly-created Documents folder. It saved, but also put a thumbnail of said image on desktop. Right-clicked on thumbnail, and selected **Delete**, which obviously deletes not just the thumbnail, but also the actual file.

---

### Post by TeoBigusGeekus on 2010-11-19
Hmm... Try this then:
Open terminal and give 
```
gconf-editor
```
Go to apps>nautilus>preferences and see if the desktop_is_home_dir is checked - uncheck it if it is.

---

### Post by Whistling Nixie on 2010-11-19
Done that. It was already unchecked. Besides, I downloaded Thunar file manager, and the same thing happened.

**SOLVED.** Forced to re-install, since there were *myriad* things wrong with the install that had been dome at the factory. And playing around with KDE in an attempt to skirt the issue didn't solve things. Nor did trying to remove KDE afterwards, finally breaking my OS in the process. At least they included a Maverick amd64 install disc with the computer! :)

---

