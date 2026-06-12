---
title: "restore wine defaults"
date: 2006-04-07
forum: General Help
---

### Post by neoroses on 2006-04-07
Hiay just install wine.,,but for some reason i decided to mess with the c:/ drive location in the winfecfg and now its seys i dont have one...and its all messed up lol..i have tried reinstalling wine still saved my old config....so is there a way i kan resotre the wine defaults so it all works again ?:)

thanks

---

### Post by aysiu on 2006-04-07
Applications > Accessories > Terminal ```
rm ~/.wine
```

---

### Post by neoroses on 2006-04-07
thanks for the quick reply however when i do that i get:

rm: cannot remove `/home/sam/.wine': Is a directory

---

### Post by aysiu on 2006-04-07
[QUOTE=neoroses]thanks for the quick reply however when i do that i get:

rm: cannot remove `/home/sam/.wine': Is a directory[/QUOTE] Sorry. Try this. ```
rm -R ~/.wine
```

---

### Post by neoroses on 2006-04-07
thanks alot m8 =)

---

### Post by catalina on 2008-05-09
Echo that thank you!

---

