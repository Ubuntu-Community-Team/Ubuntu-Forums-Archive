---
title: "Locate not existing index.html"
date: 2011-05-24
forum: General Help
---

### Post by melinux on 2011-05-24
Hello fellow ubuntu users,

I have a small problem that drives me nuts!

I have installed a lamp server on my fresh installed laptop and i changed the directory's in the 000-default file to the ones i need.

But even after restarting apache, it is directing me to that pre-placed index.html. But it is not there :|

The weird thing is also:

```

melinux@Ubuntu:/var/www$ locate index.html
<snap>
/usr/share/synaptic/html/index.html
/usr/share/transmission/web/index.html
/usr/share/ubuntu-artwork/home/firefox-index.html
/usr/share/ubuntu-artwork/home/index.html
/usr/share/vlc/http/index.html
/usr/share/vlc/lua/http/index.html
/var/www/index.html
melinux@Ubuntu:/var/www$ ls
dropit
```

There is no index.html file whatsoever :confused:

Also, like i already mentioned before, I have changed the directory to the /var/www/dropit/public/, but that isn't work either... Of course i did a apache restart.

Can someone explain me why it is doing this?

---

### Post by btindie on 2011-05-24
If you don't specify a file in the URL, i.e. [http://localhost/](http://localhost/), it will by default return index.html if it exists.

The locate program uses a database to speed up searches, it doesn't trawl the filesystem. Try running
```
$ sudo updatedb
```then if /var/www/index.html doesn't exist it won't then appear in the search results.

If /var/www is the document root of your web server then try creating an index.html file in there.

---

### Post by melinux on 2011-05-28
> **btindie said:**
> If you don't specify a file in the URL, i.e. [http://localhost/](http://localhost/), it will by default return index.html if it exists.

The locate program uses a database to speed up searches, it doesn't trawl the filesystem. Try running
```
$ sudo updatedb
```then if /var/www/index.html doesn't exist it won't then appear in the search results.

If /var/www is the document root of your web server then try creating an index.html file in there.
Thank you, this did the trick!

---

