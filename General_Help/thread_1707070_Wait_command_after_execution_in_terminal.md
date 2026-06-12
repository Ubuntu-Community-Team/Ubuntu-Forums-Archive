---
title: "Wait command after execution in terminal?"
date: 2011-03-14
forum: General Help
---

### Post by pepsifx357 on 2011-03-14
How do I create a command to launch a program and then have the terminal wait for a specified time and then move on to the next command?

I'm wanting to create a startup script, and I need program B to wait until program A has finished  loading up.

Thanks

---

### Post by rubylaser on 2011-03-14
You can use sleep if you want like this...
```

/path_to/program_a
sleep 60
/path_to/program_b
```
This will wait for 60 seconds.

---

### Post by pepsifx357 on 2011-03-15
Thanks!  That's exactly what I was looking for.

---

### Post by SWGraphics291 on 2013-02-14
This also helped me, thanks.

---

### Post by cariboo on 2013-02-17
Let's put this thread back to sleep, as it is more than a year old, especially as the last two post didn't really add any additional information

---

