---
title: "ssh stay logged in on disconnect"
date: 2009-09-18
forum: General Help
---

### Post by samuelhug on 2009-09-18
Hi I was wondering if someone could help me with a problem I have.
I would like to connect to my workstation via ssh and start a time consuming process such as building a kernel and then disconnect without stopping the build process. Then when I get home be able to see the results somehow.

---

### Post by XCan on 2009-09-18
I think screen should suit your need. Login to ssh, type "screen", and then start your process. You can detach yourself by pressing "ctrl+a ctrl+d". Then you can safely logout. When you get home you can reattach yourself to the screen by typing ```
 screen -R 
```

---

### Post by samuelhug on 2009-09-19
Thanks thats perfect

---

### Post by XCan on 2009-09-19
Glad it worked out. Screen is very powerful, although I've always felt the man page made it out to be more involved than needed. :p

---

