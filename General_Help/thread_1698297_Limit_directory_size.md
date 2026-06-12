---
title: "Limit directory size"
date: 2011-03-02
forum: General Help
---

### Post by Sinopa on 2011-03-02
I have 2 directories in my home folder that I would like to set a size limit on. The directories are ~/backup and ~/temp. Is there an **easy** way to limit the size of a directory without having to make partitions?

---

### Post by Sinopa on 2011-03-22
*bump*

---

### Post by TeoBigusGeekus on 2011-03-22
Never done it myself, but I think it can be done with quotas.
Don't know how easy it is though...

---

### Post by blueridgedog on 2011-03-22
You can setup per directory or per partition quotas.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html)

and 

man quota

and 

see "linux quota directory" on Google:

[http://www.google.com/search?aq=0&oq=Linux+limit+size+of+direc&sourceid=chrome&ie=UTF-8&q=linux+limit+size+of+directory#hl=en&sugexp=ldymls&pq=linux%20quota&xhr=t&q=linux+quota+directory&cp=13&qe=bGludXggcXVvdGEgZA&qesig=RPFS3ymQkuRWXl8ERLORnw&pkc=AFgZ2tktMtr99vZSkS9Jk7ENB6dhMTgMHN7VqQFWWVtVGId4aVIxQjFqXOu9ezzmiOvfEw2TlyRhGhPq_TK_-CWW_9_f0-557A&pf=p&sclient=psy&aq=0&aqi=&aql=&oq=linux+quota+d&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=b26d2f4496b7882f](http://www.google.com/search?aq=0&oq=Linux+limit+size+of+direc&sourceid=chrome&ie=UTF-8&q=linux+limit+size+of+directory#hl=en&sugexp=ldymls&pq=linux%20quota&xhr=t&q=linux+quota+directory&cp=13&qe=bGludXggcXVvdGEgZA&qesig=RPFS3ymQkuRWXl8ERLORnw&pkc=AFgZ2tktMtr99vZSkS9Jk7ENB6dhMTgMHN7VqQFWWVtVGId4aVIxQjFqXOu9ezzmiOvfEw2TlyRhGhPq_TK_-CWW_9_f0-557A&pf=p&sclient=psy&aq=0&aqi=&aql=&oq=linux+quota+d&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=b26d2f4496b7882f)

---

### Post by Sinopa on 2011-03-22
Ah! That was the solution. Thank you :)

---

