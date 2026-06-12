---
title: "Find -atime problem"
date: 2010-08-04
forum: General Help
---

### Post by aksovalye on 2010-08-04
This is my first message here, so first of all I want to say hello to everyone. :)

And here is my first question:

Just for checking if I use find command correctly, I did followings in order:

1. Boot with Ubuntu netobok remix 10.04 live-usb.
2. Plug my MyPassport external hard drive.
3. Open a "desktop.ini" file in that disk by gedit, with the help of nautilus to find the file.
4. Did not change the document and Close gedit.
5. In terminal I run following command:

```
find /media/MyPassport -amin -60
```6. It did not display desktop.ini file, but it displays a folder named something like ".Trash999" and some folders I have not surely accessed in the last 60 minutes.

I was expecting only desktop.ini to be listed.

Could you please guide me where am I doing wrong?

---

### Post by Vaphell on 2010-08-04
i suspect than in desktop environments amin/atime are pretty much useless. System accesses files and dirs all the time to do stuff like generate thumbnails, manage trash and such, so the list will be polluted by stuff you haven't touched manually. To get rid of dirs you can use **-type f**
no idea what's with not showing the file though

---

