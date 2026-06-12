---
title: "help installing vmc"
date: 2011-08-22
forum: General Help
---

### Post by cmcanulty on 2011-08-22
I am having trouble doing this instruction, I don't know exactly how to  do it. It isn't really code but I am putting code tags in case it is
```
If	
  vmc	
  does	
  not	
  work	
  and	
  you	
  are	
  using	
  Ubuntu,	
  add	
  :	
  	
  
export	
  PATH=$PATH:/var/lib/gems/1.8/bin	
  
to	
  your	
  .bashrc	
  file	
  

```

---

### Post by bodhi.zazen on 2011-08-22
gedit ~/.bashrc

At the bottom of the file add

```
export PATH=$PATH:/var/lib/gems/1.8/bin
```

log out and back in ;)

---

### Post by cmcanulty on 2011-08-23
OK great thanks.

---

