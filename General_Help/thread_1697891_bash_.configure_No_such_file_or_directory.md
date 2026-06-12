---
title: "bash: ./configure: No such file or directory"
date: 2011-03-01
forum: General Help
---

### Post by ftabor on 2011-03-01
I get this error when trying to compile a legacy program to install. I have build-essentials and checkintall installed. I am in the directory containing the extracted files.

---

### Post by seawolf167 on 2011-03-01
Type 

```
ls
```

is the file there?

Is there a README?

---

### Post by ftabor on 2011-03-01
> **seawolf167 said:**
> Type 

```
ls
```

is the file there?

Is there a README?

No, there is no configure file there. 

Yes, README is there, but there is only a reference to the URL for Thunderbird Release, which takes you the page to install the current release. I have that, I need to install a legacy version.

---

### Post by oldos2er on 2011-03-01
Look for an executable named thunderbird or thunderbird-bin

---

### Post by ftabor on 2011-03-01
I can run thunderbird with by only opening the file from nautilus, but it isn't installed properly. Running thunderbird from the command line starts the currently installed version. Running it from a tmp directory in the Download directory isn't the way to do it. None of the install files will "run".

---

### Post by ftabor on 2011-03-01
I guess the tar.gz file downloaded is the "runnable" program. I just need to find a way to install the legacy program along side the current program.

---

