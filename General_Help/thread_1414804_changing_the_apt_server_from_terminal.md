---
title: "changing the apt server from terminal"
date: 2010-02-24
forum: General Help
---

### Post by Natty Dreed on 2010-02-24
hi,

is there any way to change the main server for apt from terminal

sorry for this question but the main server is very slow

---

### Post by cariboo on 2010-02-24
It there a reason you can't change the server using either System-Administration->Software Sources or Synaptic package manager? The only way I know of doing it from the command line is to manually edit /etc/apt/sources.list

---

### Post by pastalavista on 2010-02-24
Open System|Administration|Software Sources and click the dropdown next to "Download from". Select "Other" and when the list pops up, click the button that says "Select Best Server". It will locate the fastest repository for your location.

---

### Post by Natty Dreed on 2010-02-24
I'm Running a Server ... Sorry for not mention that

---

### Post by i.r.id10t on 2010-02-24
edit /etc/apt/sources.list

or use sed

sed -i "s/archive.ubuntu.com/some.other.host.com/g" /etc/apt/sources.list

---

### Post by oldos2er on 2010-02-24
The nano editor does search and replace with Ctrl-\

---

### Post by Natty Dreed on 2010-02-24
Thanks every one ... i did it manually (copy & paste)

---

