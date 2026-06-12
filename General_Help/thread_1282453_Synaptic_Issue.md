---
title: "Synaptic Issue"
date: 2009-10-04
forum: General Help
---

### Post by Prominence on 2009-10-04
Whenever I go to the Update Manager and hit "Check" to check for updates, it just kind of locks up, doesn't freeze, but when there's the load thing when it's checking the repos for updates...well that thing isn't there and the Update Manager locks itself up, and if I close it, and try to launch another Synaptic, it tells me that there's another Synaptic running in non-interactive mode and it'll never stop that, until I restart the computer, then it's the same song and dance all over again.

---

### Post by crolanx on 2009-10-04
Have you tried to clean the packet cache?

In a terminal, try:
```

sudo aptitude clean

```

Or what happens when you start aptitude in a terminal and try to perform an update there?
```
sudo aptitude -u
```

---

### Post by Prominence on 2009-10-04
Alright, it worked and showed me all of the updates, but how do I install them?

EDIT: Alright, nvm, thank you so much for your help, I greatly appreciate it

---

