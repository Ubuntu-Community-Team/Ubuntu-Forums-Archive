---
title: "File access problem"
date: 2009-07-18
forum: General Help
---

### Post by ghoy on 2009-07-18
Hey Ubuntu,

I'm running a shell script and it needs to run some other scripts when I'm running it. The other scripts are in the sub_directories. 

The whole thing is inside /idl_pros folder. Some one gave me the whole thing so I can use the scripts. The first file that I usually run is under idl_pros folder and other scripts are in sub-folders of idl_pros. I tend to keep them in those folders because this way its cleaner and not messy. But My script (the first one) can't reach and call the others in the subfolers, 

so I did take them out and put them all in idl_pros. this time the script runs just fine. 

I need to know what exactly is my problem, and then How can I fix it?

Thanks

---

### Post by master_kernel on 2009-07-18
Are you running the script from the idl_pros folder? IOW, does pwd give /idl_pros?

Is the first script referring to the other scripts correctly? Is it referring to their path names right? EX: mydir/script2.sh INSTEAD of ./script2.sh.

---

### Post by ghoy on 2009-07-18
like i said the script runs when all the files are in idl_pros. but not when they are in subdirectories.

:D

---

### Post by michy99 on 2009-07-18
If you change the location of the files, then you have to change the script to refer to the new locations.

---

### Post by master_kernel on 2009-07-18
> **michy99 said:**
> If you change the location of the files, then you have to change the script to refer to the new locations.
What he said, and what I said in my first post.

---

### Post by ghoy on 2009-07-18
i have worked with this script in my friends machine. I copied the whole thing (kept the same directory structure) and the tried to run them. For some reason the first script does not like the other scripts to be in sub-directories any longer. but when I take all of those scripts out of the sub directories ( I do not change any thing in the scripts) the whole thing works like the way it was on my friend machine.

---

### Post by master_kernel on 2009-07-18
Can you post the orig. script?

---

### Post by ghoy on 2009-07-18
Before I post the script I have to add this, I think the is some ownership problem in the sub-folders. I have not tired that and I'm not sure that if it will help.

---

### Post by master_kernel on 2009-07-18
You would need to chmod 755 the subdirs. You won't need to mess w/ the files if they work fine in the root dir.

---

### Post by ghoy on 2009-07-18
can you writ the exact command?

---

### Post by master_kernel on 2009-07-18
```
cd idl_pros
chmod -R 755 *
```

---

