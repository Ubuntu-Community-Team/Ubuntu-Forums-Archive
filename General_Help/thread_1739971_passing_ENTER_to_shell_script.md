---
title: "passing ENTER to shell script"
date: 2011-04-26
forum: General Help
---

### Post by mahmoodn on 2011-04-26
Hi,
I want to write a script that runs ssh-keygen command and when it prompts for input, the ENTER key code is passed automatically for all questions.
For example consider this:
```

mahmoodserver:bin$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/mahmood/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
...

```

I want to automatically pass ENTER to the questions. What should I do?

#!/bin/bash
ssh-keygen
???

---

### Post by Krytarik on 2011-04-26
How about this command instead?:
```
ssh-keygen -q
```
>      **-q**      Silence **ssh-keygen**.  Used by system administration scripts when
             creating a new key.
[http://manpages.ubuntu.com/manpages/lucid/en/man1/ssh-keygen.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/ssh-keygen.1.html)

Greetings.

---

### Post by TeoBigusGeekus on 2011-04-26
```
yes '' | ssh-keygen
```

---

### Post by amauk on 2011-04-26
You can use the program "yes" to pass a string repeatedly to another program

By default, it'll pass 'y' to the program (hence the name), but you can specify an empty string instead

```
yes "" | ssh-keygen
```Or whatever

---

### Post by mahmoodn on 2011-04-26
Thanks
```
yes "" | ssh-keygen
``` was very handy....

ssh-keygen -q doesn't work. it still prompt for input.

the program "yes" was also new. I never heard of that. it infinitely insert y to console :D

---

### Post by mahmoodn on 2011-04-26
Sorry one more question.
Now when I want to copy that to another client I want to pass the password.

yes '' | ssh-keygen
ssh-copy-id user@client2 << PASSWORD

but it doesn't work

---

### Post by mahmoodn on 2011-04-26
Sorry one more question.
Now when I want to copy that to another client I want to pass the password.

yes '' | ssh-keygen
ssh-copy-id user@client2 << PASSWORD

but it doesn't work

---

