---
title: "Find Boolean operators help"
date: 2011-01-17
forum: General Help
---

### Post by COKEDUDE on 2011-01-17
I was reading this find guide and I saw something with the -and option that I don't think is correct. Do you need the -and option in this? 

```
$ find /mp3-collection -name 'Metallica*' -and -size +10000k 
```

I found my file that was bigger than 500 MB with and without the -and option. 

```
~ $ find / -iname 'ifn*' -size +500M 2>/dev/null
~ $ find / -iname 'ifn*' -and -size +500M 2>/dev/null
```

[http://www.codecoffee.com/tipsforlinux/articles/21.html](http://www.codecoffee.com/tipsforlinux/articles/21.html)

---

