---
title: "[SOLVED] Help needed: autogen.sh problems in bash"
date: 2006-05-10
forum: General Help
---

### Post by RavenOfOdin on 2006-05-10
When I try to run the script autogen.sh from a bash command line it gives me the message

> 
./autogen.sh: Permission denied


So I then set exec permissions on the file with:

> 
chmod a+x autogen.sh


and try again, but now I get. . .

> 
bash: ./autogen.sh: /bin/sh^M: bad interpreter: No such file or directory


Does anyone know what might be wrong, and if its a bug in bash or sh?
I'd appreciate a couple of words on this seeing as I have to compile this *yesterday* for a project I'm working on. Thanks.

---

### Post by kabus on 2006-05-10
```
bash: ./autogen.sh: /bin/sh^M: bad interpreter: No such file or directory
```

The '^M' is the problem, since bash is looking for '/bin/sh^M' instead of '/bin/sh' and not finding it for obvious reasons.
Make sure there's no character after '#!/bin/sh', not even a space.

Edit : Was this file created under Windows? It seems that the difference between Dos and Unix newline characters can lead to those '^M's.
More info here : [http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline)

---

### Post by RavenOfOdin on 2006-05-10
This project runs on both Win32 and Linux, and the person who sent me this autogen file seems to use Windows, so you might have something there.

I'll get on my Linux box, see if there are any spaces or characters after #!/bin/sh and then get back to you.

---

### Post by RavenOfOdin on 2006-05-10
No spaces or other characters are after that line, but I still get the same message.

---

### Post by RavenOfOdin on 2006-05-10
OK there we go, had to copy and save the file over again.
Apparently the loser that sent it saved EVERY single file in DOS format.

Its going to be a long reconfiguration. Lol.

(EDIT: Yay, temporary solution found, use Kate until my eyes bleed.)

---

### Post by kabus on 2006-05-11
[QUOTE=RavenOfOdin]OK there we go, had to copy and save the file over again.
[/QUOTE]
Here's a site that explains some command line ways of conversion, which is probably a bit easier if you deal with a large number of files.

[http://kb.iu.edu/data/acux.html](http://kb.iu.edu/data/acux.html)

---

### Post by compwiz18 on 2006-12-02
Just FYI: I had this problem with bzflag, but downloading the tar.gz zipped version instead of .zip version solved my problem - I guess the idea here is check and see if there is a different file that might work too.

yes, i know this thread has been dead for a long time

---

