---
title: "Wget images do not load"
date: 2010-12-20
forum: General Help
---

### Post by layers on 2010-12-20
If I use
```
wget http://static.die.net/earth/mercator/1600.jpg
```
, the image that is then downloaded cannot be loaded. it says "Error interpreting JPEG image file (Not a JPEG file: starts with 0x47 0x49)"

If I am to go to that address and download the file manually though my browser, everything is fine.

Does any one know how ti make wget work?

---

### Post by TeoBigusGeekus on 2010-12-20
Try with curl instead:
```
curl -o picture.jpg http://static.die.net/earth/mercator/1600.jpg
```
No idea why it doesn't work with wget.

---

### Post by ron999 on 2010-12-20
Look here:- [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1647582&highlight=%2Fmercator%2F1600.jpg]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1647582&highlight=%2Fmercator%2F1600.jpg")

---

### Post by layers on 2010-12-20
curl worked. thanks

---

### Post by andersbk on 2011-03-03
FYI, I'm running 10.10, and added the following to my crontab.
i.e.,
> crontab -e
...to edit.

And, mine looks like:

```

> crontab -l
35 */3 * * * /usr/bin/wget -O ~/Pictures/1600.jpg --user-agent="Mozilla/5.0 (X11; U; Linux x86_64; en-US) AppleWebKit/534.10 (KHTML, like Gecko) Chrome/8.0.552.224 Safari/534.10" http://static.die.net/earth/mercator/1600.jpg > /dev/null 2>&1

```

enjoy!

---

