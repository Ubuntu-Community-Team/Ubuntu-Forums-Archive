---
title: "Make file error .error code 2."
date: 2011-09-09
forum: General Help
---

### Post by akshay.sulakhe on 2011-09-09
Hello guys,
           I have a laptop called HP touchsmart tm2. It has a ati raedon graphics card in it,which i am looking to disable. For that i generally use this link,which works perfectly,but now m getting an error:-

Link used to disable fan :- 
[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)

Errors i am getting:-
akshay@linux ~ $ sudo apt-get install kernel-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kernel-headers-2.6.38-8-generic
E: Couldn't find any package by regex 'kernel-headers-2.6.38-8-generic'


Kindly let me know how to fix this error,coz my laptop is a heating iron till i do that. Thinking of running a ironing service.. :P...Thanks guys... :-)

---

### Post by WorMzy on 2011-09-09
No idea whether what you're doing will work or not, but this should get you past that error:

```
sudo apt-get install **linux**-headers-$(uname -r)
```

---

### Post by akshay.sulakhe on 2011-09-09
@worzhy :- Thanks for the reply. Tried the command u said.it says,cant find regex and the kernel name. Even did apt-get update. That post is to turn off the graphics card,as i have 2 in my system,i want to turn off 1 of it. Kindly let me know if u know anything more. Thanks again... :-)

---

