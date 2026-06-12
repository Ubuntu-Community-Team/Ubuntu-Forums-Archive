---
title: "Help install Calligra Beta 3"
date: 2011-10-30
forum: General Help
---

### Post by StephanG on 2011-10-30
On the Calligra-Suite website, it gives instructions for installing it on Kubuntu.  I added the ppa, and installed the necessary files.  But then, it says:  
> 
You can run these packages by adding /opt/project-neon/bin to your PATH.

I haven't actually done that before, could someone please tell me what it means?  And also, I can't help but notice that it adds the entire /bin directory, does this mean that every project-neon's bin is going to be added to my menus?  Because, that sounds almost like I'm going to have 2 versions of most apps in my menus.

---

### Post by StephanG on 2011-11-01
Bump?

---

### Post by StephanG on 2011-11-04
1... 2... 3...

Bump!

---

### Post by grahammechanical on 2011-11-04
It is telling you that something needs to know that the binaries (exe file in windows speak) are in the bin folder of the project-neon folder that is in the opt folder. How you do that I do not know but all it will do is tell whatever it is that is launching these packages where to look to find the package so it can be run.

Of course I could be wrong.

Regards.

---

### Post by StephanG on 2011-11-05
Thanks for clarifying.  I assumed that given the fact that adding it to "PATH" is mentioned in a single sentence, almost as an after thought, there must be a simple way to do it.  

But that "simple way" is proving surprisingly hard to track down...

Thanks anyway, I'll keep a lookout for adding directories to PATH.

---

### Post by Reiger on 2011-11-07
You need to edit your profile for that:
```

nano ~/.profile

```

Add something like:
```

if [ -d "/opt/project-neon/bin" ]; then
  PATH="/opt/project-neon/bin:$PATH"
fi

```

---

### Post by StephanG on 2011-11-13
I only checked this thread now, but thanks for that.  Much appreciated!

---

