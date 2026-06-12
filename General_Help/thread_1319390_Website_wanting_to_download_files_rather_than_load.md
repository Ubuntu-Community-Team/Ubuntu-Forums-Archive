---
title: "Website wanting to download files rather than load them"
date: 2009-11-08
forum: General Help
---

### Post by Renster on 2009-11-08
I have recently installed phpmyadmin, apache, mysql, and php5. However, the same experience happens to me all the time and I have yet to figure out why, nor do any of my friends that use Ubuntu know the answer to.

My website (even when I goto [http://localhost](http://localhost)) wants to download a file rather than load it up. I have no changed any permissions in the /var/www and I would like to know what is going on. Need to get some sort of access to my home website but it just wants to download the file (index.php or whatever it may be) instead of just loading it. 

(No Similar Posts showed up to this request, that or I am not wording it well. Help anyone?)

(And I'm still running an older version of Ubuntu, may this be the reason?)
```
renster@ren-desktop:~$ cat /etc/issue
Ubuntu 8.04.3 LTS \n \l

renster@ren-desktop:~$

```

Thanks much!

-Ren

---

### Post by Druke on 2009-11-08
I'm no expert on the matter, but it sounds like apache is not set up to handle php correctly.

[https://help.ubuntu.com/community/ApacheMySQLPHP#To](https://help.ubuntu.com/community/ApacheMySQLPHP#To) install the default LAMP stack in Ubuntu 7.04 (Feisty Fawn) Ubuntu 7.10 (Gutsy Gibbon) Ubuntu 8.04 LTS (Hardy Heron), 8.10 (Intrepid Ibex) and 9.04 (Jaunty Jackalope)

---

### Post by Renster on 2009-11-08
> **Druke said:**
> I'm no expert on the matter, but it sounds like apache is not set up to handle php correctly.

Anything to change? Ideas? Suggestions? It's been like this every time I reformat though, which has only been a couple of times.

---

### Post by Druke on 2009-11-08
edited my post with the help linkage on the subject.

---

### Post by Druke on 2009-11-08
notably that is one of the most bloated howtos I've ever seen... Sorry to have linked it but it is comprehensive.

If that is to rough on you let me know and I'll look up something else.

---

### Post by Primefalcon on 2009-11-08
> **Renster said:**
> Anything to change? Ideas? Suggestions? It's been like this every time I reformat though, which has only been a couple of times.
do a reinstall of the libapache2-mod-php5 package, restart apache by running

```
sudo /etc/init.d/apache2 restart
```


clear your browser cache and re-check it... 


This happens here and there for some reason, I've had it a couple of times myself, but doing the above should fix it

---

### Post by Primefalcon on 2009-11-08
oh... also try the apache2-mpm-prefork as well for a reinstall

---

### Post by Renster on 2009-11-08
> **Druke said:**
> notably that is one of the most bloated howtos I've ever seen... Sorry to have linked it but it is comprehensive.

If that is to rough on you let me know and I'll look up something else.

I'll give it a shot. Keep me informed if anything else arises.

---

### Post by Druke on 2009-11-08
ack! now a feel really bad for my post, Primefalcon's is much more simple. (it's fixing the problem instead of removing doing it from scratch, always a better idea if you know how)

---

### Post by Renster on 2009-11-08
> **Primefalcon said:**
> oh... also try the apache2-mpm-prefork as well for a reinstall
Awesome! This did it PrimeFalcon.

Much thanks to you!

-Ren

---

