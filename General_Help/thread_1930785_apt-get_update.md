---
title: "apt-get update"
date: 2012-02-24
forum: General Help
---

### Post by Hetepeperfan on 2012-02-24
Hello 

I'vegot a minor problem with apt-get if run 

```
$ sudo apt-get update
```I see the command run as usual exept for the part in the tail.:

```
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```apt-get tell me to run apt-get update again, but then I get in to a recursive problem...

Does anyone knows what might be wrong and how to fix this.

any help is appreciated kind regards.

Maarten

---

### Post by cortman on 2012-02-24
There's a duplicate line in your sources.list file. Run the following in a terminal:

```
gksu gedit /etc/apt/sources.list
```

and find two the identical lines in the file (according to the error, it's two

```
deb http://archive.canonical.com/ lucid/partner Packages
```

lines. Delete one, save, and run


```
sudo apt-get update
```

---

### Post by Hetepeperfan on 2012-02-24
Thanks Cortman,

I found a set of

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

once one was removed the problem was removed as well

thanks.

---

