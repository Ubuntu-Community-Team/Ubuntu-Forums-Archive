---
title: "Adding plugins to Opera"
date: 2006-05-23
forum: General Help
---

### Post by cobbweb on 2006-05-23
Does anyone know how to add the Mplayer plugin to Opera? also the Xine? 

 Thanks, 

 Cobbweb

---

### Post by cobbweb on 2006-05-23
Ok I belive i found the solution. 

 You copy the /usr/lib/gxine/gxineplugin.so
 file to 

/usr/lib/opera/plugins

 however I can't seem to move the .so file to the plugins folder.... anyone know that command? 

Thanks, 

 Cobbweb

---

### Post by danielph on 2006-05-27
[QUOTE=cobbweb]however I can't seem to move the .so file to the plugins folder.... anyone know that command? [/QUOTE]

I believe that you need to make a symbolic link. It goes something like this. 
```
cd /usr/lib/opera/plugins
sudo ln -s /usr/lib/gxine/gxineplugin.so .

```

Regards

Dan

---

