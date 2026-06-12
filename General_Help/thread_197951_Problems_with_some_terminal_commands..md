---
title: "Problems with some terminal commands."
date: 2006-06-16
forum: General Help
---

### Post by FlyingPenguin on 2006-06-16
I'm trying to start a program from the terminal. First of all, I can not even cd to the proper directory which is called "X-Plane 8.40".

It says can not find directory X-Plane so I guess it has something to do with the space in the name. So I renamed the directory to "x" and tried to launch the binary called "X-Plane-i586" and it said command not found.

What am I doing wrong here?

---

### Post by rbalfour on 2006-06-16
$ ./X-Plane-i586

also check to see if the file has X permissions.
If not 

$chmod +x X-Plane-i586

---

### Post by Ramses de Norre on 2006-06-16
To make bash interprete spaces correctely set "" around the path or set an \ before every space.
```
"X-Plane 8.40"
or
X-Plane\ 8.40
```

---

