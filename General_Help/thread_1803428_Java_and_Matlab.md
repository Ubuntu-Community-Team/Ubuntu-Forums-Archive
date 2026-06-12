---
title: "Java and Matlab"
date: 2011-07-13
forum: General Help
---

### Post by Helveticus on 2011-07-13
Hello

Is openJDK or Sun java better? I want to use the JDK and JRE. I don't know which to pick.

I'm also using matlab R2011a. Now I've read that matlab installer install java. If I have installed JDK and JRE before installing matlab, will the matlab installer detect java or will it overwrite it?

---

### Post by Azdour on 2011-07-13
Hi,

Not sure if MatLab will install its own Java, but according to the docs:

[http://www.mathworks.com/products/javabuilder/requirements.html](http://www.mathworks.com/products/javabuilder/requirements.html)

They recommend Sun Java 1.6

---

### Post by Gyokuro on 2011-07-13
I always suggest to install Oracle's JDK as that's the JDK which get used by most java developers.

---

### Post by Helveticus on 2011-07-14
Now I have installed Matlab. I installed it in /usr/local/MATLAB/R2011a. This path Matlab suggested. I have it installed with sudo.

Should I choose /usr/bin instead? That means /usr/bin/MATLAB/R2011a? Because I have not installed it in this directory I can not start Matlab with the command "matlab" over terminal. I have to navigate to the Matlab directory and start it. But this should not be a serious problem, because I can create a link to it.

---

### Post by androssofer on 2011-07-14
> **Helveticus said:**
> Now I have installed Matlab. I installed it in /usr/local/MATLAB/R2011a. This path Matlab suggested. I have it installed with sudo.

Should I choose /usr/bin instead? That means /usr/bin/MATLAB/R2011a? Because I have not installed it in this directory I can not start Matlab with the command "matlab" over terminal. I have to navigate to the Matlab directory and start it. But this should not be a serious problem, because I can create a link to it.

if u open terminal go to ur home directory /home/username and then type:

```
 gedit .bashrc
```

 then add in on a new line sumwhere:

```
PATH=$PATH:/usr/local/MATLAB/R2011a
export PATH

```

it will add matlab to your path and then do 

```
source .bashrc
```

and "matlab" should work on the terminal....

---

