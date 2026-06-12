---
title: "Changed the trash icon, now wont show full"
date: 2011-11-23
forum: General Help
---

### Post by clahinsch on 2011-11-23
Im using 11.10

So I changed the trash icon on the desktop from my current icon

 now it won't show full

so I want to know how to make my desktop trash can operate as it should showing me when its full and when its empty again

thanks for any advice

---

### Post by mikejonesey on 2011-11-23
user-trash-full

```
cd [your icon theme]...
find . -type f -name *trash* | xargs eog
```

ps if you have an icon cache delete it or rebuild it...

---

### Post by clahinsch on 2011-11-25
**Re: Changed the trash icon, now wont show full**             
                                                                user-trash-full

     Code:
     cd [your icon theme]... find . -type f -name *trash* | xargs eog 
ps if you have an icon cache delete it or rebuild it...
                                                                                               __________________
                My personal website with blog n apps :smile:
[http://www.mikejonesey.co.uk/](http://www.mikejonesey.co.uk/)


Hi mikejonesey,

thanks for your quick reply.

cd /usr/share/icons/ubuntu-mono-dark find . -type f -name *trash* | xargs eog
opens image viewer without any images :confused:

Don't really know what to do with it.

---

