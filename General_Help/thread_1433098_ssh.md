---
title: "ssh"
date: 2010-03-18
forum: General Help
---

### Post by kngofbuntu on 2010-03-18
Hey Guys
I keep my sql dataabase at a server at my house & i need to scp back to my lappy(that means i cannot turn off my sshd)
people in my local network here ssh into my system and w3m sites which eats away my bandwidth
Is there a way to kill these ssh connections without actually disconnecting my ssh server??

---

### Post by spiderbatdad on 2010-03-18
so you are looking to temporarily kill the user's connection, or deny access all together?
The latter should be obvious.
If you just want to kill the connection temporarily, I would think you need the user names. Then something like ps -u <user>  Look at the pid of the sshd for that user and kill it.

---

### Post by kngofbuntu on 2010-03-18
> **spiderbatdad said:**
>  Look at the pid of the sshd for that user and kill it.
how do i do that? i tried pkill <pid>....didnt work i guess cos was able to see him when i do "finger"

---

### Post by spiderbatdad on 2010-03-18
```
w
```should show you who is logged in. Then ps -u <user>.
```
kill <pid>
``` of the sshd. Perhaps of the bash process too.

---

### Post by kngofbuntu on 2010-03-18
thanks that worked on my laptop 
but on my server it gave
-bash: kill: (30851) - Operation not permitted
do i need to change any settings??

---

### Post by spiderbatdad on 2010-03-18
killing the bash process should not be necessary. Is that what you are talking about? If it is the pid of sshd not permitted then sudo or root access is needed.

---

### Post by kngofbuntu on 2010-03-18
> **spiderbatdad said:**
> killing the bash process should not be necessary. Is that what you are talking about? If it is the pid of sshd not permitted then sudo or root access is needed.
oh how in the world did i forget sudo thanks a ton
yes killing the bash was not necessary

---

