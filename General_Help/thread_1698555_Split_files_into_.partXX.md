---
title: "Split files into .partXX"
date: 2011-03-02
forum: General Help
---

### Post by _0R10N on 2011-03-02
Hi everybody, I'm looking for a free alternative to split files into .partXX files. I know this can be accomplished through rar, but it's a shareware and I was wondering if there's a free alternative that accomplishes the same job.

Kind regards!

---

### Post by gmargo on 2011-03-02
See the **split(1)** command.

---

### Post by _0R10N on 2011-03-04
Thank you for your reply, but what I need is to be able to split a file the same way it's done with WinRar, so when I attempt decompress one part (on linux or windows), it extracts the other parts also, creating the original file/folder again.

regards!

---

### Post by coldraven on 2011-03-04
Have a look at krusader.
In the File>Pack window the only packer that has "multiple volume archive" enabled is rar.
As for rar being free or not I don't know. 
Edit: I just looked at Rar in the Software Centre it says that you have to register it after 40 days.
It hasn't asked me to register so far.....

---

### Post by peculiar penguin on 2011-03-04
Install 7-zip (p7zip-full), then when using the built-in archive manager (right-click on files, Compress..., select the .7z file extension) click on "Other Options" and there's your "Split into volumes of x MB" option.

---

### Post by seawolf167 on 2011-03-04
> **peculiar penguin said:**
> Install 7-zip (p7zip-full), then when using the built-in archive manager (right-click on files, Compress..., select the .7z file extension) click on "Other Options" and there's your "Split into volumes of x MB" option.

Probably the easiest way to do this and ensure Win machines can open it (i.e. not using the *split *command)

```
sudo apt-get install p7zip-full
man 7z
```

---

### Post by coldraven on 2011-03-05
> **peculiar penguin said:**
> Install 7-zip (p7zip-full), then when using the built-in archive manager (right-click on files, Compress..., select the .7z file extension) click on "Other Options" and there's your "Split into volumes of x MB" option.
Nice:D

---

