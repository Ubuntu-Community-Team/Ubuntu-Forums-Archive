---
title: "Setuid and setgid on a shell script"
date: 2012-03-15
forum: General Help
---

### Post by rpaskudniak on 2012-03-15
Hi Family.

I have known about the setuid/setgid flags for decades but I have never had to put it to the test. I had though that if an executable file owned by, say user postgres, has the setuid/setgid flags turned on, then any user running that file would be running with the effective UID of postgres.  I wrote a tiny shell script to test this out: It writes a 2-line file to /tmp.  I ran it as user rasp, group users.  I expected the ownership on the output file to be postgres/postgres.

Ah, no!

The output file ownership was still rasp/users.  It should be explain that at this I am pained. :guitar:

A search of these forums found a [_[COLOR="Navy"]thread that explains a little[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1853754&highlight=setuid+owner"): That the setuig/gif flags work only for a binary executable but not for shell script.

If that's just the way it is, so be it.  But does anyone know of a rationale for this?  Or the mechanics, for that matter?  Does the shell deliberately force permissions to be the realy UID/GID rather than the effective UID/GID?  (I would scorn the idea that the OS knows that the shell actually writing the file is running a script; it's still a binary executable issuing the write() service calls.)

I happen to be using ksh to run the script but I just got the same result using bash.  Sherlock looking for clues... ;)

---

### Post by kjohri on 2012-03-15
The reason may be that if setuid and setgid were allowed on a shell script, it would result in running a superuser shell, which is not desirable. The recommended practice is to run individual commands with sudo.

---

### Post by papibe on 2012-03-15
Hi rpaskudniak.

I've read several articles in the past that described that allowing setiud on shell scripts is a "serious security hole". Unfortunately, I don't remember the specifics.

I'm no expert on the matter, but I'm almost sure that what is happening to you is done by design (most certainly a decision made by the distribution).

In the same direction: Let's say you have a shell script called myscript.sh that starts with:
```
#!/bin/bash
...
...
```
If you run it, it won't be actually loaded in memory since it does not actually contain machine code. That line '#!/bin/bash' is sort of like a shortcut that tell the OS to do something similar to:
```
/bin/bash -f myscript.sh
```
Then bash would be actually setting uid and guid instead of the file with the instructions.

Does that make sense?

Just some thoughts.
Regards.

---

### Post by rpaskudniak on 2012-03-16
Guys,

Thank you for the logical replies.  However, I might take issue with security that, since I cannot write a shell script, chown root, and then chmod it with setuid,  And if I chmod it first and then chown to root, the OS will automatically turn off the setuid/gid flags.  I still remember this from the first K&P book on Unix.

So let's look at papipe's explanation: When I run a script from my shell, it spawns another shell, which does NOT have the setuid flag.  That shell is reading the file for me and running the commands as ME, rasp, not as postgres, the owner of the file.

By this logic, the setuid script should be unable to read a file with 600 permission owned by postgres.  I just tested this hypothesis and, indeed, the read failed.

Conclusion: Setuid/gid on a script file is a fairly useless operation.

papipe, thanks for the jump-start on a very logical explanation of the problem.

I'd be quite interested if someone can come up with a use for doing this.

(I hope marking this SOLVED does not close the thread.)

---

