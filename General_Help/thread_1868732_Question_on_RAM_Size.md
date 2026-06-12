---
title: "Question on RAM Size"
date: 2011-10-24
forum: General Help
---

### Post by nihanthreddy on 2011-10-24
Hello,
I have an installed RAM of 8GB. But Ubuntu shows as 2.9GB only.
Can you please say why is it so.

---

### Post by LinuxFan999 on 2011-10-24
You probably installed the 32bit version of Ubuntu. Download and install the 64bit version of Ubuntu to access all of your RAM.

---

### Post by nihanthreddy on 2011-10-24
Well Thanks for the information.
I have one more question.
Does Ubuntu 32 bit version doesn't need more then 3GB or does it cannot handle.
And How can we see in Ubuntu is the installed version is 32bit or 64 bit.

---

### Post by tudor117 on 2011-10-24
Ubuntu 32 bit doesn't "handle" more than 3 GB of RAM.
However, if you install the PAE kernel, you will be able to use all of your ram. See [here]("https://help.ubuntu.com/community/EnablingPAE").
What version of ubuntu do you have?

Also, this command will let you know what version you have. ```
uname -a
```
"x86_64" is 64 bit.

---

### Post by CharlesA on 2011-10-24
Hrm, it should have installed the PAE kernel if you had more then 4GB of RAM.

What does this say?

```
uname -a
```

---

