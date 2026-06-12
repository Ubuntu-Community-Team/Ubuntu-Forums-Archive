---
title: "Update Manager Launches then Suddenly Closes"
date: 2011-07-31
forum: General Help
---

### Post by SteelReserve on 2011-07-31
Update Manager used to work fine, but now when I launch it, it appears momentarily in the task bar, then shuts down.  I haven't been able to install any updates in a couple weeks.  I'm running Ubuntu 10.04.  Any help is appreciated.  Thanks.

---

### Post by drs305 on 2011-07-31
SteelReserve,

Welcome to the Ubuntu forums.

Have you tried doing the updates via Synaptic?

If you run the following, do you get any error messages? If so, please post them:
```

sudo apt-get update
sudo apt-get upgrade
```

If you don't know how to go about doing these things, just ask.

---

### Post by thefasterblueone on 2011-07-31
Try running the update using the Terminal. The Terminal will show any errors that might occur and that will help solve the problem.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Hope this will help you. let us know.

---

