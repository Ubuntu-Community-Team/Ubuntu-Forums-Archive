---
title: "trying to uninstall srware iron. problems"
date: 2011-06-28
forum: General Help
---

### Post by prometheus442 on 2011-06-28
Tried to install this browser a while back and it never worked. I just want to get rid of it. I was trying to install something else (I don't even remember what) until Iron got in the way.  

So I gave this a shot: 
dpkg --remove --force remove-reinstreq iron  

and I got this error: 
dpkg: error: requested operation requires superuser privilege  

so I gave this a shot: 
sudo dpkg --configure -a 
[password] 
dpkg --remove --force remove-reinstreq iron  

and I got this error: 
dpkg: error: requested operation requires superuser privilege 

:mad:  
I appreciate any help.

---

### Post by woodrobin on 2011-06-28
> **prometheus442 said:**
> Tried to install this browser a while back and it never worked. I just want to get rid of it. I was trying to install something else (I don't even remember what) until Iron got in the way.  

So I gave this a shot: 
dpkg --remove --force remove-reinstreq iron  

and I got this error: 
dpkg: error: requested operation requires superuser privilege  

so I gave this a shot: 
sudo dpkg --configure -a 
[password] 
dpkg --remove --force remove-reinstreq iron  

and I got this error: 
dpkg: error: requested operation requires superuser privilege 

:mad:  
I appreciate any help.

You'll need to preface the dpkg --remove command with sudo:

```
sudo dpkg --remove --force remove-reinstreq iron
```

That should take care of it.  If the package wasn't fully or properly installed first time around, you might need to run:

```
sudo dpkg -i iron  && sudo dpkg --remove --force remove-reinstreq iron
```

That would correctly install the package, allowing the removal process to know what files it is supposed to remove.

---

### Post by prometheus442 on 2011-08-25
Thanks, Duuuuuuude.

---

