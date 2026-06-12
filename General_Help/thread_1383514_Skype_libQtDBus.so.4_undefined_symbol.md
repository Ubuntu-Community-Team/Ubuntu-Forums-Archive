---
title: "Skype libQtDBus.so.4: undefined symbol"
date: 2010-01-17
forum: General Help
---

### Post by Gorlist on 2010-01-17
Hi, ive made a slight mistake on my Ubuntu 9.10 64bit. I was trying to get Voodoo Motion Tracking software to work, and it was having trouble locating some Qt Libs, so I decided it was a good idea to move its included libs into /user/lib32 directory. 

Voodoo now works, but Skype instead comes up with:

```
skype: symbol lookup error: /usr/lib32/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

```

Skype was installed using their own provided 64bit .deb - it was previously working fine.

How can I undo the damage? :)

---

### Post by n0dix on 2010-01-17
See this link: [http://ubuntuforums.org/archive/index.php/t-924895.html]("http://ubuntuforums.org/archive/index.php/t-924895.html")

---

### Post by Gorlist on 2010-01-18
thanks for the link, but not very useful - I need to somehow back date all of my libQtDBus libs, if I force remove and reinstall its not fixing the problem..

ignore, fixed - copied them back over from the live cd

---

