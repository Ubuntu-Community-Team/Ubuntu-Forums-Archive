---
title: "how to stop cat command?"
date: 2009-10-13
forum: General Help
---

### Post by skaldyr on 2009-10-13
Im writing a shell script that uses cat to listen to a usb port.

The code im using is this:

```
echo at+csq > /dev/ttyUSB2 & | cat /dev/ttyUSB2
```the problem is that cat dosnt stop when it has read the tty.

so how could i write a shell script the cats the first to lines on tty and then stops?

---

### Post by hwttdz on 2009-10-13
You mean first two lines? head -n 2

---

### Post by skaldyr on 2009-10-13
Yes i mean first two lines.

where should the head -n 2 be

---

### Post by Xbehave on 2009-10-13
> **skaldyr said:**
> Yes i mean first two lines.

where should the head -n 2 be

```
echo at+csq > /dev/ttyUSB2 & | head -n 2 /dev/ttyUSB2
```

---

### Post by skaldyr on 2009-10-13
Nice. Thank you very much.

---

