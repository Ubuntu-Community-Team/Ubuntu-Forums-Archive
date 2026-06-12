---
title: "Custom Mime Type Icon"
date: 2010-07-18
forum: General Help
---

### Post by dodle on 2010-07-18
I followed a few tutorials online and was able to create my own mime type (application/dbp), which opens in the program I've associated it with.  But I can't figure out how to give it a custom icon.  According to the tutorials, I just need to take an icon, rename it, and place it in the /usr/share/icons/gnome directory.  For example, I am using a scalable-vector graphic, so I name it "application-dbp.svg", then place it in /usr/share/icons/gnome/scalable/mimetypes.  I'm not sure if it's necessary, but then I use the following command:
```
sudo update-mime-database /usr/share/mime
```

Then I refresh nautilus... nothing.  So I log out, and back in.  Still, the icon for .dbp extensions is a plain white paper.  So am I close to doing it the right way?  Does anybody know how to do it?

---

### Post by skooter1121 on 2010-07-30
I just tried the same using the Ubuntu tutorial.

NO LUCK !!


Have you found a solution?

-SK

---

### Post by dodle on 2010-07-31
Not yet.

---

