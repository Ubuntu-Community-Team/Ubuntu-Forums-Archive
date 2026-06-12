---
title: "Can't see any of bookmarks in firefox"
date: 2012-08-03
forum: General Help
---

### Post by alenn on 2012-08-03
Hi all

Today my bookmarks dissappeared. Can't see them in bookmarks manager nor in bookmarks toolbar, and I can't add any of bookmarks. I purged firefox and installed it again but the problem persists. I believe that some configuration files are left on my PC after purging firefox. Can you tell me how to fix this. I think I should delete these conf files but can't locate them.

---

### Post by Habitual on 2012-08-03
close firefox if open...
terminal > 
```

mv ~/.mozilla/firefox/ ~/.mozilla/firefox.org
```
run firefox. All shiny and new.

---

### Post by alenn on 2012-08-03
> **Habitual said:**
> close firefox if open...
terminal > 
```

mv ~/.mozilla/firefox/ ~/.mozilla/firefox.org
```
run firefox. All shiny and new.

thank you man, you saved me, it's working now. Can you write me complete path to this file.

---

### Post by Habitual on 2012-08-03
> **alenn said:**
> thank you man, you saved me, it's working now. Can you write me complete path to this file.

Glad it worked out.

Edit: 
sorry, 2 ways to find this file.
easiest is knowing where it is to begin with. ;P ... and
terminal > 
```
 find `pwd` -name firefox -type d
```

---

### Post by alenn on 2012-08-03
> **Habitual said:**
> Glad it worked out.

Edit: 
sorry, 2 ways to find this file.
easiest is knowing where it is to begin with. ;P ... and
terminal > 
```
 find `pwd` -name firefox -type d
```

thank you

---

