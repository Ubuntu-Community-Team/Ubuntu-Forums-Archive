---
title: "Internet no longer working with new kernel 2.6.32-23"
date: 2010-07-01
forum: General Help
---

### Post by Blackie Lawless on 2010-07-01
Hi,
upgraded from 2.6.32-22 to 2.6.32-23 through update manager this morning.

However, with the new kernel, it appears my wired network adapter is no more working! Lucky you still can boot up in 2.6.32-22 then ;)

Computer: Dell Inspiron 6400 anno 2007. (laptop)

Anyone else had this trouble?

---

### Post by dino99 on 2010-07-01
i'm more lucky: i've not a del :lolflag:

---

### Post by chewit on 2010-07-01
Nope, everything seems fine.

Just rollback to the old kernel for every boot.

Report the bug in Launchpad, and it may get fixed in another kernel release.

---

### Post by Blackie Lawless on 2010-07-01
> **chewit said:**
> ...
Report the bug in Launchpad, and it may get fixed in another kernel release.

What and where is Launchpad? :confused:

---

### Post by dino99 on 2010-07-01
ask your mom about google :lolflag:

---

### Post by Blackie Lawless on 2010-07-01
> **dino99 said:**
> ask your mom about google :lolflag:
I googled launchpad and got a picture of a giant rocket...

---

### Post by Sanjeevtrip on 2010-07-01
boot with old kernel type

```


/sbin/ifconfig 


```

see if eth0 appears, if yes then your new kernel boot it might not loading the card

then boot with new kernel and type

```

sudo /etc/init.d/networking restart

```

see if it comes up

---

### Post by Blackie Lawless on 2010-07-01
Thanks boys and girls. Now it works without me doin' none. A nice morning with Linux I've had indeed;)

:guitar:

---

### Post by Blackie Lawless on 2010-07-02
Update..
This morning the network once again failed on first boot. Worked after first booting up in 2.6.32.22 and then in 2.6.32.23 though.

---

### Post by McRat on 2010-07-03
It affects Realtek ethernet chipsets.  It's not just the internet, it will cripple a LAN as well.  I'm typing from a Mac because of it.

---

