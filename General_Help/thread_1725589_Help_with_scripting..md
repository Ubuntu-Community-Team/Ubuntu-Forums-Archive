---
title: "Help with scripting."
date: 2011-04-09
forum: General Help
---

### Post by Mr_VeRiTy on 2011-04-09
Hi, I don't know much about scripting, but I need a script that runs the command:
wget -O [output file]  [URL]

Then sleeps for 5 minutes, and then repeats.

Can somebody help me with this?

---

### Post by Old *ix Geek on 2011-04-09
> **Mr_VeRiTy said:**
> Hi, I don't know much about scripting, but I need a script that runs the command:
wget -O [output file]  [URL]

Then sleeps for 5 minutes, and then repeats.

Can somebody help me with this?

Here you go:

```
#!/bin/bash
while :
do wget -O output_file URL
sleep 300
done

```

Obviously, replace **output_file** and **URL** with the output file's name and the correct URL.

The sleep command is counted in seconds, hence 300 is 5 minutes.

---

### Post by Mr_VeRiTy on 2011-04-09
> **Old *ix Geek said:**
> Here you go:

```
#!/bin/bash
while :
do wget -O output_file URL
sleep 300
done

```Obviously, replace **output_file** and **URL** with the output file's name and the correct URL.

The sleep command is counted in seconds, hence 300 is 5 minutes.

Thanks!:D

---

### Post by Old *ix Geek on 2011-04-10
> **Mr_VeRiTy said:**
> Thanks!:DYou're very welcome.

---

