---
title: "SCP: Problem with copying var directory"
date: 2011-07-01
forum: General Help
---

### Post by shri19 on 2011-07-01
Hi all,

I am trying to copy /var directory in a server to another sysem using scp. Although the total size is around 6GB, the copied folder's size exceeds 80 GB or so. I am not sure what's going wrong, but I am suspecting that the directory contains some shortcut or symbolic link, and while using scp that directory is also getting copied. 

What's exactly the problem? Also it would help if i can see the complete path of files getting copied instead of just file name that's getting copied. Is there any option in scp to do so ( Display complete path of files).

Thanks in advance.

---

### Post by sam_delta on 2011-07-01
how exactly are you typing the scp command? you can add the '-v' switch to scp to make it verbose (to display its progress).

sam

---

### Post by regala on 2011-07-01
> **shri19 said:**
> Hi all,

I am trying to copy /var directory in a server to another sysem using scp. Although the total size is around 6GB, the copied folder's size exceeds 80 GB or so. I am not sure what's going wrong, but I am suspecting that the directory contains some shortcut or symbolic link, and while using scp that directory is also getting copied. 


are you sure of the 6GB size ? how do you measure it ?

br,

Mathieu

---

### Post by shri19 on 2011-07-01
> how exactly are you typing the scp command? you can add the '-v' switch to scp to make it verbose (to display its progress).[/QUOTE

I using scp as follows: scp -r "var" bckp_system@10.107.91.17:"/media/New\ Volume/". I tried using -v option, but it was not of much help in tracing down the problem.

[QUOTE]are you sure of the 6GB size ? how do you measure it ?

yes, i am pretty sure, i right click->properties as well as by du -h command. Both say the size is around 6.9GB's. 

Thanks.

Sripada

---

### Post by shri19 on 2011-07-01
> how exactly are you typing the scp command? you can add the '-v' switch to scp to make it verbose (to display its progress).I am using scp as follows: scp -r "var" bckp_system@10.107.91.17:"/media/New\ Volume/". I tried using -v option, but it was not of much help in tracing down the problem.

> are you sure of the 6GB size ? how do you measure it ?yes, i am pretty sure, i checked the folder properties and also using du command. Both say the size is around 6.9GB's. 

Is it possible that if there's a shortcut in the folder and while copying instead of just the shortcut the whole content gets copied?

Thanks.

Sripada

---

### Post by SeijiSensei on 2011-07-01
scp doesn't support the "-x" option that some other utilities use to limit copying to a single filesystem.  rsync does, though.  Give that a try.

```
cd /
rsync -avx var bckp_system@10.107.91.17:/media/New\ Volume/
```

---

### Post by shri19 on 2011-07-01
> **SeijiSensei said:**
> scp doesn't support the "-x" option that some other utilities use to limit copying to a single filesystem.  rsync does, though.  Give that a try.

```
cd /
rsync -avx var bckp_system@10.107.91.17:/media/New\ Volume/
```


Thanx for the help, It worked. But can you tell me what was actually the problem, like i said was it the shortcuts or something else??

---

### Post by SeijiSensei on 2011-07-02
Apparently your /var partition has either symbolic links that point to files or directories on other filesystems, or you have other filesystems mounted below /var.  The "-x" switch limits the copying to one file system, in this case the root filesystem where the /var directory lives. 

Imagine, for instance, that you have a symbolic link "/var/home" that points to the home partition.  Then a backup of /var would also include all the files in /home.

You could also avoid this problem by using the option not to follow symlinks, but that could leave your backup without some key links.  Limiting it to one filesystem is the better choice.  The links will be preserved, but they won't be followed if they go outside the origin filesystem.

Hope that's at least somewhat clarifying.

---

