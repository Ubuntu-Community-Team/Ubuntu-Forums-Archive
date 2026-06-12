---
title: "Need help with very basic bash script"
date: 2010-11-12
forum: General Help
---

### Post by geo909 on 2010-11-12
Hello all,

I'm trying to write a bash script that will help me automate my backups. I'm not really familiar with bash scripting so any help with the following would be much appreciated:

I want to execute a command (that btw includes a bunch of arguments) and I want to use the exit status of the command in an if statement. That is "if command was executed succesfuly, then do this and that, if it returned an error, then give warning message and stop".

More precisely the command I want to execute is:
```
sudo mount -t ntfs-3g $TSUNAMIID /media/TSUNAMI -rw
```
where
```
TSUNAMIID='/dev/disk/by-id/usb-ST950042_0ASG_ST9500420A_5VJ2GE2M-0\:0-part1'
```

I'm trying something like the below, but it doesn't work:

```
if [sudo mount -t ntfs-3g $TSUNAMIID /media/TSUNAMI -rw]
 22 
 23   then
 24         echo -e "Success\n"
 25         backup
 26         exit 0
 27   else
 28         echo -e "Failed\n"
 29         exit 1
 30   fi
 31 fi
 32 
 33 exit 0

```

Any ideas? 

Thank you for your time

---

### Post by endotherm on 2010-11-12
In what way does it not work? btw you may want to add a bang line at the top of your script:
```
#!/bin/bash
```well, I am not familliar with the syntax you are using to get the disk id, but my first step would be to put the whole command together without the var, and run it to see if it works. if so, then there is an issue wiht the way the command string is being intrepereted, and some varient of quoting will work. if not, then you need to revise the content of your variable expression.

so, does this command run in the terminal?
sudo mount -t ntfs-3g '/dev/disk/by-id/usb-ST950042_0ASG_ST9500420A_5VJ2GE2M-0\:0-part1' /media/TSUNAMI -
rw
the problem may be your single quotes. single quotes are for literal strings. double quotes act as literal except if they contain a variable (denoted with $) . backquotes ( ` on your tilde key) explicitly execute whatever is within them, so make sure it;s executable.
echo "hello `date`" 
returns 
hello Fri Nov 12 00:45:07 EST 2010

---

### Post by geo909 on 2010-11-12
> **endotherm said:**
> well, I am not familliar with the syntax you are using to get the disk id, but my first step would be to put the whole command together without the var, and run it to see if it works. if so, then there is an issue wiht the way the command string is being intrepereted, and some varient of quoting will work. if not, then you need to revise the content of your variable expression.

Hi and thanks for the reply. The command itself works perfectly if run from a terminal. I also tried to replace $TSUNAMIID with the whole path, but the result is the same.

Here is the script that I have so far:
```
#!/bin/bash                                                                                                                                                                           

BACKUPHD='/media/TSUNAMI'
TSUNAMIID='/dev/disk/by-id/usb-ST950042_0ASG_ST9500420A_5VJ2GE2M-0\:0-part1'


backup() {
        echo -e "Running Unison to backup to $BACKUPHD\n"
}

if grep $BACKUPHD /etc/mtab
  then
   backup
  exit 0

else

  echo "TSUNAMI drive is not mounted! Attempting to mount.."
 
  if [sudo mount -t ntfs-3g  /dev/disk/by-id/usb-ST950042_0ASG_ST9500420A_5VJ2GE2M-0\:0-part1 /media/TSUNAMI -rw]

  then 
        echo -e "Success\n"
        backup
        exit 0
  else
        echo -e "Failed\n"
        exit 1
  fi  
fi

exit 0

```

Also, here is what I get when I execute it:

```
jorge@flamingo:~$ sh backup.sh
TSUNAMI drive is not mounted! Attempting to mount..
backup.sh: 30: [sudo: not found
-e Failed

```

Any ideas?

---

### Post by endotherm on 2010-11-12
sorry, you got me while I was editing my post. as I posted above (late) I think the problem is that your /dev/disks/... command is in single quotes (it is a command, right?) and is thus being treated as a string.
I would echo out the command string to see what it is after everything is concatenated in, and test to make sure that the echoed string executes.

Ahh, I must be going blind. the problem looks to be the sudo. take it out, and instead, launch your script with sudo.

---

### Post by DaithiF on 2010-11-12
you are muddling up the 'if' and '[' commands

either do it this way:
```
if command; then
    # do stuff
fi
```

or:
```
command
if [ $? -eq 0 ]; then
   # do stuff
fi

```
and note that when using [ you need to leave a space either side of the [ symbol.

---

### Post by geo909 on 2010-11-12
Hi, and thank you for your replies

I actually gave it a thought and realized that I'd prefer to avoid sudo commands inside the scripts, as I would like to assign a a keyboard shortcut and make "one-button" backups..

But, for my future reference, the code below
```
if command; then
    # do stuff
fi
``` 

works even if "command" has arguments in it, like in my case (I would try it myself but I'm not going to be home for a while)?

---

