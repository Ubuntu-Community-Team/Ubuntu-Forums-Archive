---
title: "Support for GNOME in Server release"
date: 2010-02-02
forum: General Help
---

### Post by leandromartinez98 on 2010-02-02
If I install a server edition and after that I install Gnome and
all other ubuntu-desktop applications on that server. Will these
applications be supported through the whole server support time? 

In other words, what exactly does it mean that the server is 
supported for longer? Is the number or applications available
to the server smaller than to the desktop? 

Or, similarly, could I build a Server-long supported desktop
by hand?

---

### Post by jamesisin on 2010-02-02
At that point, why not just install the Desktop version?  I did that for a server here.

---

### Post by leandromartinez98 on 2010-02-03
Well, because of the longer release support.

---

### Post by gmargo on 2010-02-03
The server and desktop editions are supported for the same length of time.  Certain releases are designated "LTS" or Long-Term-Support, and these are supported for a longer time than intermediate releases.

The most recent LTS is 8.04 "Hardy Heron".  The next LTS is 10.04 "Lucid Lynx", which is in alpha release now and will be released in April 2010.

No matter which edition, server or desktop, you install, there is nothing to prevent you from running desktop tools like Gnome.  The difference between server and desktop is only a) a slightly differently configured kernel, and b) a different set of packages installed by default.

---

### Post by leandromartinez98 on 2010-02-03
I thought they were different. Indeed, from here:

- Ubuntu Desktop will receive a 3 years support, Ubuntu Server will be supported for 5 years. 



[https://help.ubuntu.com/community/ServerFaq#What%27s%20the%20difference%20between%20desktop%20and%20server?](https://help.ubuntu.com/community/ServerFaq#What%27s%20the%20difference%20between%20desktop%20and%20server?)

and here:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle](http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle)

True, the difference is only for the LTS versions. 3 years for the Desktop and 5 for the Server.

So, can I have a 5-year supported desktop by installing the desktop applications in my LTS-Server release?

---

### Post by jamesisin on 2010-02-03
Adding applications does not change the support arrangement as far as I know.  But consider what this support consists of, namely updates.  Will you really want to run this same version four years from now?

---

### Post by Iowan on 2010-02-03
> **jamesisin said:**
>  But consider what this support consists of, namely updates. I suspect that's the key- updates for the non-server components will (probably?) cease after 3 years.

---

### Post by bodhi.zazen on 2010-02-03
Linux is not windows, so unlike windows where there are specific server versions and specific desktop versions Linux is organized at the application level.

With a LTS, server applications , such as Apache or Samba, are supported for 5 years and desktop apps like gnome are supported for 5 years.

So , after 3 years, you would have security updates for your server apps, but not yoru desktop apps.

I do not know of the exact list of maintained applications.

A better question is, why do you feel you need Gnome on a Server ? For the most part you will use gedit and a terminal.

If you want a gui interface for your server, try something like webmin or phpmyadmin or what not.

---

### Post by leandromartinez98 on 2010-02-03
No, I don't want a server with gnome. I want a desktop supported for several years. Believe me or not, some user I know don't need anything else than what was available back on hardy, and they are using hardy still. Being forced to change after 3 years to Lucid because of the end of security fixes will be just a waste of time. That's why I was wondering if I could install them the Lucid-server version and put the desktop applications on it so I can delay the new reinstallation cycle for 5 years now.

Other distributions, as CentOS, are fully supported for seven years. I have seen this being useful in similar environments.

Anyway, it was more a curiosity, I think the point is that list of server versus desktop applications. If such a list exists, I would like to find it.

---

### Post by bodhi.zazen on 2010-02-03
Sounds like Centos may be the way to go then if long term support of a desktop if you goal. 3 years is fairly generous as desktops go.

---

### Post by mk1w86 on 2010-02-04
You could have a look at Debian, although they don't have fixed release and support cycles their stable release if often supported for a few years.  You could install the current testing release (Squeeze) and keep running it when it becomes stable and eventually old stable which would give you a supported distro for a long time without major upgrades. ;)

I think however CentOS is still the distro that will be supported longest if you're happy with a RPM system.

---

