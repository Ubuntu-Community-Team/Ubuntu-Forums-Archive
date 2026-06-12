---
title: "/bin/bash: flex: command not found"
date: 2012-08-16
forum: General Help
---

### Post by UbuntuNerd on 2012-08-16
can anybody please be so kind to help me with this problem:

im trying to compile android from source but i keep getting:
/bin/bash: flex: command not found

i google around and try a few things but is still there, any help is much appreciated

---

### Post by ads52 on 2012-08-16
I had a quick look and found this:

```

andrew@corinth:~$**[COLOR="Red"] apt-cache search flex | grep -i lexical[/COLOR]**
**[COLOR="Red"]flex - A fast lexical analyzer generator.[/COLOR]**
flex-doc - Documentation for flex (a fast lexical analyzer generator).
jflex - lexical analyzer generator for Java
libfl-dev - static library for flex (a fast lexical analyzer generator).
alex - lexical analyser generator for Haskell
cl-lexer - Lexical-analyzer-generator package for Common Lisp
flex-old - Old version of the fast lexical analyzer generator
flex-old-doc - Documentation for an old flex (a fast lexical analyzer generator)
tclex - A lexical analyzer generator for Tcl

```

So a good start might be:

```
sudo apt-get install flex 
```

Hope this solves the issue for you...

---

### Post by UbuntuNerd on 2012-08-16
i also found that and install it but i still got the error, let me reinstall again, thanks by the way !!!

---

### Post by ads52 on 2012-08-16
Can I ask what source you are trying to compile?

---

### Post by UbuntuNerd on 2012-08-16
cm9 
[http://aosp.chris41g.org/chris41g_org/aosp/post/2012/07/09/How-To-Compile-CyanogenMod-9-from-Source.aspx](http://aosp.chris41g.org/chris41g_org/aosp/post/2012/07/09/How-To-Compile-CyanogenMod-9-from-Source.aspx)

---

