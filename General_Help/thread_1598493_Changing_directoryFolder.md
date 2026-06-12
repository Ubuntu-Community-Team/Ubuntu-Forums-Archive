---
title: "Changing directory/Folder"
date: 2010-10-16
forum: General Help
---

### Post by hewjr1000 on 2010-10-16
Can Someone look at attached screenshot and tel me why I can't cd to John Lennon.

Henry

---

### Post by TeoBigusGeekus on 2010-10-16
Try 
```
cd John\ Lennon
```
Linux doesn't automatically recognise spaces in names.

---

### Post by nothingspecial on 2010-10-16
```
cd John\ Lennon
```or 
```

cd "John Lennon"
```

bash doesn`t do spaces in file or directory names :)

---

### Post by hewjr1000 on 2010-10-16
The quotes worked.

Thank you very much.

BTW can I change from Bash to something better?

Henry

---

### Post by nothingspecial on 2010-10-16
There isn`t better really. Some people prefer zsh. 

fish is another option.

Understanding bash is the best option. I don`t mean that in a condescending manner. Really, a passing knowledge (not in depth) of bash will help you enjoy linux alot.

However it is not necessary.
[COLOR=#CC0000][/COLOR]

---

### Post by CharlesA on 2010-10-16
Using tab completion is helpful for filenames as well.

---

