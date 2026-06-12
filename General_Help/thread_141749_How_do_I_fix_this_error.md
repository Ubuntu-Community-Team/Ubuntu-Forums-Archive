---
title: "How do I fix this error?"
date: 2006-03-08
forum: General Help
---

### Post by jhaykage on 2006-03-08
I need help please, I messed up with the terminal in my Ubuntu in installing the Nessus vulnerability scanner.

After I downloaded the packages, a prompt came up for configuring the SSL certificate I didn't know what to do so I just closed the terminal.

Now whenever I try to install a new package or program I get this message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

How do I fix this? Help:confused:

---

### Post by bluevoodoo1 on 2006-03-09
Well, you can try to do what it's telling you to do... so try running

```

dpkg --configure -a
```

in a terminal, see if that sorts anything out.

---

### Post by jhaykage on 2006-03-09
I did try that and it returned with this message

"dpkg: requested operation requires superuser privilege"

What do I do now?

---

### Post by bluevoodoo1 on 2006-03-09
sudo dpkg --configure -a


then type in your password. (I forgot to tell you to add sudo before... whoops)

---

