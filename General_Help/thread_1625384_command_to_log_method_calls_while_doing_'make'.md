---
title: "command to log method calls while doing 'make'"
date: 2010-11-19
forum: General Help
---

### Post by celeritas9 on 2010-11-19
Hi,

I am building an android, from the source using make command.
I want to achieve simple logging while this make is happening.

[COLOR="Blue"]Aim:[/COLOR]

I want to look/log for internal system calls that are being made after i do 'make' command in bash terminal. So that after the make is done, i can look and study the internal method/file calls made while make was happening. In this way i will come to know how the actual building process works.

Please if you have any other suggestions to achieve this let me know.

Help appreciated.

Thanks, cheers.

---

### Post by gmargo on 2010-11-19
> **celeritas9 said:**
> Hi,

I am building an android, from the source using make command.
I want to achieve simple logging while this make is happening.

[COLOR=Blue]Aim:[/COLOR]

I want to look/log for internal system calls that are being made after i do 'make' command in bash terminal. So that after the make is done, i can look and study the internal method/file calls made while make was happening. In this way i will come to know how the actual building process works.

Please if you have any other suggestions to achieve this let me know.

Help appreciated.

Thanks, cheers.

If you seriously want to see what "internal system calls" were used, use the **strace** command.  See the strace man page for more info.

However, I'm not sure this will tell you "how the actual building process works."  It's going to be far too much detail.  Perhaps I misunderstand what you want.  Maybe the "-d" debug flag on the make command is more what you're looking for.  Or do you just want to capture the printed output of the make command, which you can do with simple redirection?

---

