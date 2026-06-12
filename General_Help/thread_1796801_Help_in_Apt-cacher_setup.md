---
title: "Help in Apt-cacher setup"
date: 2011-07-04
forum: General Help
---

### Post by karthick87 on 2011-07-04
I have setup -ed apt-cacher server. But when i install packages in clients i get the following error. Can someone sort out pls..


[IMG]http://i.imgur.com/MLkgC.png[/IMG]

---

### Post by mikejonesey on 2011-07-04
your mirror is down change it in /etc/sources n run apt-get update

172.29.32.9 looks like 3rd party posibliy? just remove that from sources.list n apt-get update

---

### Post by karthick87 on 2011-07-04
Dude thats my apt-cacher server ip, what's wrong with that? I dont guess that's wrong..

---

### Post by mikejonesey on 2011-07-04
lol well it returns a 404 which is the prob, maybee if it's only to server on local it's a firewall prob?...

---

### Post by karthick87 on 2011-07-04
How to verify it?

---

### Post by karthick87 on 2011-07-05
Bump for a move..

---

### Post by karthick87 on 2011-07-08
Final bump :)

---

### Post by gmargo on 2011-07-08
I suspect your problem is due to improperly specifying the apt proxy.

Do not edit your **/etc/apt/sources.list** file.

Instead, add an **/etc/apt/apt.conf** file (or a file under /etc/apt/apt.conf.d/) with this content, appropriately substituted:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```Personally, I define an extra host entry "apthost" to point to the server where apt-cacher-ng is running.  So my apt.conf file looks like:
```

Acquire::http::Proxy "http://apthost:3142/";

```[B]
apt-cacher[/B] is quite crude. Use **apt-cacher-ng** instead.

---

### Post by karthick87 on 2011-07-08
> **gmargo said:**
> I suspect your problem is due to improperly specifying the apt proxy.

Do not edit your **/etc/apt/sources.list** file.

Instead, add an **/etc/apt/apt.conf** file (or a file under /etc/apt/apt.conf.d/) with this content, appropriately substituted:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```Personally, I define an extra host entry "apthost" to point to the server where apt-cacher-ng is running.  So my apt.conf file looks like:
```

Acquire::http::Proxy "http://apthost:3142/";

```[B]
apt-cacher[/B] is quite crude. Use **apt-cacher-ng** instead.

Thanks for the update gmargo :) will go through it and let you know the results.

---

