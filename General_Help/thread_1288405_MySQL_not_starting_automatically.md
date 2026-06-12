---
title: "MySQL not starting automatically"
date: 2009-10-11
forum: General Help
---

### Post by Jmz360 on 2009-10-11
When I restart my Ubuntu computer, MySQL doesn't seem to start automatically. To get it to work all I have to do is run

```

sudo /etc/init.d/mysql restart

```

What can I do to make it start by itself?

---

### Post by eric3_14159 on 2009-11-09
It's a little bit hacky, but if you put "/etc/init.d/mysql restart" in the file /etc/rc.local , then it will run at the end of startup.

It's odd that MySQL isn't starting automatically, though, so it's also worth looking in to why that happens. Try searching the output of dmesg or /var/log/messages to see if any errors are printed.

---

