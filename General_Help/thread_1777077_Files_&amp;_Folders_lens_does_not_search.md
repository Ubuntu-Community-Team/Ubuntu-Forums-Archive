---
title: "Files &amp; Folders lens does not search"
date: 2011-06-07
forum: General Help
---

### Post by hounddog32 on 2011-06-07
I have a laptop and a desktop with Natty. The laptop does exactly what it's supposed to: I press [super]+f, type the first few letters of a file I want to use (that I have used recently), the results on the lens change to what I want. The desktop is different. Application search works fine, but files & folders does not change whatever I type in - the same most recent files show up on the list.

Solved - while I was typing this up, but I figure someone might appreciate the fix. Delete the Zeigeist database
```
rm ~/.local/share/zeitgeist -r
```
Restart zeigeist
```
zeitgeist-daemon --replace
```
Try searching now...

---

### Post by windfix on 2011-07-18
Thanks!  I had the same issue

---

### Post by widespread1 on 2011-10-03
I had the same issue as well. thanks for posting. :)

---

### Post by bluepicaso on 2012-02-29
> **hounddog32 said:**
> I have a laptop and a desktop with Natty. The laptop does exactly what it's supposed to: I press [super]+f, type the first few letters of a file I want to use (that I have used recently), the results on the lens change to what I want. The desktop is different. Application search works fine, but files & folders does not change whatever I type in - the same most recent files show up on the list.

Solved - while I was typing this up, but I figure someone might appreciate the fix. Delete the Zeigeist database
```
rm ~/.local/share/zeitgeist -r
```Restart zeigeist
```
zeitgeist-daemon --replace
```Try searching now...




YOu are awesome

---

