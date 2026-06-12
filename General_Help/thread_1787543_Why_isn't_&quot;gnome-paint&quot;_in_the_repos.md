---
title: "Why isn't &quot;gnome-paint&quot; in the repos?"
date: 2011-06-21
forum: General Help
---

### Post by nrundy on 2011-06-21
I've been using Gpaint but am less than thrilled with it. I would much rather use gnome-paint.

Anybody know why this GPL software is not in the repos? At least, I can't find it with Lucid 10.04.

---

### Post by haqking on 2011-06-21
> **nrundy said:**
> I've been using Gpaint but am less than thrilled with it. I would much rather use gnome-paint.

Anybody know why this GPL software is not in the repos? At least, I can't find it with Lucid 10.04.


its in mine, depends on your sources.list i imagine

---

### Post by Frogs Hair on 2011-06-21
I see Gnome Paint and GNU Paint with no special repositories activated .

---

### Post by pqwoerituytrueiwoq on 2011-06-21
no problem here

---

### Post by nrundy on 2011-06-21
wtf!

I tried synaptic, terminal apt-get, and USC. I haven't disabled any of the default repos.

---

### Post by nrundy on 2011-06-21
> **pqwoerituytrueiwoq said:**
> no problem here

Oh, wait! that picture you posted is NOT Gnome-paint. It is Gpaint. There's a difference.

Are you sure you guys are not confusing Gpaint with gnome-paint? they're not the same.

---

### Post by pqwoerituytrueiwoq on 2011-06-21
did some googleing
[http://launchpad.net/gnome-paint/trunk/0.4.0/+download/gnome-paint_0.4.0-1_i386.deb](http://launchpad.net/gnome-paint/trunk/0.4.0/+download/gnome-paint_0.4.0-1_i386.deb)
there is no 64 bit deb but there is a 64bit rpm guess it is time to use alien
[https://launchpad.net/gnome-paint/+download](https://launchpad.net/gnome-paint/+download)

---

### Post by sanderd17 on 2011-06-21
It's quite new, so it isn't in 10.04, but I have it in 11.04:

```

$ aptitude show gnome-paint
Pakket: gnome-paint                              
Staat: niet geïnstalleerd
Versie: 0.4.0-2
Prioriteit: optioneel
Sectie: universe/graphics
Beheerder: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Ongecomprimeerde grootte: 852 k
Hangt af van: libc6 (>= 2.7), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>=
              2.22.0), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.18.0),
              libx11-6
Beschrijving: simple, easy to use paint program for GNOME
 gnome-paint is a program inspired by MS Paint and designed for GNOME (and maybe
 other) desktop environment. It could be used to manipulate images in a very
 simple way. With a very friendly user interface, gnome-paint is easy to get
 started for new users.
Homepage: http://launchpad.net/gnome-paint/

```

---

### Post by haqking on 2011-06-21
> **nrundy said:**
> Oh, wait! that picture you posted is NOT Gnome-paint. It is Gpaint. There's a difference.

Are you sure you guys are not confusing Gpaint with gnome-paint? they're not the same.

I am not confusing either, see my attachment, i run 10.10 and it is in there, i opened a 10.04 virtual machine and it is in there aswell.

---

### Post by haqking on 2011-06-21
I know it doesnt solve why it aint in your repos but you can get it here as a package.

[https://launchpad.net/gnome-paint](https://launchpad.net/gnome-paint)

---

### Post by nrundy on 2011-06-21
Thanks guys. I didn't realize gnome-paint was that new. Guess I'll have to wait till I update from Lucid to use it.

---

### Post by pqwoerituytrueiwoq on 2011-06-21
> **haqking said:**
> I know it doesnt solve why it aint in your repos but you can get it here as a package.

[https://launchpad.net/gnome-paint](https://launchpad.net/gnome-paint)
my money is on your virtual machine is 32 bit verses there mine and his are 64bit

---

### Post by Elfy on 2011-06-21
[http://packages.ubuntu.com/search?keywords=gnome-paint&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=gnome-paint&suite=default&section=all&arch=any&searchon=names)

Maverick onwards apparently.

---

### Post by haqking on 2011-06-21
> **pqwoerituytrueiwoq said:**
> my money is on your virtual machine is 32 bit verses there mine and his are 64bit


ahh yeah good point, i run x64 host 10.10 but yeah my VM's are 32 bit for the most part.

well said ;-)

---

### Post by haqking on 2011-06-21
> **nrundy said:**
> Thanks guys. I didn't realize gnome-paint was that new. Guess I'll have to wait till I update from Lucid to use it.


Just down load the package yourself

---

