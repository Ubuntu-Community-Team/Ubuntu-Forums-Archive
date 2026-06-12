---
title: "Shell Script that keeps Terminal Open"
date: 2010-09-21
forum: General Help
---

### Post by alexgeek on 2010-09-21
If I have a shell script that executes some commands, can I get it so that the terminal will not close after it completes those commands?
Hope you know what mean, ta.

---

### Post by Tibuda on 2010-09-21
yes, add the following as the last line of the script.
```
read -n1
```

---

### Post by bodhi.zazen on 2010-09-21
> **alexgeek said:**
> If I have a shell script that executes some commands, can I get it so that the terminal will not close after it completes those commands?
Hope you know what mean, ta.

Not sure what you are wanting exactly. Do you want to capture the output ? Just have an open terminal ?

---

### Post by alexgeek on 2010-09-21
Just wanted an open terminal 'read -n1' worked great, would be interesting to know how to capture output to though.
Thanks :)

---

### Post by Tibuda on 2010-09-21
> **alexgeek said:**
> Just wanted an open terminal 'read -n1' worked great, would be interesting to know how to capture output to though.
Thanks :)

```
command > filename
```
will capture the output of **command** to **filename**, erasing it. if you want to append the output to the filename, use
```
command >> filename
```

---

### Post by alexgeek on 2010-09-21
Diolch :)

---

