---
title: "Does string contain a specific character?"
date: 2011-10-09
forum: General Help
---

### Post by Kissell on 2011-10-09
I need to check a variable "$name" to see if the string contains a "." period.  If so, I want the program to exit.  I tried a case statement like the one below and it doesn't work.  

> 
  case "$name" in
    *.*)
      exit 0;;
    *)
      CONTINUE_PROGRAM;;
  esac


---

### Post by papibe on 2011-10-09
What kind of error are you having?
Is that the actual code?

This works:
```

case "$name" in
    *.*) exit 0
         ;;
    *)
esac

# rest of the code
```
You can also use this logic:
```
if [[ "$name" == *.* ]]; then
    exit 0
fi
```
Or just simple as:
```
[[ "$name" == *.* ]] && exit 0
```
Does that help?
Regards.

---

### Post by JKyleOKC on 2011-10-09
Does the period need to be escaped? It matches "any character" in a regular expression, but I don't know whether these constructs use REs or simply the globbing syntax. Try putting a "\" in front of it and see if that works...

EDIT-- If it's an RE, then the expression would be ".*\..*" since the "*" also has a different meaning!

---

### Post by sisco311 on 2011-10-10
> **JKyleOKC said:**
> Does the period need to be escaped? It matches "any character" in a regular expression, but I don't know whether these constructs use REs or simply the globbing syntax. Try putting a "\" in front of it and see if that works...


No. In the above examples *.* is a glob. In bash, only the [[ command allows you to use a RE:
```
[[ whatever **=~** ERE ]]
```

---

### Post by Kissell on 2011-10-11
> **papibe said:**
> 
You can also use this logic:
```
if [[ "$name" == *.* ]]; then
    exit 0
fi
```

I just tried this, and it doesn't work.  Script doesn't exit, it just keeps on going.

---

### Post by papibe on 2011-10-11
I just tested the expressions and they all work here. The 'case' was the closer of what you were looking, Did you try the case?

Could post your script?

Regards.

---

