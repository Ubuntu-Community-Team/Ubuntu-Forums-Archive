---
title: "Synaptic cant update koti, theli, archive"
date: 2006-05-14
forum: General Help
---

### Post by dhruv_1884 on 2006-05-14
hi whenever i try to update my repositories the koti, theli, archive repositories donot get updated


then i get a set of warnings

all the error messages and warnings can be seen in the screen shots that i have attached.

please do have a look at the screen shots

thanks 
regards 
dc

---

### Post by arthur on 2006-05-14
My theli.fr repositories NEVER work, either

---

### Post by fattony on 2006-05-14
I don't know what is causing this, But I just encoutered it.. say about 3 days ago out of 2 weeks with out any problems. I've redone the .list file, sudo apt-get update,
removed the cd from the repository listing..

Anyone else experiencing this?? Please feed back would be greatly appreciated. His screen shots are excellent and same the same if you are in a console trying.

--------------------------------------
ok I noticed for some reason from the console wget and apt-get were just now trying to use a proxy, so do "env" and see the proxy listed "mine was invalid/wrong (I didnt add it <shrug>) so do "env HTTP_PROXY=" then ran "sudo apt-get update" everything worked (updating list, etc.) got 2 warnings about duplicates, ran it a 2nd time and sweet cheeba problem fixed!!!

---

### Post by dhruv_1884 on 2006-05-15
dude could u give me the step by step procedure to fix the issue


thanks 

regards

dc

---

### Post by easyease on 2006-05-15
Im having the same problems.....

---

