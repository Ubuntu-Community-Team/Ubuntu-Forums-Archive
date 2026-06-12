---
title: "Help with Script to shell 2 commands"
date: 2011-09-27
forum: General Help
---

### Post by zoldy on 2011-09-27
I am trying to write a script that will launch to terminal commands from my home folder

Manually I am doing this..

Open terminal
type ./app1

open another terminal
type ./app2

Both apps stay running

I am trying to script this using

xterm -e ./app1
sleep 10
xterm -e ./app2



My first app opens and runs normal but the second one never starts.

thanks in advance for your help

---

### Post by TeoBigusGeekus on 2011-09-27
```
xterm -e ./app1 &
sleep 10
xterm -e ./app2
```

---

### Post by zoldy on 2011-09-27
thank you this does start my second app but it closes itself.    

If I run it manually it does not.    Any ideas?

---

### Post by TeoBigusGeekus on 2011-09-27
> **zoldy said:**
> thank you this does start my second app but it closes itself.    

If I run it manually it does not.
Could you please elaborate?

---

### Post by zoldy on 2011-09-27
sorry  ... although it closes the second one everything works.   I am not sure even i understand but it works.

Okay so now for the first one.    Since it is an open terminal that stays running all the time I want to hide it on another desktop or even just run it minimized... is that possible?

---

### Post by TeoBigusGeekus on 2011-09-27
If you don't want the terminals to appear, you don't need to launch them at all:
```
./app1
sleep 10
./app2
```

---

### Post by spiky001 on 2011-09-27
Will this help you at all [http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html](http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html)

---

