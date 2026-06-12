---
title: "having command line tools return error messages without a tty"
date: 2011-03-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-16
is there a way to have a application like tesseract retrun a error message (assuming there is one) to the application that called it lets say php
for example if you run 
```
shell_exec("man life");
```
in php it will return a empty string
but if you run it in a tty you get 
*No manual entry for life*
i would like to know if there is a way for php to get the message the app would print out in a tty
i am aware that anything that would prompt for data would cause an issue

---

### Post by tordeu on 2011-03-16
shell_exec only returns stdout and not stderr. I do not know how familiar you are with stdout/stderr, but there are basically two different "streams" where a program can output data/text to: stdout and stderr.
The "normal" output of a program is written to stdout, but errors are written to stderr. In a terminal, both stdout and stderr are displayed, so you will see everything the program outputs.

The shell_exec function, however, does only return stdout, so the error messages of the program are lost.

What you could do to get the normal output AND the errors is to append ```
2>&1[CODE] to the command you want to execute:

[CODE]shell_exec("man life 2>&1"); 
```

This will give you all the normal output AND the errors. To only get the errors, use ```
2>&1 1>/dev/null[CODE], like this:

[CODE]shell_exec("man life 2>&1 1>/dev/null"); 
```

The problem in that case is, that you lose the "normal" output of the program, so you would have to execute it another time to get the stdout(the normal output).

What you do as well is to get one of the streams directly and save another one in a file, like this:

```
shell_exec("man life 2>&1 1>out.txt"); 
```
 
This will make shell_exec return stderr (the error messages) and all the normal output is saved to out.txt, so you can get the normal output from their and don't have to execute the command twice (which sometimes is not possible).

I hope this helps you a little.

---

### Post by pqwoerituytrueiwoq on 2011-03-16
thanks i was trying to upgrade a debug console and that is not all that useful without error messages in the output

```
$user=posix_getpwuid(posix_geteuid());
$user=$user['name'];
$here=$user.'@'.$_SERVER['SERVER_NAME'].':'.getcwd().'$ ';
$debug='';
function exe($shell,$error){// String, Boolean
    $output=shell_exec($shell.($error?' 2>&1':''));
    $GLOBALS['debug'].=$GLOBALS['here'].addslashes($shell)."\n".$output.(substr($output,-1)=="\n"?"":"\n");
    return $output;
}
```
show output in inside PRE tags

---

