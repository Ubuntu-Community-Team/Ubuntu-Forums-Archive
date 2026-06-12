---
title: "Pass parameters to bash through Shellscript."
date: 2010-03-21
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-03-21
How do I pass file names as parameters to the shell through a script?

I have installed 'wipe' from the repos and it is a shell based app.
so I made a shellscript and put it in my script folder.

the normal usage of wipe is 'wipe -q /path/to/file'


so if I were to make a shell script, right click on the file in question, and run the script on it, how to I permit the shell to wipe that file only, in other words pass it as a parameter.


I think on windows it was the use of %1, such as.  'wipe -q %1' for example, which was simple enough.  how to I achieve this with bash?


Thanks.

---

### Post by dcstar on 2010-03-21
> **NiGhtMarEs0nWax said:**
> How do I pass file names as parameters to the shell through a script?

I have installed 'wipe' from the repos and it is a shell based app.
so I made a shellscript and put it in my script folder.

the normal usage of wipe is 'wipe -q /path/to/file'


so if I were to make a shell script, right click on the file in question, and run the script on it, how to I permit the shell to wipe that file only, in other words pass it as a parameter.


I think on windows it was the use of %1, such as.  'wipe -q %1' for example, which was simple enough.  how to I achieve this with bash?


Thanks.

The Positional Parameters are $1 $2 etc:
```
man bash
```

---

### Post by kaibob on 2010-03-21
> **NiGhtMarEs0nWax said:**
> so if I were to make a shell script, right click on the file in question, and run the script on it, how to I permit the shell to wipe that file only, in other words pass it as a parameter.

If you are going to right-click on the file while in Nautilus, a regular shell script won't do what you want. One option is a Nautilus script:

[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

An alternative is Nautilus Actions:

[http://www.grumz.net/index.php?q=taxonomy/term/2/9](http://www.grumz.net/index.php?q=taxonomy/term/2/9)

---

