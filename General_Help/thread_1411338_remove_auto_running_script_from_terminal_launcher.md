---
title: "remove auto running script from terminal launcher"
date: 2010-02-19
forum: General Help
---

### Post by Aimetal on 2010-02-19
When I launch terminal it tries to run bash first.
I get the following messages in the terminal window..

bash: /home/myfolder/appfolder/setup.sh: Permission Denied
myname@computername:~$

This started after I installed an application from within appfolder.
How can I remove/stop this bash from executing when I launch
the terminal window?

---

### Post by dcstar on 2010-02-20
> **Aimetal said:**
> When I launch terminal it tries to run bash first.
I get the following messages in the terminal window..

bash: /home/myfolder/appfolder/setup.sh: Permission Denied
myname@computername:~$

This started after I installed an application from within appfolder.
How can I remove/stop this bash from executing when I launch
the terminal window?

```
man bash | grep .profile
```

---

### Post by Aimetal on 2010-02-21
> **dcstar said:**
> ```
man bash | grep .profile
```

Thanks for the direction dcstar, I haven't solved this question yet as I am unable
to find the offending profile, need to read more.
I am still coming up to speed with Linux command line procedure. 
I now have a couple of books on Linux so will do some more reading. I will post 
when the mystery is solved.
Cheers.

---

