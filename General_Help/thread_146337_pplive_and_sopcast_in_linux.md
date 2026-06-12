---
title: "pplive and sopcast in linux"
date: 2006-03-18
forum: General Help
---

### Post by mitjab on 2006-03-18
I would like to kow if is possible how to use pplive or sopcast program in linux for vide. I am searching for that answer for very long time but i can't find it.

---

### Post by pulp on 2006-03-18
well, at least for sopcast there is a GTK frontend. Get it here: [http://lianwei3.googlepages.com/home2](http://lianwei3.googlepages.com/home2)

Then you might want to try [http://www.peercast.org](http://www.peercast.org) with several Gnome frontends available. One of them is in the Backports

---

### Post by mitjab on 2006-03-18
i try sopcast but i get this error

```

gcc -O2  `pkg-config --cflags gtk+-2.0`  -c callbacks.c -o callbacks.o
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from callbacks.c:22:
header.h:23:21: error: gtk/gtk.h: No such file or directory
In file included from callbacks.c:22:
header.h:56: error: syntax error before &#8216;*&#8217; token
header.h:56: warning: data definition has no type or storage class
header.h:57: error: syntax error before &#8216;*&#8217; token
header.h:57: warning: data definition has no type or storage class
header.h:58: error: syntax error before &#8216;*&#8217; token
header.h:58: warning: data definition has no type or storage class
header.h:59: error: syntax error before &#8216;*&#8217; token
header.h:59: warning: data definition has no type or storage class
header.h:60: error: syntax error before &#8216;*&#8217; token
header.h:60: warning: data definition has no type or storage class
header.h:61: error: syntax error before &#8216;*&#8217; token
header.h:61: warning: data definition has no type or storage class
callbacks.c:25: error: syntax error before &#8216;*&#8217; token
callbacks.c: In function &#8216;on_clist_channel_select_row&#8217;:
callbacks.c:30: error: &#8216;event&#8217; undeclared (first use in this function)
callbacks.c:30: error: (Each undeclared identifier is reported only once
callbacks.c:30: error: for each function it appears in.)
callbacks.c:30: error: &#8216;GDK_2BUTTON_PRESS&#8217; undeclared (first use in this functio n)
callbacks.c:35: error: &#8216;row&#8217; undeclared (first use in this function)
callbacks.c:37: error: &#8216;clist&#8217; undeclared (first use in this function)
callbacks.c: In function &#8216;on_button_sopcast_clicked&#8217;:
callbacks.c:57: error: invalid type argument of &#8216;->&#8217;
callbacks.c: At top level:
callbacks.c:85: error: syntax error before &#8216;*&#8217; token
callbacks.c: In function &#8216;on_button_channel_toggled&#8217;:
callbacks.c:87: error: &#8216;widget&#8217; undeclared (first use in this function)
callbacks.c:87: error: invalid type argument of &#8216;->&#8217;
callbacks.c:89: error: invalid type argument of &#8216;->&#8217;
callbacks.c:90: error: &#8216;TRUE&#8217; undeclared (first use in this function)
callbacks.c: At top level:
callbacks.c:128: error: syntax error before &#8216;*&#8217; token
callbacks.c: In function &#8216;on_adj_sound_change_value&#8217;:
callbacks.c:130: error: &#8216;adj&#8217; undeclared (first use in this function)
callbacks.c: In function &#8216;on_button_save_clicked&#8217;:
callbacks.c:155: error: syntax error before &#8216;*&#8217; token
callbacks.c:156: error: &#8216;line&#8217; undeclared (first use in this function)
callbacks.c: At top level:
callbacks.c:179: error: syntax error before &#8216;*&#8217; token
callbacks.c: In function &#8216;on_button_record_clicked&#8217;:
callbacks.c:182: error: &#8216;widget&#8217; undeclared (first use in this function)
callbacks.c:182: warning: passing argument 1 of &#8216;strlen&#8217; makes pointer from inte ger without a cast
callbacks.c:182: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:182: warning: passing argument 1 of &#8216;strlen&#8217; makes pointer from inte ger without a cast
callbacks.c:182: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:182: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:182: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:187: warning: passing argument 1 of &#8216;strlen&#8217; makes pointer from inte ger without a cast
callbacks.c:187: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:187: warning: passing argument 1 of &#8216;strlen&#8217; makes pointer from inte ger without a cast
callbacks.c:187: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:187: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
callbacks.c:187: warning: passing argument 1 of &#8216;__builtin_strcmp&#8217; makes pointer  from integer without a cast
make: *** [callbacks.o] Error 1

```


or if i try sp-sc i get
```

mitjab@ubuntu:~/Desktop$ ./sp-sc
./sp-sc [-u username:password] <sop:url> <localport> <playerport>

```

---

### Post by pulp on 2006-03-19
You need **libgtk2.0-dev** and **build-essential** from the repositories, if you want to build the program

---

### Post by ryukent on 2008-02-21
For sopcast in Ubuntu see this post:

[http://sopcast.pxn.ca/viewtopic.php?f=17&t=203]("http://sopcast.pxn.ca/viewtopic.php?f=17&t=203")

---

