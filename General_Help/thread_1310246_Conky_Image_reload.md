---
title: "Conky Image reload"
date: 2009-11-01
forum: General Help
---

### Post by Amstell on 2009-11-01
Anyone know how to reload this command in conky every 15 minutes

 ${image /home/john/image.gif}

I have an image that I pull off the web and would like to update it every 15 minutes to keep it current.

Thanks

---

### Post by Amstell on 2009-11-02
bump

Anyone have any ideas....

Thanks

---

### Post by Amstell on 2009-11-03
One more time....

Can anyone help me out?

---

### Post by Amstell on 2009-11-03
Figured it out : 

This doesn't cache the image so it reloads when updated. 

[PHP]imlib_cache_size 0[/PHP]

---

