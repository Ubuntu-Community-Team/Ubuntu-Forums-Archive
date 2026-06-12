---
title: "First VPS"
date: 2009-09-17
forum: General Help
---

### Post by josephmcnelis on 2009-09-17
Hey all,

Im a web developer but a bit of a novice and definitly a noob when it comes to Ubuntu.

At the moment im getting my first VPS and its running on a Ubuntu 8.04 64bit-Standard enviroment, im taking everything one step at a time, just wondering if anyone can recommend any tutorials to help me set it up so thats it secure.

Ill be using PHP, Apache and Mysql on it and to be honest havent got a clue as to where to start...

Also could anyone help me with (probably the simplest of commands) how to turn apache off? 

I reckon it would be best to turn it off until i feel comfortable enough that its secure.

Thanks in advance ^_^

---

### Post by jimjawn on 2009-09-17
Since you're running this in a VPS, you should think about this as an actual 'server', one that you would be running on your own network somewhere.  

By default, the standard ubuntu lamp installation is pretty secure and you can be safe installing it and running it.  Generally, its the program that's running that needs to be locked down.

I find that reading the tutorials in howtoforge, combined with their forums is a great place to get started.  [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts).

Another great tool that I've found is fail2ban.  Its proactive server defense [http://www.ubuntux.org/preventing-brute-force-attacks-with-fail2ban-on-debian-etch](http://www.ubuntux.org/preventing-brute-force-attacks-with-fail2ban-on-debian-etch)

And locking down the server tightly is what's also know as hardening.  The forums here have a great post... [http://ubuntuforums.org/showthread.php?t=1002167](http://ubuntuforums.org/showthread.php?t=1002167)

Hopefully that's enough to get started.

---

### Post by josephmcnelis on 2009-09-17
Thanks those links look promising. Im in work at the moment so ill defo have a look through in greater detail later. :P

---

