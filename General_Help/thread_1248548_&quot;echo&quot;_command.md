---
title: "&quot;echo&quot; command"
date: 2009-08-24
forum: General Help
---

### Post by mechanic on 2009-08-24
I am puzzled with the use of this command, there appear to be two versions of "echo" in the system, one a shell built-in and one at /bin/echo. Although I cannot reproduce this with a simple command line test, the use of the "-e" option to expand newlines seems different as used in scripts. 

One perl script I'm using to tidy email before printing looks a bit like this:
```

#!/usr/bin/perl

$head = "";
$body = "";
$newbody = "";

while (<>) {
        if (1 .. /^$/) {
                $head = $head . $_;
        } else {
                $body = $body . $_;
        }
}

# The range selects the head of the mail, from the first line to the first
# blank line.
#
#...omitting some lines to help problems with ' and " characters

$newbody = `/bin/echo -e '$body'|par 88`;

 print ($head,$newbody) ;

```

If I use the line:

 $newbody = `echo -e '$body'|par 88`

instead the result is different and I have to omit the -e parameter.

par is just a formatter like the "fmt" command.

What is going on?

Regds, m.

---

### Post by geirha on 2009-08-24
I'm guessing `command` in perl runs command in a shell, and that it uses /bin/sh as the shell to run the command in. If so, then `echo` will use the builtin echo of that shell, which by default is dash (/bin/sh is a symlink to /bin/dash). Dash's echo is very limited; the only command-line option it accepts is -n.

---

### Post by mechanic on 2009-08-25
> **geirha said:**
> I'm guessing `command` in perl runs command in a shell, and that it uses /bin/sh as the shell to run the command in. If so, then `echo` will use the builtin echo of that shell, which by default is dash (/bin/sh is a symlink to /bin/dash). Dash's echo is very limited; the only command-line option it accepts is -n.

Thanks for the reply - yes that seems very plausible. A quick test shows that dash behaves as if "-e" was the default, whereas bash has "-E" as default (it doesn't expand /n into newlines). Maybe 'Programming Perl' should include a note about this!

Thanks again!

Regds, m.

---

