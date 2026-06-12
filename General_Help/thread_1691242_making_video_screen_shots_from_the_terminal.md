---
title: "making video screen shots from the terminal?"
date: 2011-02-19
forum: General Help
---

### Post by sohlinux on 2011-02-19
I need to take screen shots from a 60 minute video in jpeg format in intervals of 1 minute.

which program will do this from the terminal?

---

### Post by sohlinux on 2011-02-19
any ideas?

---

### Post by WorMzy on 2011-02-19
Save this as a script:
```
#!/bin/bash
x=0
while [ $x -le 60 ]; do
  scrot $(echo $x).jpg
  x=$(($x + 1))
  sleep 60
done
```

Replace the scrot line with whichever screenshot application you use.

---

### Post by sohlinux on 2011-02-19
> **WorMzy said:**
> Save this as a script:
```
#!/bin/bash
x=0
while [ $x -le 60 ]; do
  scrot $(echo $x).jpg
  x=$(($x + 1))
  sleep 60
done
```

Replace the scrot line with whichever screenshot application you use.

thanks ;) I will try that

---

