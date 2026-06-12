---
title: "Removing a program"
date: 2011-08-21
forum: General Help
---

### Post by Reddoug on 2011-08-21
Hi

I mistakenly installed CINT/ROOT C/C++ on my computer running Ubuntu 10.4 LTS. I was trying to do something and it said I did not have root installed so I sudo apt-get install root and it installed CINT/ROOT. I tried to unistall it with package manager but it still show up in my applications. I have Ubuntu installed in Virtualbox so I could removing it and reinstall but I would not learn anything that way. I have tried do some searching but not had any luck. 

Thanks, Doug

---

### Post by fdrake on 2011-08-21
> **Reddoug said:**
> Hi

I mistakenly installed CINT/ROOT C/C++ on my computer running Ubuntu 10.4 LTS. I was trying to do something and it said I did not have root installed so I sudo apt-get install root and it installed CINT/ROOT. I tried to unistall it with package manager but it still show up in my applications. I have Ubuntu installed in Virtualbox so I could removing it and reinstall but I would not learn anything that way. I have tried do some searching but not had any luck. 

Thanks, Doug

i don't quite understand what kind of package you installed but you can try
```

sudo apt-get purge root
```

---

### Post by Reddoug on 2011-08-21
Hi

The program that I installed is CINT/ROOT C/C++ Interpreter. 
[http://root.cern.ch](http://root.cern.ch) is the web address that it shows. I will try the command you posted and let you know it if works.

Thanks for the help.
Doug

---

### Post by Reddoug on 2011-08-21
Hi

Tried the command and it gave me an error; Couldn't find package root.

Thanks, Doug

---

### Post by Reddoug on 2011-08-26
Uninstalled VM and reinstalled ubuntu.

Doug

---

