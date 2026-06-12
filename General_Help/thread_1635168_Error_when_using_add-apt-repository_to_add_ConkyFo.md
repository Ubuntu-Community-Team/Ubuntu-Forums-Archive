---
title: "Error when using add-apt-repository to add ConkyForecast"
date: 2010-12-01
forum: General Help
---

### Post by fhsm on 2010-12-01
I wanted to install the Conky Hardcore PPA so I did: ```
sudo add-apt-repository ppa:conkyhardcore/ppa
```.

Everything seemed to work until I ran update at which point I got a 404.

After a bit of looking I found that [I]/etc/apt/sources.list.d/conky-hardcore-ppa-maverick.list
[/I] had the following:
```

deb http://ppa.launchpad.net/conky-hardcore/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/conky-hardcore/ppa/ubuntu maverick main

```

When I changed that to 
```
deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu maverick main

``` I was able to update without a problem.

When I ran update the next time I got a duplication error at which point I found that [I]/etc/apt/sources.list.d/conkyhardcore-ppa-maverick.list
[/I] had been created. Removing the old file fixed this problem.

Not sure what the story is here. Has anyone else noticed the same thing and if so where should I file the bug?

---

### Post by atvcrazee on 2012-12-20
Just posting for anyone who is still having trouble updating : Quantal and Precise not working for me so had to use Maverick!

---

### Post by oldos2er on 2012-12-20
Old thread closed.

---

