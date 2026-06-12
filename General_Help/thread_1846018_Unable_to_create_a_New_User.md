---
title: "Unable to create a New User"
date: 2011-09-18
forum: General Help
---

### Post by Zephilinox on 2011-09-18
> **anur.bhargav said:**
> I'm not able to create a 'New User Account' using either the graphical method or the command line...
This is the message I get when doing it using command line (See Image Attached).
Please Help...:D:p

try chmodin' it

```
chmod 755 /etc/passwd
```

if that doesn't work, use sudo chmod.

---

### Post by anur.bhargav on 2011-09-18
I'm not able to create a 'New User Account' using either the graphical method or the command line...
This is the message I get when doing it using command line (See Image Attached).
Please Help...:D:p

I am Using Ubuntu 11.04

---

### Post by anur.bhargav on 2011-09-18
Will Try and report back..

---

### Post by anur.bhargav on 2011-09-18
> **Zephilinox said:**
> try chmodin' it

```
chmod 755 /etc/passwd
```

if that doesn't work, use sudo chmod.
Same thing :(

---

### Post by psrdotcom on 2011-09-18
Have you tried the GUI mode of User Creation? 

Please let us know the result

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by Toz on 2011-09-18
Also, have a look here with regards to lock files: [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896]("https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896")

---

### Post by anur.bhargav on 2011-09-18
> **psrdotcom said:**
> Have you tried the GUI mode of User Creation? 

Please let us know the result

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Yes I Have and the screenshot shows what I get as a response.

---

### Post by anur.bhargav on 2011-09-20
Please help...

---

### Post by Toz on 2011-09-20
What does the following command return:
```
ls /etc/*.lock
```

---

### Post by anur.bhargav on 2011-09-22
> **Toz said:**
> What does the following command return:
```
ls /etc/*.lock
```

Here's the output of ```
ls /etc/*.lock
```
See Attachment.

---

### Post by anur.bhargav on 2011-09-22
I also get these errors every time I Install/Remove any program.

I guess both 'Unable to create a new user' and 'These errors' are interconnected after reading a pair of bug reports.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202682&d=1316679007[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202683&d=1316679007[/IMG]

---

### Post by anur.bhargav on 2011-09-22
> **Toz said:**
> What does the following command return:
```
ls /etc/*.lock
```


Toz Ur The King:popcorn::p:D

Ur latest post made me understand the importance of the bug report u previously posted. The title of the bug report had confused me. I just followed the solution given there.

Thanks a Ton !!

(For other people who get the same error)
This is what I did
> 
SOLUTION:
Look for /etc/group.lock, /etc/passwd.lock and /etc/shadow.lock files and remove them.

Be careful to only remove the files ending in 'lock' or else you might damage your system.

the list of locked files may be
1. /etc/passwd.lock 
2. /etc/shadow.lock 
3. /etc/group.lock 
4. /etc/gshadow.lock

And these were the lock files I had (Though I don't know how and where they came from)
> /etc/passwd.lock  & /etc/shadow.lock

The Install/Remove program error that I mentioned in the previous post is indeed connected and that too is solved. There's no error returned now :)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202684&stc=1&d=1316680848[/IMG]

---

### Post by Toz on 2011-09-22
Glad to hear it worked out for you. Can you please mark this thread as solved from the Thread Tools link above so that others can benefit as well? Thanks.

---

