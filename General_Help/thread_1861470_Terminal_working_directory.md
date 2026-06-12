---
title: "Terminal working directory"
date: 2011-10-15
forum: General Help
---

### Post by beer-in-box on 2011-10-15
Hi, this is the first post in the forum. So, hello :)

While I was using Pardus, I could start terminal in right click menu and it started in the folder I started it. The same thing was present in Mint, too.
I mean if I started it in "/beerinbox/Desktop/stuff" by right clicking and selecting terminal, the pwd of the terminal was set to /beerinbox/Desktop/stuff. How can I achieve this in Ubuntu?

---

### Post by WorMzy on 2011-10-15
Try installing nautilus-open-terminal, then restarting nautilus.

```
sudo apt-get install nautilus-open-terminal
```

```
killall nautilus
```

---

### Post by beer-in-box on 2011-10-15
Thank you. This solves it. I can't believe it was that easy.

---

### Post by ajgreeny on 2011-10-15
There are several more nautilus plugins/extensions you might find useful, in particular **nautilus-gksu** which allows you to right click and "Open as administrator"

---

### Post by beer-in-box on 2011-10-15
Thank you! It just gets better and better. So, I am going to google for more useful nautilus plugins.

---

### Post by beer-in-box on 2011-10-16
It seems there is a bug with nautilus-open-terminal and it makes nautilus close randomly. I removed it and now I'm monitoring it if it was the problem.

---

