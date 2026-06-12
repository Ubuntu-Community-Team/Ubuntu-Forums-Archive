---
title: "Setting password to an user through a shell (Bash) script"
date: 2010-09-22
forum: General Help
---

### Post by yerba_mate on 2010-09-22
Hello to all

Let's assume that we have the next script to create a new user in the system:

```

#!/bin/bash

useradd a_user --password its_password --groups its_group


```where we want to create the user `[FONT=Courier New]`[/FONT][FONT=Courier New]a_user[/FONT]'' that belongs to the group ``[FONT=Courier New]a_group[/FONT]'' (that already exists) and we try to set the password as ``[FONT=Courier New]its_password[/FONT]''.

The problem is that if we try to execute the script creates all perfectly, except for the password. When we try to log in to the system with the user that we just created simply we cannot.
When we take a look to the ``[FONT=Courier New]/etc/shadow[/FONT]'' file we encounter that the password field of the user ``[FONT=Courier New]a_user[/FONT]'' it's filled with the string ``[FONT=Courier New]its_password[/FONT]'' (not encripted).

The question is: How we can set the new user's password through a script, without using ``[FONT=Courier New]passwd[/FONT]'' in an interactive way.

P.S.: Any suggestions to improve my English are welcome!


Thanks in advance
Greetings,
yerba_mate

---

### Post by bodhi.zazen on 2010-09-22
There are several tutorials on how to do this on the web, I have not tried it recently, see:

[http://www.howtoforge.com/how-to-add-linux-system-users-from-a-text-file](http://www.howtoforge.com/how-to-add-linux-system-users-from-a-text-file)

[http://www.cyberciti.biz/tips/howto-write-shell-script-to-add-user.html](http://www.cyberciti.biz/tips/howto-write-shell-script-to-add-user.html)

---

### Post by BobVila on 2010-09-22
I've done something similar with python. The advantage here is that I don't have to type the password into the terminal for anyone with access to my history or line of sight to the monitor to see.

It's called by './uadd.py username', then prompts for a password to assign to the user. The input isn't shown on screen.

If you'd like, I can post relevant snippets. If you're dead-set on bash script, I won't be much help.

---

### Post by luvshines on 2010-09-22
I generally use expect scripts for those kind of stuffs

---

### Post by CharlesA on 2010-09-22
> **bodhi.zazen said:**
> 
[http://www.cyberciti.biz/tips/howto-write-shell-script-to-add-user.html](http://www.cyberciti.biz/tips/howto-write-shell-script-to-add-user.html)

That script works fine. :)

If you are batch adding users, I believe you can just assign variables for the password and read a text input or a file for the variables.

---

### Post by bodhi.zazen on 2010-09-22
> **CharlesA said:**
> That script works fine. :)

Thank you for confirming that, it has been a while since I have wanted to script adding users.

---

### Post by yerba_mate on 2010-09-23
Thanks to all for the replies!

I solved the problem using the command [FONT=Courier New]chpasswd[/FONT]:

[FONT=Courier New]echo "a_user:its_password" | chpasswd[/FONT]

Cheers,
yerba_mate

---

