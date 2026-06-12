---
title: "Problems with Java WebStart in 11.04"
date: 2011-06-07
forum: General Help
---

### Post by DMJ on 2011-06-07
I'm trying run NASA WorldWind Java demos with Java WebStart. WorldWind opens just fine, but many layers are missing. I can see the atmosphere outline of the earth but the earth itself is transparent. This is on an ACER 1410 laptop with Natty 32-bit.

I have Natty 64-bit on my desktop and it runs just fine. However, if I try to run it from the command line I get fatal errors. On my 32-bit machine I get no errors on the command line, but the layers are still missing. 

I tried running it under Windows 7 on my laptop, to see if it may be the video adapter, but it works just fine. 

I tried installing the JOGL packages from the repos, but no change.

I installed WorldWind from the repos and it runs fine, but a little slow. Seems identical to the demo, so it must have something to do with javaws.

---

### Post by linuxinstalledfromhdd on 2011-06-07
Did you install all of the plugins you needed identically on both versions of Ubuntu? 

Check out:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Maybe you missed a plugin or something? :guitar:

---

### Post by DMJ on 2011-06-08
> **linuxinstalledfromhdd said:**
> Did you install all of the plugins you needed identically on both versions of Ubuntu? 

Check out:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Maybe you missed a plugin or something? :guitar:

Thanks for the reply. That's a pretty long list of stuff on that link, most of which depends highly on user preference. I have installed the Java browser plugin on both systems. I installed the Sun plugin and removed the Iced-tea plugin. However, this shouldn't matter as the webstart app runs independent of the browser. 

I tried installing Openjdk run-time on my laptop, because it's installed on my desktop. I'm not sure why it wasn't installed by default on my laptop. Running the demos with the Icedtea webstart produced identical results. The only difference was that it automatically downloaded the JOGL bindings when starting the app, but this didn't change the result. it actually downloaded the same stuff as running the Sun WS from the command line on my desktop, but without the fatal errors. Funny that the machine that gets errors is the only one that works. I guess its true what they say about Java: write once, debug everywhere.

---

