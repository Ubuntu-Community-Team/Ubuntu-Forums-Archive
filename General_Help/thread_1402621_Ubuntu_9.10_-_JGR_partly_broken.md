---
title: "Ubuntu 9.10 - JGR partly broken"
date: 2010-02-09
forum: General Help
---

### Post by Nordic on 2010-02-09
I have been using JGR as my default R interface for a year or so now - It makes working in R so much easier. Now I have encountered a problem. 

JGR still works -sort of. That is R works through JGR, but many of the nice features of JGR don't work. Notably, the object browser and package manager do not work, and the function hinting (pop up window showing arguments accepted by a function) dont work either.
[INDENT]> JGR :: package.manager()
Error in JGR :: package.manager : 
  package 'JGR' has no name space and is not on the search path
> object.browser()
Error: could not find function "object.browser"
> [/INDENT]


As far as I can tell, this occured on upgrade to 9.10. 

I've tried using different Java environments, but no real success.

Has anyone else encountered this?
I wonder if I should just go for a removal and reinstall of R and JGR?

Eric

---

### Post by jjunju on 2010-02-14
I too have this problem. I have to do the re-installation each time I want to start R and JGR because when I exit and start again without this re-install it fails. 

The moment i start to do anything, e.g ? plot(), or even 1+1  then in the console I get the following statements which do not stop.

? plot
```
> Error: could not find function ".getModels"
Error: could not find function ".getDataObjects"
Error: could not find function ".getOtherObjects"
Error: could not find function ".getFunctionsInWS"
```

---

### Post by jjunju on 2010-02-14
i have found that when i launch JGR in terminal using ```
library(JGR)
``` then ```
JGR()
```, it will give me the errors i described earlier [HTML](see screen capture image1: attachment 1)[/HTML] when i start typing my commands after JGR loads. 

However if i start by reloading the JGR library i.e. ```
library(JGR)
```,after JGR window loads, then (at least for now) i can do everything else without any errors [HTML](see screen capture image2: attachment 2)[/HTML]

If you continue having problems, you can switch to rkward. It can be installed through synaptic or ```
sudo apt-get install rkward
```. May need to have some repositories in your sources list. I do not remember which one but google can help. But the graphics in rkward dont look as nice!!

---

### Post by dugh on 2010-03-15
I'm getting the same error in 9.04, too, with R 2.10.  Is there a bugfix or bug report for this anywhere?

---

### Post by dugh on 2010-03-15
After moving /usr/lib/R/site-library and and deleting any objects in the session and re-installing JGR the errors appear to have gone away now. Perhaps it was an old rJava or other conflict, I don't know.

The object browser and so forth still were not working.  But I just tried it again from the script launcher and now the object browser works.

---

