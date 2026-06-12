---
title: "How to backup from an old mysql in a hard drive?"
date: 2011-05-04
forum: General Help
---

### Post by micael3000 on 2011-05-04
Hello!

How to backup from an old mysql in a hard drive?
I have this HD which used to have an Ubuntu 7.04... However, the system crashed and it is not possible to boot anymore.
I have moved the HD to another computer and made a copy for every important file and folder... But I am facing trouble to backup mysql... To copy /etc/lib/mysql doesn't work because it is probably in an older version from the mysql I use on Ubuntu 10.10...

Does anyone know how to do that?

Thanks in advance :)

---

### Post by micael3000 on 2011-05-04
Bump :(

---

### Post by micael3000 on 2011-05-06
I just gave up by using an OOOOLD backup... :S

---

### Post by Ghost|BTFH on 2011-05-06
Hi Michael,

I think the issue here is: "To copy /etc/lib/mysql doesn't work because it is probably in an older version from the mysql I use on Ubuntu 10.10..."

Instead of telling us what you *think* is the problem, please explain what the problem is, in detail.

Example:

"I attempted to copy files from /etc/lib/mysql on the old hard drive to my new one, but it is not allowing the files to be copied...I am using this command to copy:

cp -druv * media/oldhardrive/etc/lib/mysql /etc/lib/mysql

and it tells me that this is denied."

See, in the above situation, I could tell you instantly that you forgot to use:

sudo cp

instead of

cp

and the problem would be solved quickly and easily.  So please, if you can, explain exactly what you want it to do, what you are trying to make this happen, and what the error is when you attempt to do so and it fails.

Cheers,
Ghost|BTFH

---

