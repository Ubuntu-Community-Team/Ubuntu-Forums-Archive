---
title: "Regarding permission Problem"
date: 2010-11-21
forum: General Help
---

### Post by abhay2101 on 2010-11-21
Hi,
 I have one a.out which i had created in my home diirectory.i am able to read write execute everthing in my home folder. 
But when i move the same a.out file to other mounted partion(Partiton which used to get mounted automatically by ubuntu). i am not able to execute it and it is giving some permission denied problem.
I tried running it as root user it didn't worked.
I tried chmod -Rf 777  but this command was not able to change the permissions.
Please let me know what needs to be done to execute my file from the other monted partiton.

Thanks in advance
Abhay Kumar

---

### Post by papibe on 2010-11-21
What kind of disk is it? Is it ntfs?  Could you post the result of disk commmad:
```
$ mount -l
```
Regards.

---

### Post by asmoore82 on 2010-11-21
```
mount -l
```[size=3]+1[/size]
Sounds like your other partition is either not in a Linux format,
-OR- it is having the "noexec" security option set when it is being mounted.

You should _***[COLOR="Red"]not[/COLOR]***_ have execute permission on all plain files in your Home Folder.

You should ***_[COLOR="Red"]never[/COLOR]_*** `chmod -R` in combination with `777`
The only proper forms of `chmod -R` are `chmod -R +rw`, `chmod -R -w`, `chmod -R +rwX`, etc.

---

