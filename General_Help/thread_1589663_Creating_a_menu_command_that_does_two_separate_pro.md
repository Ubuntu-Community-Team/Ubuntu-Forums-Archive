---
title: "Creating a menu command that does two separate processes in terminal"
date: 2010-10-06
forum: General Help
---

### Post by kolo-01 on 2010-10-06
this should be quite an easy one for anyone who knows- i am trying to create an icon with a command in the main menu that first kills an application and then opens another, i am able to perform the commands separately, but can't work out how to execute them both in the same main menu command, maybe there is something to write in-between the commands, or is this process not possible?

---

### Post by ridgeland on 2010-10-09
Here is a snipet from my bash script that records a video from my TV tuner card:
```
    if [[ $YesNo == "Y" || $YesNo == "y" || $YesNo == "" ]]; then
        cat /dev/video0 > $SaveAs &
        ### assume that the PID of the command is $!
        ### assumptions can be dangerous
        my_PID=$!
        sleep $count_secs
        kill -15 $my_PID
    else
        echo "Since you did not hit \[Enter\] or enter Y or y program aborted - No recording"; echo
    fi
```
Don't know if it fits but maybe food for thought.
It starts a "cat" command.  Gets a PID then does some stuff (record for $count_secs seconds) Then kills that process and goes on with the script.
Does 
$ ps -el | grep first_application_to_kill
give you the PID you need to kill?

---

### Post by dcstar on 2010-10-09
> **kolo-01 said:**
> this should be quite an easy one for anyone who knows- i am trying to create an icon with a command in the main menu that first kills an application and then opens another, i am able to perform the commands separately, but can't work out how to execute them both in the same main menu command, maybe there is something to write in-between the commands, or is this process not possible?

```
command_1 & command_2
```

If you want #2 to wait until #1 finishes:

```
command_1 && command_2
```

---

### Post by rcayea on 2010-10-09
I believe, and I may be wrong, that the "&&" is a way to be sure that command_1 starts and if it doesn't succeed, then command_2 won't start. I guess like a safety measure.

---

