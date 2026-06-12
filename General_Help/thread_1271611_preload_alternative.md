---
title: "preload alternative"
date: 2009-09-21
forum: General Help
---

### Post by J V on 2009-09-21
I read about the method to add open office to the startup list with an extra "-nodefault -nologo" to make it start up much faster, is there a built into ubuntu way to do this for other programs (mainly FF/Gimp) or do I have to install preloader?

---

### Post by J V on 2009-09-21
bump

---

### Post by mike555 on 2009-09-21
I use Preloader and it seams to help .........

---

### Post by J V on 2009-09-21
Well yes but I would like to control *which* apps are preloaded...

The openoffice command is a good example, is that possible with say FF? Pidgin? Gimp?

---

### Post by J V on 2009-09-21
bump

---

### Post by conorsulli on 2009-12-01
+1

---

### Post by Jive Turkey on 2009-12-01
You can access some config options for FF by typing "about:config" in the address bar, some of which could be tweaked for better performance.  There is no splash afaik on FF to slow down loading.  You might get better startup time by making the homepage of your browser "about:blank" so you don't have to load a page at every startup too.

For whatever app you want to load, you can see the options in most cases by typing <appname> --help

doing this for gimp I found it has a few options like "--no-data --no-splash --no-fonts" that might make it start faster for you.  Keep in mind that these options, aside from no-splash also reduce the functionality.

---

