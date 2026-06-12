---
title: "Keeping sites separate on apache2"
date: 2012-08-05
forum: General Help
---

### Post by Hovercat on 2012-08-05
I can't really think of a better way to word this, but I've tried many configurations and I can't get it exactly right.

[http://hovertac.co.cc](http://hovertac.co.cc) goes to /var/www

No problems there.

[http://copiaguerobotics.co.cc](http://copiaguerobotics.co.cc) goes to /home/robotics/www

No problems there.

However, [http://24.38.249.14](http://24.38.249.14) goes to /home/robotics/www.

Basically, what I'm trying to do is configure apache to the point where if the domain is NOT hovertac.co.cc or copiaguerobotics.co.cc, it goes to /var/www2.

apache2.conf: [http://pastebin.com/kx9VMUMs](http://pastebin.com/kx9VMUMs)

httpd.conf: ```
ServerName localhost
```

ports.conf: [http://pastebin.com/2XzuYCAN](http://pastebin.com/2XzuYCAN)

hovertac.co.cc: [http://pastebin.com/eAc6tUPW](http://pastebin.com/eAc6tUPW)

copiaguerobotics.co.cc: [http://pastebin.com/zX4r7bGF](http://pastebin.com/zX4r7bGF)

other: [http://pastebin.com/vXYDnQAw](http://pastebin.com/vXYDnQAw)

Thanks if anyone can help.

EDIT: Did some testing.

I removed hovertac.co.cc and copiaguerobotics.co.cc from sites-enabled and on any 3, it took me to the page in /var/www2.

I re-enabled only hovertac and all sites took me to /var/www.

I disabled hovertac and enabled copiaguerobotics and all sites took me to /home/robotics/www.

---

