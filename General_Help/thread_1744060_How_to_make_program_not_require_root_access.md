---
title: "How to make program not require root access"
date: 2011-04-30
forum: General Help
---

### Post by Pyroflea on 2011-04-30
I'm working on a PHP script that interfaces with smartmontools.  Unfortunately, to run this tool in the command line, you need root access.  I don't want to give all PHP files root access for obvious reasons.  I'm curious if there's a simple way to simply allow smartmontools (smartctl specifically) to run without needing root access.  If not, what are my other options?

Thanks,


- Jesse

---

### Post by HiImTye on 2011-04-30
[here]("https://help.ubuntu.com/community/RootSudo") is the RootSudo policy
more specifically [here]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo") is the process for allowing access without typing in a password

---

### Post by Pyroflea on 2011-04-30
> **HiImTye said:**
> [here]("https://help.ubuntu.com/community/RootSudo") is the RootSudo policy
more specifically [here]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo") is the process for allowing access without typing in a password

Thanks for your reply.  

[PHP]<?php
echo exec('whoami');
?>[/PHP]

I ran the above script, and it printed out 'www-data'.

So just confirming before I do anything, I'd just need to add:

www-data ALL=NOPASSWD: ALL

and it would allow www-data to execute the program?  Am I able to change the ': ALL' at the end to just include specific programs?

Thanks again,


- Jesse

---

### Post by Pyroflea on 2011-04-30
I tried adding that line to the end of the sudoers file.  I can't get it to work still.  The page doesn't output anything.

I've tried running a command that works:

[PHP]exec('pwd');[/PHP]

and then tried using sudo in two different methods:

[PHP]exec('sudo pwd');[/PHP]
[PHP]exec('/usr/bin/sudo pwd');[/PHP]

And nothing are working still.  'tail'ing /var/log/apache2/error.log gives me:

sudo: no tty present and no askpass program specified

What's next?

Thanks,


- Jesse

---

### Post by Pyroflea on 2011-04-30
Bump, would like to get this figured out as soon as possible!

Thanks,


- Jesse

---

### Post by Pyroflea on 2011-04-30
Nevermind, got it to work!  Had a bit of a typo (wrong username :D)

Thanks again,


- Jesse

---

