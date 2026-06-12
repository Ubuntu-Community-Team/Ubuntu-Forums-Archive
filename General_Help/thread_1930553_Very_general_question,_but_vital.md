---
title: "Very general question, but vital"
date: 2012-02-23
forum: General Help
---

### Post by SergioQ on 2012-02-23
So my long story short is that my current hosting service cannot install all the modules I need.   Even thought they are all on CPAN.

So I want to turn one of my free (64 bit) machines into a server (for development services.  Someone suggested Ubuntu.

I just need to know this, as someone who is techinically capable, yet totally new to the Unix/Linux world:

Does the free version of Ubuntu have easy to use GUIs that will allow me to add modules from CPAN and administrate MySQL?

Many thanks ahead, 

Signed...   "Lost in Linux land"

---

### Post by HeroOfCanton on 2012-02-24
I have no clue about CPAN. There are, however, a ton of tools for MySQL administration. The most popular is probably phpMyAdmin [http://www.phpmyadmin.net/]("http://www.phpmyadmin.net/home_page/")

If that's not what you are looking for just google "linux mysql gui tools" and you'll find several more including ones that mimic the query browser and admin available in Windows quite well.

That said, do you really want a GUI on your web server? Typically the server is kept as slim as possible with the GUI tools installed to the computers accessing the server for maintenance.

Also, ubuntu is not typically considered the best distro for a server (although it's capable of handling it if needed). It's really targeted towards the desktop world rather than servers. The updates are constant which is not typically a good thing for a live web server. You may want to look into Red Hat (if you're willing to pony up for support), or CentOS if you're not.

Of course, that's just my opinion and it's worth exactly what you paid for it. :)

---

### Post by cariboo on 2012-02-24
> **SergioQ said:**
> So my long story short is that my current hosting service cannot install all the modules I need.   Even thought they are all on CPAN.

So I want to turn one of my free (64 bit) machines into a server (for development services.  Someone suggested Ubuntu.

I just need to know this, as someone who is techinically capable, yet totally new to the Unix/Linux world:

Does the free version of Ubuntu have easy to use GUIs that will allow me to add modules from CPAN and administrate MySQL?

Many thanks ahead, 

Signed...   "Lost in Linux land"

The short answer is no, the server version doesn't come with a gui, and the CPAN interface is also text based.

If you are new to Linux, I'd suggest installing the desktop version of Ubuntu. If you are using Ubuntu as a development system, the desktop version will do everything you need. CPAN on the command line is quite easy to use, as long as you read the messages you get on screen, it is installed by default, all you have to do is open a terminal and type:

```
sudo cpan
```

you need to have system admin permissions, to install the perl modules hence the need for sudo.

---

