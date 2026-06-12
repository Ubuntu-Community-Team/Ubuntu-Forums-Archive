---
title: "how to configure libraries?"
date: 2006-05-10
forum: General Help
---

### Post by jsmidt on 2006-05-10
I am trying to configure seamokey.  When I do ./configure this is the error I get:

checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


I have libgtk2.0 installed, it seems seamokey's configure file can't see it.

when I type ./configure --help I see:

 --with-gtk-prefix=PFX   Prefix where GTK is installed (optional)


I think I need to run ./configure -- --with-gtk-prefix=PFX   altered to match where libgtk is installed.  

Am I right and does anybody know how to do this?

---

### Post by tonyr on 2006-05-10
I can't answer your question exactly, but I have some guesses.
**--with-gtk-prefix** is probably used if you built GTK yourself
and installed it in some non-standard place.  

I think the configuration defaults for **seamonkey** are not quite right
for Debian based platforms (like Ubuntu). The configure command line I used was
```

./configure --enable-application=suite --enable-default-toolkit=gtk2

```
which worked just fine.  I am using the latest Dapper Drake installation
of Ubuntu, however.

---

### Post by jsmidt on 2006-05-10
I appriciate the advice tonyr, but unfortunatly it din't work, I still get the same error message. :(

---

### Post by tonyr on 2006-05-10
I'm sorry that didn't work.  My impression is that Dapper (6.06) is
signficantly different from Breezy (5.10).
Did you look at Build Documentation and Build Configuration web pages?
[URL="http://developer.mozilla.org/en/docs/Build_Documentation"]
http://developer.mozilla.org/en/docs/Build_Documentation[/URL]
[URL="http://developer.mozilla.org/en/docs/Configuring_Build_Options"]
http://developer.mozilla.org/en/docs/Configuring_Build_Options[/URL]

---

### Post by jsmidt on 2006-05-11
tonyr you were right about what to type.  I found out the problem was I didn't have the -dev files.

---

