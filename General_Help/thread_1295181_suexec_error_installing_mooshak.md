---
title: "suexec error installing mooshak?"
date: 2009-10-19
forum: General Help
---

### Post by abhilashm86 on 2009-10-19
i was installing mooshak, its an compulsory tool for online contest, why is this error on installing?
```
root@abhi:/home/abhilash/Desktop/mooshak-1.4.3# ./install --config-suexec
There might have been errors enabling suexec
can't read "m2": no such variable
    while executing
"puts "Apache's Output: \n\t $m1 \n\t $m2""
    (procedure "enable_suexec" line 35)
    invoked from within
"$action"
    (procedure "process" line 39)
    invoked from within
"process"
    invoked from within
"if { [ string compare [ exec whoami ] root ] == 0 } {
    process
    exit 0
} else {
    puts stderr "You have to be root to install Mooshak"
    exi..."
    (file "./install" line 732)
root@abhi:/home/abhilash/Desktop/mooshak-1.4.3# 

```
i'm refering this [tutorial to install mooshak.....]("http://ideamonk.blogspot.com/search/label/mooshak")
please help.........

---

