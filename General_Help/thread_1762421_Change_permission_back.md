---
title: "Change permission back"
date: 2011-05-19
forum: General Help
---

### Post by VirtualWaver on 2011-05-19
Hi all,

I wanted to set a password on Pidgin application, so that it will require a sudo password every time when it is executed. I read somewhere in forums that a possible solution is to change permissions by this code:

```
  
sudo chmod 700 /usr/bin/pidgin 
```After doing this I am totally unable to run pidgin (nothing happens when I click to pidgin). 

So my question is: how to change the permission back and make pidgin executed properly when clicked?

Thank you in advance.

P.S. I just tried to do the following:

```


chmod 777 /usr/bin/pidgin


```

And now it is executing normally. Is everything correct with this permission, or it is not the wrong one?

---

