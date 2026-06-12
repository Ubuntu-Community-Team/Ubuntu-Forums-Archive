---
title: "Replace a certain word in every file in a particular folder"
date: 2009-08-11
forum: General Help
---

### Post by ltwinner on 2009-08-11
How would i do the following - i want to change all occurrences of the word 'blue' in every file in a certain directory to 'green'. anyone have any ideas?

---

### Post by lykeion on 2009-08-11
```
find /certain/directory -type f -exec sed -i 's/blue/green/g' {} \;
```

---

### Post by ltwinner on 2009-08-11
Thanks mate!

---

