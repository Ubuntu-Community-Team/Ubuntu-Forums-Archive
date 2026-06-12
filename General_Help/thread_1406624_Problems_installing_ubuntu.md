---
title: "Problems installing ubuntu"
date: 2010-02-14
forum: General Help
---

### Post by bmvalves on 2010-02-14
Hello , I ve got a bit of a problem , every time I try to install ubuntu 9.10 installer for windows I get this msg after awhile **[COLOR=#ff0000]PERMISSION[/COLOR]** **[COLOR=#ff0000]DENIED[/COLOR]** . Im running as administrator and it is not the first time i use this version on my laptop . Thanks for your time.

---

### Post by joeknoodle on 2010-02-14
I'm an amateur, so take my advice with all precautions and no warranty.

You might want to...

Mount the disk you wish to install to

Then in a terminal:
```

sudo chown -R admin:admin path/to/drive (edit in you might want to use path/to/"ubuntu" folder)

```Where:
sudo is superuser
chown is to take ownership
-R is apply through all directories
admin:admin is user "admin" as an administrator
path/to/drive or path/to/"ubuntu" folder is the path to the disk/folder that you mounted

If it asks for a password use "topsecret" without the quotes.

---

