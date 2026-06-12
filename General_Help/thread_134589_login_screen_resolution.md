---
title: "login screen resolution"
date: 2006-02-22
forum: General Help
---

### Post by khateeb on 2006-02-22
Hi all

My login screen has higher resolution than everything else. The thing is while it works well and gives a very nice image at login, the monitor seems to object to the resolution and shows a floating message telling me to reduce the screen resolution!

Does my monitor support this higher screen resolution or not? i am using HP 1902

Thanks

---

### Post by heimo on 2006-02-22
[quote=khateeb]Does my monitor support this higher screen resolution or not? i am using HP 1902
[/quote]

Is it this [monitor]("http://h18000.www1.hp.com/products/quickspecs/11928_div/11928_div.HTML")? If it's TFT and 17" or 19" 4:3 (not wide) then it's probably 1280x1024 and you should use only this native resolution. It should be possible to remove other options from /etc/X11/xorg.conf to force it to use this mode all the time. See my signature for details.

---

