---
title: "bash help"
date: 2011-12-08
forum: General Help
---

### Post by Scooter_X on 2011-12-08
Hey so I need to provide someone with the output of 'lsusb -v' but it's LOOOONG and I don't know what option it is to be able to see it bit by bit instead of just having it spit out everything all at once. Any help? Thanks.

---

### Post by d2btoo on 2011-12-08
Are you looking for something like this ...
```

lsusb -v | less

```

or

```

lsusb -v > output.txt

```

---

### Post by mutley89 on 2011-12-08
Not sure if it's installed by default (if not "sudo apt-get install xclip"), but if you want to copy / paste the output use xclip:
```
lsusb -v | xclip -selection c
```then simply Ctrl-v wherever you want it.

---

### Post by Scooter_X on 2011-12-08
> **d2btoo said:**
> Are you looking for something like this ...

```

lsusb -v > output.txt

```

I didn't know I could send it straight to a file. Thanks!

---

### Post by markbl on 2011-12-08
> **Scooter_X said:**
> I didn't know I could send it straight to a file. Thanks!
FYI, you can also view it, and send it to a file:
```

lsusb -v | tee output.txt

```

---

