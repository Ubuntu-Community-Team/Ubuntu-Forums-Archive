---
title: "Mystery server running"
date: 2010-12-17
forum: General Help
---

### Post by LeeM on 2010-12-17
I have removed apache2 (AFAIK) and also ApacheFriends version of XAMPP from my desktop PC. However, I still have a server running - I know this, since I get to my local web pages when I browse to 'localhost'. Mystery! Is it possible that ANOTHER web server is running? And if so, how do I find it?? I want to do a clean install of apache2.

Thanks!:confused:

---

### Post by warriorforgod on 2010-12-17
I would do a search on your pc for apache.  You can do this by typing the following from a command prompt.

sudo find /* -name apache

You might also try the following.

sudo find /* -name http
sudo find /* -name httpd

---

### Post by WorMzy on 2010-12-17
You say you removed them, but have you restarted your computer since doing so? Removed applications do not cease functioning upon removal, although they may terminate with an error code if they try to read a file which no longer exists.

If you don't want to restart for whatever reason, then you can still kill the process by running
```
sudo killall apache
```
or, if that fails, try
```
sudo killall -9 apache
```

I'm not sure about XAMPP. It's possible it has a similarly named process which can be terminated with the same method.

---

### Post by gmargo on 2010-12-17
Here are some handy commands for your toolbox.  With these you should be able to figure out what server is responding:

To find a particular process listening on a particular port (80 in this case):
```

sudo lsof -i :80

```To list all listening processes:
```

sudo netstat -tnulp

```

---

