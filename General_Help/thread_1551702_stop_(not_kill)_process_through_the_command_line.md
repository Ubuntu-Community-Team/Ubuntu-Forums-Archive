---
title: "stop (not kill) process through the command line"
date: 2010-08-12
forum: General Help
---

### Post by Mr Nemo on 2010-08-12
I was wondering if there was a way to stop a specific process through the command line, but not kill it. Such as if you went into the system manager and right clicked on a process and selected stop.

---

### Post by wojox on 2010-08-12
I just use Ctrl+C. If I just started the process.

---

### Post by GlazedDonut on 2010-08-12
```
kill -s SIGSTOP <pid>
``` 
will send the stop signal to a process.

---

### Post by amauk on 2010-08-12
kill -STOP <PID>

This will completely stop the application
If it's a GUI app, it's GUI interface will be completely non-responsive

Undo the stop with
kill -CONT <PID>

---

### Post by Mr Nemo on 2010-08-12
Great. Thanks a lot, worked like a charm.

---

