---
title: "Error sudo: no valid sudoers sources found, quitting"
date: 2010-10-06
forum: General Help
---

### Post by s0c0 on 2010-10-06
So I awesomely changed my /etc/sudoers file permissions from 0440 to 0740 so I could edit the file as root.  I know get the following error when I attempt to sudo:

```

sudo: /etc/sudoers is mode 0740, should be 0440
sudo: no valid sudoers sources found, quitting

```

Since I don't have root access and I cannot sudo I am unable to change the file back to 0440.  Pretty freakin circular.  Pretty freakin dumb of me.  The only solution I can think of is running a live disk and changing the permissions from there.  Any better ideas?

---

### Post by e79 on 2010-10-06
Can you see if this works :
```
sudo /bin/bash
```and enter your password.

**Know that you will gain root access doing it if it works, so beware what you are doing !**

For future reference, don't touch the sudoer file, to edit files as root simply type :
```
sudo nano file.txt
```or
```
sudo vi file.txt
```or to edit from files from the GUI:
```
gksu nautilus
```**But again, having root access could mess your system if you are not cautious !**

If it doesn't work, booting of a LiveCD would probably be the best options, unless someone can correct me.

Hope this helps

---

### Post by luvshines on 2010-10-07
@e79: If sudo command itself is not working, will sudo /bin/bash work ?

@s0c0
Did you have a root password setup ??
You can su then and change the permissions back

---

### Post by sikander3786 on 2010-10-07
Just boot into recovery mode and drop to root shell and then do chmod.

```
chmod 440 /etc/sudoers
```

---

### Post by s0c0 on 2010-10-07
Yeah I don't get a grub window when I boot.  So I can't get into recovery mode...weird.

---

### Post by andrewthomas on 2010-10-07
hold down shift when booting

---

### Post by s0c0 on 2010-10-07
> **andrewthomas said:**
> hold down shift when booting

thanks, that was the trick.

---

### Post by andrewthomas on 2010-10-07
Glad to be of help.

---

