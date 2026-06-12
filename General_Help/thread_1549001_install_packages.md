---
title: "install packages"
date: 2010-08-09
forum: General Help
---

### Post by aksx on 2010-08-09
is there a way to schedule an installation when the one being performed ends...
eg.
i gave the command "apt-get install wine" but then i realized that i also neede to install cheese so what can i do that when wine is installed "apt-get install cheese" will be executed....

---

### Post by realzippy on 2010-08-09
```
sudo apt-get install wine cheese bread *aso*
```

installs simultaneously


if you want it to install wine first,then cheese,then bread:

```
sudo apt-get install wine && sudo apt-get install cheese && sudo apt-get install bread *aso*
```

---

### Post by aksx on 2010-08-09
the thing is the first installation has already started nd i am like oh s*** now ill have to wait for it to complete....

---

### Post by realzippy on 2010-08-09
Yep,you will have to wait.Can only run 1 instance of apt-get...

---

### Post by aksx on 2010-08-09
i was thinking of something like the "Ubuntu Software Center" does when a installation is in progress it waits for it to complete and then starts....

---

### Post by snowpine on 2010-08-09
You can interrupt with Ctrl+C. If it's just downloading at that point, it's safe; if it's actually installing the downloaded packages, be careful.

---

