---
title: "FAT32 Label is Always Caps.."
date: 2010-11-28
forum: General Help
---

### Post by Austifarian on 2010-11-28
Yeah, I've been messing around with my partitions recently to make them more organized and appealing to my OCD file management habits. 

My main partition that I use to store all my files and windows programs on was previously labeled "Free" since I installed Ubuntu a few weeks ago and created separate partitions for things, I didn't like the vagueness of the name, so I changed it to "Storage" via GParted Partition Editor.

Yet, for some reason it always changes its self to all capital letters. I label it "Storage", it becomes "STORAGE". I've researched around for others who have similar issues, but they usually ended up with a response similar to "It's Fat32, so it's always capital." I don't see how that's true, considering mine was labeled "Free" for the longest time..

**So basically, does anyone know how to relabel Fat32 partitions to include both upper and lower case characters?**

---

### Post by Austifarian on 2010-11-28
Uuh, help, please?

---

### Post by dcstar on 2010-11-29
> **Austifarian said:**
> Uuh, help, please?

```
man dosfslabel
```

That will set mixed case, report the **gparted** problem as a bug.

---

### Post by HermanAB on 2010-11-29
The original DOS volume labels were indeed uppercase only.

---

### Post by pteri498 on 2010-11-29
Then is there a way to force Ubuntu to make a mount directory in /media in all lower case instead of upper?

---

