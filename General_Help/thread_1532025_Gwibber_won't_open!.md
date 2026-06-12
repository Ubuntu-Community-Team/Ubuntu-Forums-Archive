---
title: "Gwibber won't open!"
date: 2010-07-15
forum: General Help
---

### Post by Cam! on 2010-07-15
For some odd reason, Gwibber won't open at all. The process is listed as "Sleeping", but every time I try and open the app, nothing happens. I tried re-installing it, and even deleting it via Synaptic and installing, but to no avail.

What do I do?

---

### Post by techunit on 2010-07-15
go to the terminal and type the following:

```
sudo aptitude purge gwibber
``````
sudo apt-get install gwibber
```

---

### Post by Cam! on 2010-07-15
> **techunit said:**
> go to the terminal and type the following:

```
sudo aptitude purge gwibber
``````
sudo apt-get install gwibber
```

That didn't help at all.

---

### Post by techunit on 2010-07-15
really have you restarted?

Just kidding...

That should have worked...

```
sudo aptitude reinstall gwibber
```

---

