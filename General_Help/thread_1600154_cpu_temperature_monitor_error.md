---
title: "cpu temperature monitor error"
date: 2010-10-18
forum: General Help
---

### Post by williammrbiggs on 2010-10-18
I installed ubuntu 10.10 and when I start ubuntu I get this error cpu temperature monitor error. I would like to know how to fixed it

---

### Post by williammrbiggs on 2010-10-18
it also says can not load /lib/mod.../ 2.26. something like that ?

---

### Post by Hippytaff on 2010-10-18
> **williammrbiggs said:**
> it also says can not load /lib/mod.../ 2.26. something like that ?

can you make the error happen again and post it?

---

### Post by williammrbiggs on 2010-10-18
no it right after the computer boot's up . Then right after it shows up then ubuntu boot right up

---

### Post by williammrbiggs on 2010-10-18
it something like this error /lib/modules/2.35-22-generics ...

---

### Post by williammrbiggs on 2010-10-18
more info it is /lib/modules/2.35-22-generics/modules.dep

---

### Post by Hippytaff on 2010-10-19
> **williammrbiggs said:**
> more info it is /lib/modules/2.35-22-generics/modules.dep
 
what does the error message say? or does it just say error /lib etc..?
 
can you copy and paste the contents of module.dep?

---

### Post by williammrbiggs on 2010-10-19
no it is right at boot when gnome loads

---

### Post by Hippytaff on 2010-10-19
> **williammrbiggs said:**
> no it is right at boot when gnome loads
 
So you unable to boot and it hangs with this message?

---

### Post by williammrbiggs on 2010-10-19
no it say it 2 times then somthing about cpu temperature monitor then boot right into 10.10

---

### Post by Hippytaff on 2010-10-19
once you log in, open a terminal and post the output of
 
```

ascpi -V

```
 
capital V - you might need to download acpi
 
```

sudo apt-get install acpi

```
 
also it might be worth updating stuff just to see if that sorts it
 
```

sudo apt-get update && sudo apt-get upgrade

```
 
Looks like something to do with dependencies but do this first and we'll take if from there :-)

---

### Post by williammrbiggs on 2010-10-19
I got command not found ascpi -V

---

### Post by williammrbiggs on 2010-10-19
I try to install ascpi it says nothing found

---

### Post by Hippytaff on 2010-10-19
sorry...should've been acpi - will tell you temp etc

---

### Post by williammrbiggs on 2010-10-19
ok I'll try it

---

