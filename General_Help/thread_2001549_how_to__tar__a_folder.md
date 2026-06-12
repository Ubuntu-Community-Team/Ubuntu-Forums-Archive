---
title: "how to  tar  a folder ?"
date: 2012-06-11
forum: General Help
---

### Post by winzip on 2012-06-11
I'm writing a shell script . [COLOR=Blue]**This script will run **[/COLOR][COLOR=Blue]**under **[/COLOR][COLOR=Blue]**user's  crontab**
[/COLOR]

How do I write tar command in script ?

Do I need to  give **tar exe  path **in the below command if I want to run the script **under user's crontab ?**



```
tar czvf myfolder.tar.gz abcfolder/
```

---

### Post by codemaniac on 2012-06-11
you need to provide absolute path of myfolder.tar.gz and constituent folder abcfolder/ .

---

### Post by winzip on 2012-06-11
> **codemaniac said:**
> you need to provide absolute path of myfolder.tar.gz and constituent folder abcfolder/ .

Ok thanks.

What about the  path of  tar.exe ? Do I  need that ?  If so how do I find that ?

---

### Post by codemaniac on 2012-06-11
What is tar.exe ? Do you mean the archived file ?

---

### Post by winzip on 2012-06-11
> **codemaniac said:**
> What is tar.exe ? Do you mean the archived file ?

I mean the tar executable .

something like this ...

/usr/bin/tar  

Do I need to specify this way ?  If so how do I find the exact path for this ?

---

### Post by codemaniac on 2012-06-11
> **winzip said:**
> I mean the tar executable .

something like this ...

/usr/bin/tar  

Do I need to specify this way ?  If so how do I find the exact path for this ?

It is always better to mention the absolute path of the binaries .

Because there may be different versions of the same program might be installed on the system .


You can find the absolute path of a executable by the below command ..

```
which tar
``` 

i.e . in solaris you can find different versions of grep that has its own set of options to play with .

---

### Post by sudodus on 2012-06-11
> **winzip said:**
> I'm writing a shell script . [COLOR=Blue]**This script will run **[/COLOR][COLOR=Blue]**under **[/COLOR][COLOR=Blue]**user's  crontab**
[/COLOR]

How do I write tar command in script ?

Do I need to  give **tar exe  path **in the below command if I want to run the script **under user's crontab ?**



```
tar czvf myfolder.tar.gz abcfolder/
```

Yes, you need absolute paths wherever applicable, because the environment of crontab is very simple. Path and other environment variables, that you are used to from the terminal window are not there.

In my Ubuntu 10.04 the full path of tar is
```
/bin/tar
``` You find the location of your tar with the command ```
which tar
```
By the way, in linux there is no exe extension.

---

