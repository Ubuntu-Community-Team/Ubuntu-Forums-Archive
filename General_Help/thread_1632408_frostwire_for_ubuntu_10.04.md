---
title: "frostwire for ubuntu 10.04"
date: 2010-11-27
forum: General Help
---

### Post by dr13 on 2010-11-27
Hi Guys
i am having a problem downloading frostwire. i am downloading from frostwire.com file frostwire-4.21.1.i586.deb and the following error message comes up

/tmp/frostwire-4.21.1.i586-1.deb could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.

the process above doesnt seem to work for me. i am not to clued up on all this so if someone could assist by giving me a step by step run down of what i should be doing i would really appreciate it

thanks

---

### Post by ctdesing on 2010-11-27
hi, try in terminal Applications>Accessories>Terminal ```
sudo dpkg -i /tmp/frostwire-4.21.1.i586-1.deb
```

---

### Post by ctdesing on 2010-11-27
maybe it is corrupted, try downloading again, try this way in terminal Applications>Accessories>Terminal ```
wget http://newyork1.frostwire.com/frostwire/4.21.1/frostwire-4.21.1.i586.deb
``` then ```
sudo dpkg -i frostwire-4.21.1.i586.deb
```

---

### Post by dr13 on 2010-11-29
thank you ctdesing

you are the man

---

### Post by Yellow Pasque on 2010-11-30
Or use gtk-gnutella: [http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html)
It's a native Linux gnutella client.

---

