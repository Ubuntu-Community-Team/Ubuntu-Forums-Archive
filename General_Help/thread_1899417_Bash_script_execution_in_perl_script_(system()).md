---
title: "Bash script execution in perl script (system())"
date: 2011-12-23
forum: General Help
---

### Post by Joern_MSI on 2011-12-23
Hello

I want to run a bash-script in a perl script in ubuntu.

system("bash sendthemail");

works but how can I tell him the correct directory?

system("/.../.../bash sendthemail");

does not work... how can I define the working folder correctly?

---

### Post by Shompol on 2011-12-23
"/.../.../bash sendthemail" is not a valid path, as far as I know, ../../ might be valid.  Also, do you want a path to bash or to sendmail? 

How about you add 1st line to sendmail like this:
#!/usr/bin/sh

Then you do not need to prefix command with **bash **(which should be **sh**)

It is usually best to use absolute paths in scripts, like **$HOME/myproject** not relative ones like ../..

You can probably obtain current working directory in Perl through $ENV{VARIABLE}, but my recommendation is still to try to stick to absolute paths.

---

### Post by Joern_MSI on 2011-12-23
Hello

ok thanks.

Finally I made it works with, by exchanging the bash and using first line + extension .ti:

system("/opt/abc/sendthemail.sh");

---

