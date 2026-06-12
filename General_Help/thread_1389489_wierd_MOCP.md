---
title: "wierd MOCP"
date: 2010-01-24
forum: General Help
---

### Post by pedrom169 on 2010-01-24
i have installed minimal ubuntu on my desktop.

When i run "mocp" from terminal and go to a directory to try to play a song i get this error:

```
FATAL_ERROR: Can't receive value from the Server
```

But when i do "sudo mocp". It allows me to play songs perfectly.

Anyone know what this error is?

Thank you advanced.

---

### Post by afrodeity on 2010-11-02
Getting this error after maverick upgrade. Wish I knew the answer.

---

### Post by afrodeity on 2010-11-02
I filed a bug
[https://bugs.launchpad.net/ubuntu/+source/moc/+bug/670027](https://bugs.launchpad.net/ubuntu/+source/moc/+bug/670027)

---

### Post by afrodeity on 2010-11-02
This message when it initialises

```

Build signature doesn't match environment
```

---

### Post by afrodeity on 2010-11-02
FIXED:

rm -r ~/.moc/cache

---

### Post by CharlesA on 2010-11-02
Friendly mod note: Please use the *edit* button, it's there for a reason.

---

