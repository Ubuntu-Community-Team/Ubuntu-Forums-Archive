---
title: "Increase Ubuntu System Stack Size for Ruby 1.9"
date: 2012-04-14
forum: General Help
---

### Post by linuxspy007 on 2012-04-14
Hi,

I am running Ubuntu 10.04 LTS virtual machine on Windows Vista.  I am experimenting with Ruby 1.9.3 and I am trying to increase the ubuntu stack size with "ulimit -s [x]" where [x]=20000 or unlimited or whatever I choose to input, default is 8192 KB. 

I have a recursion program as follows

```
def countUpTo(current, final)
     puts current
     return nil if current == final
     countUpTo(current+1, final)
 end

 countUpTo(1, 10000)
```It only gets up to 8186, whether or not I increase the stack size with ulimit -s command.  So how do I up the stack size so this ruby program can at least output up to 10000?

---

