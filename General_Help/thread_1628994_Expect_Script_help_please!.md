---
title: "Expect: Script help please!"
date: 2010-11-23
forum: General Help
---

### Post by conradin on 2010-11-23
Hi All, 
I'm trying to learn to use the automation scripting tool Expect here I have a script named ExpectPass.
On my computer I have a user account named j
So From root I try runing ./ExpectPass j
```

#!/usr/bin/expect
spawn passwd [lindex $argv 0]
set password [lindex $argv 1]
expect "password:"  
send "$password\r"
expect "password:"
send "$password\r"
expect eof

```

From there, Im just not sure how to put in a password. The shell does prompt briefly, for a "Enter new Unix password:" but its not taking input as far as I can tell.  If i type anything at this prompt I get:

```

# y7
newpass: command not found


```
If I dont type anything I end up back at the prompt.
Can anyone explain what is going on here?
This is an example from the book "Exploring Expect", Page 5
Please help!

---

### Post by sanderj on 2010-11-23
you say "**user **account named j" which you give as argument 1, bu the script puts "$argv 1" into ... $**password**

I would start by running 'passwd' just from the command line to see it's workings.
And autoexpect is always a big help in developing expect scripts

---

### Post by conradin on 2010-11-23
Yeah, I figured it out after looking at it again. The script runs fine when you pass it the arguments user-name & password. 
as in:
```

#./ExpectPass <user> <password>

```

its set up to run as root too, since if I ran it as the user j, it would ask me to retype the current password before entering the new one. 

Any ways, Ive heard of autoexpect, but I haven't located a source for it. Where can I get autoexpect?

---

### Post by conradin on 2010-11-23
[http://ubuntuforums.org/showthread.php?t=460087](http://ubuntuforums.org/showthread.php?t=460087)
solved my issues.

---

