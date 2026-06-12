---
title: "Auto Script to release all exe permissions ??"
date: 2011-06-17
forum: General Help
---

### Post by Alexdelpiero1974 on 2011-06-17
in Ubuntu 11.04 :
i dont know why they blocked exe files to be run automatically by wine 
and you must release every exe file permission in order to run it 
i dont think this will be any good step , as even you have al lthe viruses in the world 
in your exe files , it will not affect your ubuntu system , it will only damage wine itself
if so , you can install a new wine service . 

now , i need an script file to release all the exe files permissions on my hard disk ????

---

### Post by KeyserSoze93 on 2011-06-17
```

find -iname '*.exe' -exec chmod +x '{}' \;

```

Having said that, remember that not all viruses want to take control of the system. It could just be a piece of malicious software designed to mess with your own files.

I assume you allow Wine-hosted application's to access your home folder in some way, and this would include any viruses.

---

### Post by Alexdelpiero1974 on 2011-06-17
> **KeyserSoze93 said:**
> ```

find -iname '*.exe' -exec chmod +x '{}' \;

```Having said that, remember that not all viruses want to take control of the system. It could just be a piece of malicious software designed to mess with your own files.

I assume you allow Wine-hosted application's to access your home folder in some way, and this would include any viruses.

- is this will search all the root until reach the media folder to reach all my partitions ????
- can i save this in a file and save it as .sh to be automatic script ?

---

