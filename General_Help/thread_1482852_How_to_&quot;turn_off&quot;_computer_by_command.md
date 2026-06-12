---
title: "How to &quot;turn off&quot; computer by command?"
date: 2010-05-14
forum: General Help
---

### Post by ganzheng on 2010-05-14
I would like to turn off computer by commands.

But, I don't know how to use "halt","reboot" nor "shutdown".

Need help :)

---

### Post by devilized on 2010-05-14
try: sudo shutdown now

---

### Post by elliotn on 2010-05-14
> **devilized said:**
> try: sudo shutdown now

i would like some more

---

### Post by devilized on 2010-05-14
Run shutdown --help for a list of all of the possible options.

---

### Post by wojox on 2010-05-14
```
sudo shutdown -H now
```

```
sudo poweroff
```

---

### Post by warri0r on 2010-05-14
sudo halt
sudo poweroff
sudo shutdown -P <delay in minutes>
sudo shutdown -H

---

### Post by wojox on 2010-05-14
Reboots it:

```
sudo shutdown -r now
```

---

### Post by torham-tr on 2010-05-14
I am using
 
```
sudo shutdown -P now
```
 
to turn off immediately.

---

### Post by Drenriza on 2010-05-14
```
sudo shutdown -P 0
``` shutsdown now.

```
sudo shutdown -P 60
``` shutdown in 60 minuts.

---

### Post by dcstar on 2010-05-14
> **warri0r said:**
> ```
sudo halt
sudo poweroff
sudo shutdown -P <delay in minutes>
sudo shutdown -H
```

```
sudo init 0
```

---

