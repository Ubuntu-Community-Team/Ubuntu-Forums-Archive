---
title: "linux file permission xxxx, why 4 digits?"
date: 2009-08-05
forum: General Help
---

### Post by cpthk on 2009-08-05
I worked with ubuntu for awhile now. Mostly, if I do chmod, the file permission would be something like 666, 777, 700. But I have seen some documentations that ask me to change permission to 0700. Why is there 4 digits? What does that extra digit mean?

Thanks.

---

### Post by mcduck on 2009-08-05
In addition to the normal read/write/execution permissions there are couple of special options.

I can't remember the numbers for octal notation, but with symbolic notation you'll find that permissions for directories starts with a "d". Then there's "setuid" and "setgid", which makes the programs run as the owner (or group) of the executable file instead of the user who starts the program, and "sticky bit" which is used for all kinds of different purposes on different Linux/Unix systems.

edit:
[http://en.wikipedia.org/wiki/Sticky_bit]("http://en.wikipedia.org/wiki/Sticky_bit")
[http://en.wikipedia.org/wiki/Setuid]("http://en.wikipedia.org/wiki/Setuid")

---

### Post by cpthk on 2009-08-05
so that sticky bit can be only 0 or 1? or it could be 2,3,4...

---

### Post by aesis05401 on 2009-08-05
There is a table that explains it all clearly.  Follow the link:[http://www.zzee.com/solutions/unix-permissions.shtml#setuid]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid")

---

### Post by kjohri on 2009-08-06
The permissions are xxxx in octal. The first digit is for set user-id (4), set group-id (2) and restricted deletion/sticky (1). The second digit is for the owner of the file, read (4), write (2) and execute (1). The third digit is for the other users in file's group and the fourth digit is for other users not in file's group.

---

