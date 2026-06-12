---
title: "GLib not found"
date: 2006-01-28
forum: General Help
---

### Post by SilverTab on 2006-01-28
Im trying to install a xmms plugin and I get the following error at ./configure:


```

checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```


I installed GCC and G++...not sure what more I need to be able to compile this?

---

### Post by public_void on 2006-01-28
Check if have glib packages installed. I'd get libglib2.0-0 and libglib2.0-0-dev packages. 

Just do 

```
sudo apt-get install libglib2.0-0, libglib2.0-0-dev
```

or go through Synaptic.

---

### Post by jrib on 2006-01-28
[QUOTE=SilverTab]Im trying to install a xmms plugin and I get the following error at ./configure:


```

checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```


I installed GCC and G++...not sure what more I need to be able to compile this?[/QUOTE]

```
sudo apt-get install build-essential
```
 
should give you everything you need

---

### Post by meemoo on 2008-02-17
you might find that you need to install libgtk1.2-dev this was what i had to do and i had all the suggested packages installed already

```
sudo apt-get install libgtk1.2-dev 
```

---

### Post by sycroft on 2008-05-08
the above "sudo apt-get install libgtk1.2-dev" worked for me.

thx

---

