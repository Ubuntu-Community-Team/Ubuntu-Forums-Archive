---
title: "Command Not Found After Launching Terminal"
date: 2011-01-26
forum: General Help
---

### Post by xcusmwah on 2011-01-26
As soon as I launch terminal I get the following:

[...]: command not found
[...]: command not found

And it then goes to a $~ prompt as usual.  How do I make it so the two commands it is trying to launch don't run upon launching terminal?

---

### Post by TeoBigusGeekus on 2011-01-27
Look for a strange configuration in your bashrc or a mistyped parameter in your launch-terminal command in your menu.

---

### Post by xcusmwah on 2011-01-28
The command I have for launching terminal is gnome-terminal.  How do I edit bashrc?  Thanks!

---

### Post by oldos2er on 2011-01-28
```
gedit .bashrc
```

---

### Post by nothingspecial on 2011-01-28
I`d post it before you mess with it if you don`t know what your doing.

Having said that, there is a default one at /etc/skel/.bashrc so if you do mess it up just do

```
cat /etc/skel/.bashrc > /home/$USER/.bashrc
```

then

```
. ~/.bashrc
```

And that will reset it.

---

### Post by TeoBigusGeekus on 2011-01-28
> **oldos2er said:**
> ```
gedit .bashrc
```

Make it 
```
gedit ~/.bashrc
```
and yeah, post it to us before you change anything.

---

