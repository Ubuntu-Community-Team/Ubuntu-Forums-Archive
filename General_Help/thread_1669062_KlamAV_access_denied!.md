---
title: "KlamAV access denied!"
date: 2011-01-17
forum: General Help
---

### Post by shatanas on 2011-01-17
I have installed KlamAV just in case and am now proceeding with scanning. However, a few directories showed up in pop-ups non-accessible and at about 5% a whole sequence of such. I also remember this "access denied" occurring when I tried to change something in the Administrator menu, although I can't remember what.

How can I allow full access to all files? I am the admin after all!

---

### Post by XeonBloomfield on 2011-01-17
Did you start ClamAV by typing that?
```
sudo <program_start_command>
```

---

### Post by shatanas on 2011-01-17
no, I have installed it using the ubuntu software centre and started via Applications -> System Tools -> KlamAV

---

### Post by XeonBloomfield on 2011-01-17
Try to start it by typing:
```
sudo klamav
```
in your Terminal.

Terminal can be run from Applications > Accessories > Terminal.

"sudo" run command after it with "root's power".

When you start it from Terminal you need to have opened Terminal since you end work with that program, because Terminal running it as child process and when you shutdown it command what is still executing will be killed.

---

### Post by shatanas on 2011-01-17
But that still does not explain why I don't have administrator rights...And would it not pose the same problem if it opens a GUI?

---

### Post by XeonBloomfield on 2011-01-18
You have, but it is dangerous for normal work with these rights.

You can miss-click and destroy whole system. Command "sudo" and window "Run as Administrator" is protecting from it by delivering "Admin's power" when it is really needed.

---

### Post by shatanas on 2011-01-18
the 'elevated privileges' key sign? Why does the system then not ask me to type in my password!!??

---

### Post by shatanas on 2011-01-18
the 'elevated privileges' key sign? Why does the system then not ask me to type in my password!!??

---

