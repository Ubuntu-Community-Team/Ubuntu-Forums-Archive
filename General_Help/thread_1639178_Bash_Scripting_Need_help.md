---
title: "Bash Scripting Need help"
date: 2010-12-06
forum: General Help
---

### Post by hantechbl on 2010-12-06
I am looking for a way to keep a log and make if then statements if a line exitsts in the log.  I also am looking for a way to make a simple loop, like goto line number, and I also am wondering how to add/remove bits of text from a text file (plugins line in server.properties)

---

### Post by luvshines on 2010-12-06
Don't know for sure, but I think you can achieve all that with 'sed' command - searching, goto line number, replace
For logging, simply echoing would suffice

---

### Post by DaithiF on 2010-12-06
> **hantechbl said:**
> I am looking for a way to keep a log and make if then statements if a line exitsts in the log.  I also am looking for a way to make a simple loop, like goto line number, and I also am wondering how to add/remove bits of text from a text file (plugins line in server.properties)
Hi, it will be easier to help if you give some actual example(s) of what you want to do.

---

### Post by hantechbl on 2010-12-07
Ok I got figured out everything else but looping, EX. goto line #
and how to use sed to remove a bit of information for example 
```
Server.properties
Some Lines Up here.
plugins=x
```
how would I get sed to remove x and make it:
```
server.properties
Some Lines Up here.
plugins=
```

---

### Post by sisco311 on 2010-12-07
```
sed -i 's_^plugins=.*_plugins=_' path/to/file
```

---

### Post by hantechbl on 2010-12-07
where would the variables go?

---

