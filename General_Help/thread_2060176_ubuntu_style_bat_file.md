---
title: "ubuntu style bat file?"
date: 2012-09-19
forum: General Help
---

### Post by linuxvstheworld on 2012-09-19
Are there any type of file that when you click it runs a command, similar to a .bat file in Windows?

---

### Post by cmont899 on 2012-09-19
this is generally accomplished with a shell (.sh) script:

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

---

### Post by jwbrase on 2012-09-19
Yes, they're called "shell scripts" and have the extension "sh".

You start them off (optionally) with "#!" plus the name of the shell you want to use to run the script. The rest of the file is a list of shell commands to run.

For example:

```
#!/bin/bash
echo "Hello World"
```

---

### Post by linuxvstheworld on 2012-09-19
WIll the .sh file be like an icon I can click and it'll do the command?

---

### Post by cmont899 on 2012-10-04
Yes, just navigate to where you saved the file in nautalis and double-click :D

---

