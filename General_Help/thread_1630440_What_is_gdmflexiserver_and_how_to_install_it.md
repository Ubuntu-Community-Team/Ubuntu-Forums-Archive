---
title: "What is gdmflexiserver and how to install it?"
date: 2010-11-25
forum: General Help
---

### Post by karthick87 on 2010-11-25
I have heard that **gdmflexiserver** allows fast user switching on gnome.Can someone explain me abt **gdmflexiserver**?Also say me how to install it in ubuntu 10.04.

---

### Post by pawhtiobo on 2010-11-25
Hi :)

I don't know much about that, but...

Check this out:

[http://manpages.ubuntu.com/manpages/hardy/man1/gdmflexiserver.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/gdmflexiserver.1.html)

[http://www.cims.nyu.edu/cgi-comment/man.cgi?section=1&topic=gdmflexiserver](http://www.cims.nyu.edu/cgi-comment/man.cgi?section=1&topic=gdmflexiserver)



See ya..

---

### Post by srikanthganta on 2012-12-23
$gdmflexiserver  (gdm=gnome display manager)
the above command is working by default,but i guess it is depricated in latest Ubutu versions.Try below..

    $dm-tool --help       
    $dm-tool switch-to-greeter
    $dm-tool  switch-to-guest
    $dm-tool  switch-to-user XYZ

---

