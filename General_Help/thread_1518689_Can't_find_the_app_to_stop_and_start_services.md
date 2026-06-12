---
title: "Can't find the app to stop and start services"
date: 2010-06-27
forum: General Help
---

### Post by ubnewbie2 on 2010-06-27
I thought it was in the System>administration menu somewhere, but I just can't see it.  What is it called, and where do I find it please?

---

### Post by NoBugs! on 2010-06-27
You can set them in Boot-up Manager (System-Admin-Boot Up Manager)
You can install it from the Software Center.

---

### Post by ubnewbie2 on 2010-06-27
That's not the one I am used to seeing, but it works.  All I want to do is stop/start a service to get it to re-read it's conf files.  

They must have changed to this new one in the newer Ubuntu (I upgraded from 8.10 fairly recently).

---

### Post by stderr on 2010-06-27
What did you upgrade to?

If you mean a service such as you'd normally start|stop|restart etc. via /etc/init.d/... then they're mainly using the **service** command now. By way of example for the Denyhosts app:

```
service denyhosts restart
```

If you tell us which service it is, we may be able to offer another solution too. For example, you can essentially restart Pulseaudio with:

```
pulseaudio -k
pulseaudio -D
```

---

### Post by ubnewbie2 on 2010-06-27
I upgraded to the latest, 10.04.  In my old version there was a nice gui that listed all services and you could just untick them to stop them, then tick them again to restart.  The GUI Boot-up Manager mentioned above is similar looking, and I guess it's the latest, just it wasn't installed by default.

It is actually Apache2 I wanted to restart, and one web page I went to mentioned a command - apachectl -  but that didn't seem to be there, but later I found apache2ctl, so now I can do it at the command line too.

---

### Post by chrismitt2002 on 2010-06-27
could it possable be called start up applications ????

---

### Post by ubnewbie2 on 2010-06-27
> **chrismitt2002 said:**
> could it possable be called start up applications ????

Not applications,  services, the things that run in the background, like CUPs, Apache, etc etc

---

### Post by Detonate on 2010-06-27
The program "webmin" is a very complete program that gives you total access to all of your services settings, and much more.  I highly recommend it, especially if your are using apache. Once installed, you access it with a browser at [https://localhost:10000](https://localhost:10000).

---

### Post by ubnewbie2 on 2010-06-28
> **Detonate said:**
> The program "webmin" is a very complete program that gives you total access to all of your services settings, and much more.  I highly recommend it, especially if your are using apache. Once installed, you access it with a browser at [https://localhost:10000](https://localhost:10000).

I remember that one from a while back.  I think I might try it.  Might be interesting using it to restart Apache which it is running on :)

I can't believe no-one remembers the built-in app that Ubuntu used to have though.  Strange.

---

### Post by Detonate on 2010-06-28
If you have not used webmin in awhile, the latest version has a much nicer interface and provides a lot more functions and information than the old version.

---

### Post by ubnewbie2 on 2010-06-29
> **Detonate said:**
> If you have not used webmin in awhile, the latest version has a much nicer interface and provides a lot more functions and information than the old version.

It certainly is.  Thanks for the tip.

---

