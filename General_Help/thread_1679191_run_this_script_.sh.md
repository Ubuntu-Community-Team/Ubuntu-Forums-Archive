---
title: "run this script .sh"
date: 2011-01-31
forum: General Help
---

### Post by yae7 on 2011-01-31
Hi:

How i can run this script  remove-orphans.sh ?

[http://lubuntu.net/blog/lubuntu-screencast-cleanup-your-system](http://lubuntu.net/blog/lubuntu-screencast-cleanup-your-system)

I have tried the next thing, but displays an error;

> usuari@pc:~$ sh /home/usuari/Descargas/remove-orphans.sh
[COLOR="Red"]Error: You must be root to run this script![/COLOR]

thanks in advance

---

### Post by TeoBigusGeekus on 2011-01-31
Try
```
sudo sh /home/usuari/Descargas/remove-orphans.sh
```

---

### Post by yae7 on 2011-02-01
yes, i tried this, but i have not seen any result. 

Now I dont know if not runs this instruction or script is incorrect

script:


#/bin/sh
if test $(id -u) != 0; then
 echo Error: You must be root to run this script!
 exit 1
fi
RC="$(COLUMNS=200 dpkg -l|grep ^rc|awk '{print $2}')"
[ "$RC" ] && dpkg --purge $RC

---

### Post by TeoBigusGeekus on 2011-02-01
Could you give us the exact command you give and the exact message you get from terminal, along with the exact script content you're trying to execute?

---

### Post by slooksterpsv on 2011-02-01
> **yae7 said:**
> yes, i tried this, but i have not seen any result. 

Now I dont know if not runs this instruction or script is incorrect

script:


#/bin/sh
if test $(id -u) != 0; then
 echo Error: You must be root to run this script!
 exit 1
fi
RC="$(COLUMNS=200 dpkg -l|grep ^rc|awk '{print $2}')"
[ "$RC" ] && dpkg --purge $RC

It won't output anything. The script does it all in the background.

RC is a variable that is holding the packages it needs to remove/purge. [ "$RC" ] - lists each item store in $RC - on mine when I run, echo [ "$RC" ] - it gives me
```

[ claws-mail
libbrasero-media0
libchamplain-0.4-0
libchamplain-gtk-0.4-0
libept0
libetpan13
libgraphviz4
libobasis3.3-base
libobasis3.3-calc
libobasis3.3-core02
libobasis3.3-draw
libobasis3.3-impress
libobasis3.3-math
libobasis3.3-writer
librapi2
libreoffice-debian-menus
libreoffice3-dict-en
libreoffice3-dict-es
libreoffice3-dict-fr
libruby1.8
libsynce0
odbcinst1debian1
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-writer
picasa
popularity-contest
ruby1.8
songbird
spamassassin ]

```

So then for all those items it'll purge it from dpkg cache.

---

### Post by yae7 on 2011-02-01
Hi:

correct. output anything.

in my case, when I run, echo [ "$RC" ] - it gives me anything:
[ ]

but this script not remove inside  /var/cache/apt/archives ?

because this folder is full....

How i can remove temporal and cache files? like a windows  (remove temporal files)

---

### Post by slooksterpsv on 2011-02-01
Technically it should be:
["$RC"] | dpkg --purge $RC

not:
["$RC"] && dpkg --purge $RC

---

