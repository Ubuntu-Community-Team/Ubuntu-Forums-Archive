---
title: "My folders are empty after log in!"
date: 2012-01-07
forum: General Help
---

### Post by coolmanlg on 2012-01-07
I logged into my Ubuntu 11.10 that I have been using and I can't see any of my created documents and folders. My folders have defaulted to how it was when I did a fresh install! There is nothing in the folders. What is wrong pleases?

---

### Post by BlinkinCat on 2012-01-07
Hi,

I can't really help you but I was wondering how long it has been since your fresh install?

---

### Post by WorMzy on 2012-01-07
Open a terminal and run the command
```
ls -R /home
```

The output should make it obvious whether all your files are there or not.

In my experience though, home folders do not simply "reset" themselves.

---

### Post by coolmanlg on 2012-01-07
I have carried out the command and my folders are empty? I have been running 11.10 for over three months now. What could have happened?

---

### Post by todak on 2012-01-07
Perhaps you are logged in as a different user, e.g., guest.

---

### Post by coolmanlg on 2012-01-07
I logged in as myself, normal user.

---

