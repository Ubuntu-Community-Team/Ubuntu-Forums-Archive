---
title: "bash socket programing"
date: 2009-07-03
forum: General Help
---

### Post by mamali on 2009-07-03
how to connect to a local port in bash?
i have tried netcat but it says:
```
connection refused
``` 
what should i do ?

---

### Post by Brandon Williams on 2009-07-03
It would be better if you show us how you're trying to use nc for this.

Here's an example of a shell command line that works just fine:
```
echo -e 'GET / HTTP/1.0\n\n' | nc www.google.com 80
```

---

