---
title: "Mass Rename All Picture Extensions."
date: 2010-06-24
forum: General Help
---

### Post by Roasted on 2010-06-24
Linux cares about case sensitivity. This is a problem when some picture upload services accept .jpg while my camera uploaded the thousands of pictures I have as .JPG.

Thanks to help from users in the IRC chat, I can handle this task fine PER DIRECTORY. The problem is, I still have a ton of directories. Is there a way I can select - Pictures - Mass rename EVERYTHING inside and everything inside all sub directories from JPG to jpg?

Basically I want to take the existing command: 

rename 's/\.JPG$/.jpg/' *.JPG

a step further.

---

### Post by renkinjutsu on 2010-06-24
> **Roasted said:**
> Linux cares about case sensitivity. This is a problem when some picture upload services accept .jpg while my camera uploaded the thousands of pictures I have as .JPG.

Thanks to help from users in the IRC chat, I can handle this task fine PER DIRECTORY. The problem is, I still have a ton of directories. Is there a way I can select - Pictures - Mass rename EVERYTHING inside and everything inside all sub directories from JPG to jpg?

Basically I want to take the existing command: 

rename 's/\.JPG$/.jpg/' *.JPG

a step further.

Try this
```

cd /to/your/picture/directory
find ./ -type d -exec rename 's/\.JPG/\.jpg/g' '{}'/\* \;

```

---

