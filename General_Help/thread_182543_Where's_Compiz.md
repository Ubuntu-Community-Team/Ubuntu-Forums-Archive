---
title: "Where's Compiz?"
date: 2006-05-26
forum: General Help
---

### Post by blanc11 on 2006-05-26
Hi

I typed in 
```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```

and it said that it could not find compiz. Does anyone know a repository or something I can get it from? Thanks!

---

### Post by bruce89 on 2006-05-26
It's not in Breezy, it's in Dapper only.

---

### Post by ChrisD on 2006-05-26
This is my first post, so hope it will be a useful one.

[QUOTE=blanc11]Hi

I typed in 
```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```

and it said that it could not find compiz. Does anyone know a repository or something I can get it from? Thanks![/QUOTE]

You need to add the repositories to your sources.list, like this (assuming you **are** on Dapper):

```
sudo gedit /etc/apt/sources.list
```

And paste the following in:

```

## Compiz -- Xgl
deb http://www.beerorkid.com/compiz dapper main
deb-src http://www.beerorkid.com/compiz dapper main

```

Then update your list:

```

sudo apt-get update

```

And try installing compiz again.

:)

---

### Post by bruce89 on 2006-05-26
[QUOTE=ChrisD]This is my first post, so hope it will be a useful one.



You need to add the repositories to your sources.list, like this:

```
sudo gedit /etc/apt/sources.list
```

And paste the following in:

```

## Compiz -- Xgl
deb http://www.beerorkid.com/compiz dapper main
deb-src http://www.beerorkid.com/compiz dapper main

```

Then update your list:

```

sudo apt-get update

```

And try installing compiz again.

:)[/QUOTE]
Unfortuantly, that won't work.  (it would on dapper, but this is the Breezy forum).  These packages are compiled for Dapper.  If you want to use compiz you will either have to compile everything yourself, or upgrade to Dapper by doing ```
gksu "update-manager -d"
```
Good first post, shame you didn't realise that this is the breezy forum!

---

### Post by blanc11 on 2006-05-26
I am using breezy.  Sorry, I'm a little new here, can ya tell? Thanks a lot guys! :)

---

