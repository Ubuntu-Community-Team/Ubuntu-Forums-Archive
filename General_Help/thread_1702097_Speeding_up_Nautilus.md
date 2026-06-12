---
title: "Speeding up Nautilus"
date: 2011-03-07
forum: General Help
---

### Post by neu5eeCh on 2011-03-07
Folders with large collections of photos are incredibly slow to load in Nautilus. Sometimes Nautilus goes grey and never recovers. I've tried increasing the size of the thumbs cache but that doesn't seem to make a difference. Ubuntu's Nautilus is also several times slower than Fedora on the same computer and same folders (Multiple OS). 

Any suggestions? I've gotten so that I mainly use Thunar, which loads the same folders in a fraction of a second, though Thunar comes with its own limitations. Is there a way, yet, to [make Nautilus behave like Thunar]("http://brainstorm.ubuntu.com/idea/6878/").

---

### Post by TeoBigusGeekus on 2011-03-07
> **VTPoet said:**
> ...though Thunar comes with its own limitations.
Such as?
I use thunar for the last 8 months and it kicks nautilus' behind in every aspect.

---

### Post by fragos on 2011-03-07
Nautilus is sensitive to the number of files in a folder. Perhaps not the solution you're looking for but creating sub folders, perhaps subject oriented, will speed things up and make make finding particular images easier. Works for me.

---

### Post by Alan.Brown on 2011-03-07
In Nautilus try **Edit > Preferences > Preview > Show thumbnails** and set to **Never**.   You can also set all other Preview options to **Never**.

Time is taken up by displaying thumbnails for each file - the more files, the more time taken.

Nautilus may be slower under Ubuntu than Fedora because you have different settings.

Hope this helps.

Alan

---

