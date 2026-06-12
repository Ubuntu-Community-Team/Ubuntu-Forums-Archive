---
title: "Command line file manager that doesn't require x-window"
date: 2010-02-08
forum: General Help
---

### Post by garethsimpsonuk on 2010-02-08
Hi all,

I have just asked my hosting company to install midnight commander on my web server as they do not allow root access. The answer they gave me was that they are not prepared to install midnight commander because it depends on the 'x-window' package. This is totally understandable and I was wondering if there is an alternative to mc that doesn't require this dependancy.

Please note that the VPS is running Red Hat, not Ubuntu but this is the place I always come for my linux needs!

Thanks

---

### Post by undecim on 2010-02-08
The command line itself makes an excellent file manager. Take a look at [http://gd.tuwien.ac.at/linuxcommand.org/lts0050.html](http://gd.tuwien.ac.at/linuxcommand.org/lts0050.html) for details on that.

I also found this page from a Google search: [http://freshmeat.net/search/?q=%2Bfile+%2Bmanager+%2Bconsole&section=projects&Go.x=0&Go.y=0](http://freshmeat.net/search/?q=%2Bfile+%2Bmanager+%2Bconsole&section=projects&Go.x=0&Go.y=0)

---

### Post by BOFH+ on 2010-02-08
Vifm. It's based on ncurses.

Screenshot here: [http://vifm.sourceforge.net](http://vifm.sourceforge.net)

---

### Post by etnlIcarus on 2010-02-08
MC most certainly should not require the x-windowing system. Someone fudged the dep flags.

That said, the basic CLI tools like ls, cd, mv, cp, rm, mkdir, touch, chmod, chown and grep should cover most of your needs and are amongst the easiest CLI tools to use. Shouldn't take you any more time to become comfortable with them, than it would mc. It'll also be a hell of a lot more efficient, if you can't get mouse support in mc.

---

### Post by Arand on 2010-02-08
At least on ubuntu, the sole dependencies of MC are:
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.16.0), libgpm2 (>= 1.20.4), libslang2 (>= 2.0.7-1
So no X-window..
- Arand

---

### Post by garethsimpsonuk on 2010-02-09
Thank you for the replies guys. Yes obviously it's good to get to know these commands but I also feel having tools such as mc can really help in some situations. In the end I installed Clesk which is a basic file manager but after you guys have higlighted the fact that mc does not require that package I am going to let them know. Hopefully they will install it for me.

Obviously the RHEL system is flagging up the missing dependencies, is it possible to force install without this package?

Thanks for the help

---

### Post by garethsimpsonuk on 2010-02-09
Just to let you know, they have installed MC. Thanks for the help guys :)

---

