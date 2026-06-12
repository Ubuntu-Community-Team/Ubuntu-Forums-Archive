---
title: "Apache2 ftp folder or shortcut?"
date: 2011-04-26
forum: General Help
---

### Post by LuniTux on 2011-04-26
Hello,

I have a website that accesses ftp. I was wondering which would be more secure. A "shortcut" inside the website folder that leads to the ftp folder, or having the ftp folder directly inside the website folder.

Key:
[COLOR="RoyalBlue"]Normal Folder[/COLOR]
[COLOR="Cyan"]Linked folder[/COLOR]
[COLOR="Lime"]Normal File[/COLOR]

```
ls /var/www/
[COLOR="RoyalBlue"]mywebsite[/COLOR] [COLOR="#00ffff"]myftp[/COLOR]
```

or

```
ls /var/www/mywebsite
[COLOR="Lime"]index.php[/COLOR] [COLOR="#00ff00"]search.php[/COLOR] [COLOR="RoyalBlue"]myftp[/COLOR]
```

Please let me know if the message is not clear.

Thanks,

---

