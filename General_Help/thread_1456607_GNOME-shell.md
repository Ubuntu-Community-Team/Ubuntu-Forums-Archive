---
title: "GNOME-shell"
date: 2010-04-17
forum: General Help
---

### Post by thedoctor81877 on 2010-04-17
I just upgraded to beta 10.04, & am trying to get GNOME-shell installed. I have downloaded the tar file for it, but when I do ./configure in a terminal, I get the following error messages:
No package 'mutter-plugins' found
No package 'gjs-gi-1.0' found
No package 'gobject-introspection-1.0' found

Any help would be appreciated.

-Michael (the Doctor)

---

### Post by thedoctor81877 on 2010-04-17
BTW, when I simply try: sudo apt-get install gnome-shell, I get the following:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages

-Michael

---

### Post by mediumcool on 2010-04-17
Try this thread - first page:

[http://ubuntuforums.org/showthread.php?t=1305154&highlight=gnome+shell]("http://ubuntuforums.org/showthread.php?t=1305154&highlight=gnome+shell")

---

### Post by thedoctor81877 on 2010-04-17
When I get to step #5, for jhbuild build, I get the following error message in the terminal:


jhbuild: could not load config file, /home/thedoctor/.jhbuildrc is missing


-Michael

---

### Post by mediumcool on 2010-04-17
I usually just follow steps 1, 2, 3 and 5 and it works!

If you aren't getting any errors from running /bin/bash gnome-shell-build-setup.sh, I don't know why you don't have the .jhbuildrc.

Run /bin/bash gnome-shell-build-setup.sh again if you don't get any errors, try the jhbuild command again.

You are best off using the main thread I linked to above for help on this - firstly it is in the Lucid forum and secondly you are more likely to get noticed by someone who can help you further (that thread is pretty high volume).

Cheers,
Sean

---

### Post by jaco223 on 2010-04-17
> **thedoctor81877 said:**
> I just upgraded to beta 10.04, & am trying to get GNOME-shell installed. I have downloaded the tar file for it, but when I do ./configure in a terminal, I get the following error messages:
No package 'mutter-plugins' found
No package 'gjs-gi-1.0' found
No package 'gobject-introspection-1.0' found

Any help would be appreciated.

-Michael (the Doctor)


Open a terminal and type the following:

```
$ sudo add-apt-repository ppa:ricotz/testing
$ sudo apt-get update
$ sudo apt-get install gnome-shell
```That will install Gnome shell for you, no need to build it.

Hope this helps.

Jaco

---

### Post by thedoctor81877 on 2010-04-17
Hullo Sean,

When I try running the command you suggested, I get:

no such file or directory

-Michael

---

### Post by jaco223 on 2010-04-17
> **thedoctor81877 said:**
> BTW, when I simply try: sudo apt-get install gnome-shell, I get the following:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages

-Michael

Did you add the repository before trying to install Gnome shell?

---

### Post by thedoctor81877 on 2010-04-17
Jaco,

The 3 commands you sent me seemed to me to work correctly [that is they did not cause any error messages], but now how do I actually run the GNOME-shell???
-Michael

Thanks.

---

### Post by kouter on 2010-04-17
Either in terminal or by pressing Alt+F2 enter

```
gnome-shell --replace
```

---

### Post by jaco223 on 2010-04-17
+1 As Kouter said. I like Gnome-shell, but for me on my system it is too buggy.
Good luck with it!

Jaco

---

### Post by thedoctor81877 on 2010-04-17
Now, I get the following:

(mutter:3375): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (/usr/lib/libgjs-gi.so.0: undefined symbol: g_struct_info_is_foreign)]
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
Window manager warning: Log level 8: mutter_window_mapped: assertion `!priv->mapped' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x52013ef (thedoctor@)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


-Michael

---

### Post by mediumcool on 2010-04-17
To download the gnome-shell-build-setup.sh make sure you use 

curl -O [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)

The link is truncated in the other thread.

---

### Post by mediumcool on 2010-04-17
ok, that is truncated too!  Copy the link by right clicking it and selecting copy link location and pasting it after curl -O.

---

### Post by thedoctor81877 on 2010-04-17
Should there be any space between the 'curl-O' and the http, b/c when I just tied that I got that: 

curl-O : command not found

-Michael

Thanks

---

### Post by mediumcool on 2010-04-17
the command is curl, then a space, the option is -O and then a space and the url :

curl -O <url>

---

### Post by thedoctor81877 on 2010-04-18
OK, that seemed to work, but now how do I start the shell?

---

### Post by mediumcool on 2010-04-18
./gnome-shell/source/gnome-shell/src/gnome-shell --replace

---

### Post by thedoctor81877 on 2010-04-18
When I try that in the terminal, I get:

no such file or directory

-Michael

---

### Post by mediumcool on 2010-04-18
did you run 

/bin/bash gnome-shell-build-setup.sh

and

jhbuild build

after running the curl command?

---

### Post by thedoctor81877 on 2010-04-20
Thanks for all your help, that did finally work.

-the Doctor (Michael)

---

