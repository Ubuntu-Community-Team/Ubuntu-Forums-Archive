---
title: "loop commands in bash scripting"
date: 2010-05-15
forum: General Help
---

### Post by eshadcloud on 2010-05-15
What is the difference between For and While when creating loops in bash scripting?

---

### Post by patchwork on 2010-05-15
Long story short, while loops will execute until a set condition is satisfied and for loops iterate through a sequence until the sequence is completed.

The bash man page has a full explanation:

> while list; do list; done
       until list; do list; done
              The while command continuously executes the do list as  long  as
              the  last  command  in list returns an exit status of zero.  The
              until command is identical to the while command, except that the
              test  is  negated;  the  do list is executed as long as the last
              command in list returns a non-zero exit status.  The exit status
              of  the  while and until commands is the exit status of the last
              do list command executed, or zero if none was executed.
> for name [ [ in [ word ... ] ] ; ] do list ; done
              The list of words following in is expanded, generating a list of
              items.  The variable name is set to each element of this list in
              turn, and list is executed each time.  If the in word  is  omit&#8208;
              ted,  the  for  command  executes  list once for each positional
              parameter that is set (see PARAMETERS below).  The return status
              is  the  exit  status of the last command that executes.  If the
              expansion of the items following in results in an empty list, no
              commands are executed, and the return status is 0.
See ```
man bash
```for more information.

A handy little way to read information from files is to use a while loop like this:

while read some_variable; do
    some_command
done < some_file

---

