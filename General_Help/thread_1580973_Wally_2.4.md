---
title: "Wally 2.4"
date: 2010-09-24
forum: General Help
---

### Post by cancer10 on 2010-09-24
Hi

I am using Ubuntu 10.04 and installed Wally 2.4.

I have few questions:

1) Currently I run wally with command line by running

```
sudo wally
```

It works, but as soon as I close my terminal, wally terminates. Is there anyway I can make it not terminate?

2) Please refer the screenshot, why is that option disabled?


Many thanks

---

### Post by SlugSlug on 2010-09-24
```
nohup sudo wally
```or create a custom launcher



add it to startup applications  in system > prefrences

---

### Post by cancer10 on 2010-09-24
What does ***_nohup sudo wally_*** do?

---

### Post by SlugSlug on 2010-09-24
nohup = no hangup


```
$ whatis nohup
nohup (1)            - run a command immune to hangups, with output to a non-tty

```

---

### Post by cancer10 on 2010-09-24
> **SlugSlug said:**
> ```
nohup sudo wally
```or create a custom launcher



add it to startup applications  in system > prefrences



Thanks.

---

