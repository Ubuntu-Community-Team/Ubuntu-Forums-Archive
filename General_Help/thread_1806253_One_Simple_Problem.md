---
title: "One Simple Problem"
date: 2011-07-17
forum: General Help
---

### Post by rezame on 2011-07-17
Hi,
I am very new in Linux & Ubuntu. I am trying run below command in ubuntu and get below error:
echo "" > /etc/radiusclient/port-id-map

Error: bash: /etc/radiusclient/port-id-map: Permission denied

I tried sudo echo "" > /etc/radiusclient/port-id-map  too, but got same error too.
How to solve that?
Regards,

---

### Post by patchwork on 2011-07-17
The sudo applies only to the echo before the redirect overwrite.

To accmplish this, you can use the tee command:
```
echo "" | sudo tee <file location>
```

---

### Post by japq7b on 2011-07-17
It's something that pops up from time to time.  You can get around it by doing one of two things that I've found so far.  You can use a command line editor and append the content of the echo manually or else you can run
```
sudo bash
```
which will give you a root shell and then you can just run the command normally.

---

### Post by CatKiller on 2011-07-17
> **japq7b said:**
> which will give you a root shell and then you can just run the command normally.

```
sudo -i
``` if you really must have a root terminal.

---

### Post by nothingspecial on 2011-07-17
You realise that command will delete whatever is in that file? I hope.

If you are just trying to create it you can use touch.

What are you actually trying to do?

---

