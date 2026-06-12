---
title: "Sending messages to Other Computers on the same network with Write command"
date: 2010-09-14
forum: General Help
---

### Post by eimhin85 on 2010-09-14
Hi,

Ok the write command just isnt working for me at all. Am i right in thinking it can even do this function?

Im using:

```
 write paul@paul-laptop pts/0
```It keeps telling me > write: paul is not logged in on pts/0

anyone know what im doing wrong?

---

### Post by jpaugh64 on 2010-09-14
I am *pretty* sure that the write command only works for users of the local machine, and only while they are logged in. It is from the days of time-sharing, most likely. I guess get a ssh account on the other computer(s)?

---

### Post by eimhin85 on 2010-09-14
ahh ok. well thats a mild disappointment. thanks for swift reply though

---

