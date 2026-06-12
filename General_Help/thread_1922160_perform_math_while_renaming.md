---
title: "perform math while renaming"
date: 2012-02-08
forum: General Help
---

### Post by HiImTye on 2012-02-08
I'm fairly new to using perl and was wondering if there was a way to perform math on the perl string while renaming bulk files. here is how I would normally rename something:
```
rename -n 's/0(\d{2})/1$1/' *
```which would, for instance, perform the following on my dummy files:
```
tye@T:~/Documents/you're a dummy$ rename -n 's/0(\d{2})/1$1/' *
dummy001 renamed as dummy101
dummy002 renamed as dummy102
dummy003 renamed as dummy103
```I would like to be able to, for instance, subtract 1 or more from the stored string so that dummy002 could come out as dummy001, etc..

---

### Post by erind on 2012-02-13
Take a look at '**e**' (*evaluate*) modifier, which makes possible the code execution in the substitution part. For your example try something along the lines of:

```
rename -n 's/(\d+)/ sprintf("%.3d", $1-1) /e' dummy*
```

---

### Post by HiImTye on 2012-02-13
> **erind said:**
> Take a look at '**e**' (*evaluate*) modifier, which makes possible the code execution in the substitution part. For your example try something along the lines of:

```
rename -n 's/(\d+)/ sprintf("%.3d", $1-1) /e' dummy*
```
that actually solved two questions I had, the other was how to pass variable length numbers to prename

thanks a million!

---

