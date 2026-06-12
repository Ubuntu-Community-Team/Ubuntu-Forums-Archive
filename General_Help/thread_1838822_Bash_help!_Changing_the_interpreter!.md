---
title: "Bash help! Changing the interpreter!"
date: 2011-09-04
forum: General Help
---

### Post by bsreram85 on 2011-09-04
Hello,

This may be a simple task for most of the linux users, but as a newbie i  find this difficult to do. I were participating in a competition which  mandated me to change the interpreter by executing the command  '#!/usr/bin/bash' via shell script. But i found out like the bash file  was in '/bin' folder instead of '/usr/bin' folder. So i changed it to  appropriate path and executed the script. Unfortunately, it gives the  'bad interpreter' message. Whats strange is that if i execute it via  terminal (instead of putting it in a script and running it ), it  executes perfectly fine without any errors. Can any body point out the mistake i might be doing wrong here?

---

### Post by FormatSeize on 2011-09-04
No offense, but it's difficult to discern what you are talking about. When you executed the command without using the terminal, how was it that you executed it? Also, if you can execute the command, why does it matter whether you used the terminal or not?

---

### Post by zero2xiii on 2011-09-04
oka, 

It seems like you have very little scripting background. I am by no measure a professional.

every linux script starts with a line "#!/bin/bash"

This is the line that determines the "interpreter" as far as I understand it. So as far as the competetion goes, change that line to the syntax/path they give you.

If your srcipt is lacking this line, it WONT be executable as a scrip inside (or out) of a terminal.

Example of a simple script to show syntax:

```

#!/bin/bash

clear   ##clears the terminal screen
echo "Hello linux!"   ##Echoes the words hello linux to the terminal

exit  ##Exits

##You need to append an empty line to the end of the file after the last line of code.
##this is comment lines, you can use a single #, but I prefer to use two.


```

---

### Post by idoitprone on 2011-09-04
> **zero2xiii said:**
> oka, 

It seems like you have very little scripting background. I am by no measure a professional.

every linux script starts with a line "#!/bin/bash"

This is the line that determines the "interpreter" as far as I understand it. So as far as the competetion goes, change that line to the syntax/path they give you.

If your srcipt is lacking this line, it WONT be executable as a scrip inside (or out) of a terminal.

Example of a simple script to show syntax:

```

#!/bin/bash


```

Actually all scripts are run as a subshell of the parent process, which means it is run inside the current termianal

[http://tldp.org/LDP/abs/html/subshells.html](http://tldp.org/LDP/abs/html/subshells.html)

```
#!/bin/bash

```line only tells which shell should be used. The script might excute depending on the distro, in most cases it will. If not specified, it defaults to the default shell. In Ubuntu the default is dash shell. Beware of special bash features such as the bracket if statements. It will fail in dash

---

### Post by sisco311 on 2011-09-04
@idoitprone
The infamous "Advanced" Bash Scripting Guide should be avoided unless you know how to filter out the junk. It will teach you to write bugs, not scripts. In that light, the BashGuide was written: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)


@OP: [http://homepages.cwi.nl/~aeb/std/shebang/](http://homepages.cwi.nl/~aeb/std/shebang/)
the Wikipadia page is quite accurate too:
[http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

---

