---
title: "Duplicate a user account?"
date: 2009-10-02
forum: General Help
---

### Post by macabrem on 2009-10-02
Is there an easy way to duplicate a user account?  

Essentially, what I want to do is create a new user that has all of the same settings as another user so that way I don't have to reconfigure all of the default settings that the Ubuntu sets for a new user on my computer...

---

### Post by Giblet5 on 2009-10-02
Let's assume user "bob" and clone user "pete".

Add the new user pete with whatever tool you're comfy with.

Bring up a terminal and
```
sudo bash
cd /home/bob
tar cf - . | (cd ../pete;tar xf -)
chown -R pete:pete /home/pete
exit
```

pete is now bob's clone.

---

### Post by macabrem on 2009-10-02
> **Giblet5 said:**
> Let's assume user "bob" and clone user "pete".

Add the new user pete with whatever tool you're comfy with.

Bring up a terminal and
```
sudo bash
cd /home/bob
tar cf - . | (cd ../pete;tar xf -)
chown -R pete:pete /home/pete
exit
```

pete is now bob's clone.

Thanks. 

Can you explain the portion above that says: "tar cf - . | (cd ../pete;tar xf -)"

I've read the man page for "tar", but I'm still having trouble understanding what this command fully does.  I'm fairly new to Linux and as part of my learning process I try to understand everything I put into the CLI. 

I also wanted to make sure the "cd" in the aforementioned line wasn't supposed to be a "cp"? 

Thanks again.

---

### Post by Giblet5 on 2009-10-02
> **macabrem said:**
> Thanks. 

Can you explain the portion above that says: "tar cf - . | (cd ../pete;tar xf -)"

I've read the man page for "tar", but I'm still having trouble understanding what this command fully does.  I'm fairly new to Linux and as part of my learning process I try to understand everything I put into the CLI.  

Thanks again.


It's more a function of using the shell...

tar -cf - . = Create a tar archive on the stdout stream of everything in the current directory (.)

'|' is the character for a pipe, which tells the shell to send the output stream of the tar command to the following commands.

(cd ../pete;tar xf -) tells the shell to start a new sub-shell (stuff in parentheses) and execute a cd to another directory followed by a tar extraction of the input stream.

For tar (and many other commands) a '-' refers to stdio streams (stdin, stdout, and stderr) and is dependent on usage. The tar command 'cf -' means write on stdout, while 'xf -' means extract from stdin.

I used tar because it preserves file timestamps, but you could also use cpio and others.

---

### Post by st0nes on 2011-06-30
Or more simply you could do this
```

cd /home/olduser
sudo cp -R --preserve * /home/newuser
cd /home/newuser
sudo chown -R newuser:newuser

```

---

### Post by Halfling Rogue on 2011-09-24
Worked perfectly - statement of the obvious for newbies, don't have Firefox or other programs running while executing this script, or not all files will transfer over properly.

I have Dropbox installed and it wouldn't let me change the local folder to the new user for some reason, but desynching it and then reestablishing the connection with the new user worked fine.

Great fix, thanks a bunch. :)

---

