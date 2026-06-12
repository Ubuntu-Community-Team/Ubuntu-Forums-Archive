---
title: "other users cannot run scripts"
date: 2011-08-09
forum: General Help
---

### Post by blesbok on 2011-08-09
Dear Community, Gutsy (7.10) won't run python scripts for another user, apprentice. As far as I can see, this user has sufficient permissions to do so; the line in /etc/passwd is almost identical.

The path for the other user is /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/sbin:/bin:/usr/games

It was not possible to change the path by doing this (make path resemble that of other user):

```

apprentice@blesbok-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
apprentice@blesbok-desktop:~$ export PATH=""
apprentice@blesbok-desktop:~$ echo $PATH

apprentice@blesbok-desktop:~$ PATH=$PATH/usr/local/bin:/usr/bin:/bin:/usr/games
apprentice@blesbok-desktop:~$ export PATH
apprentice@blesbok-desktop:~$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/games
 
```

Although appearing to change the path, after logging out and back in, the path remains unchanged as output for the top line of code.

So the user cannot permanently change his own path! Please tell me where the path is set; it's not in .bashrc.

The script to run simply reads: print 1+1 and its name is script.py. The command python script.py produces zero output, although the script has execute permission. This does however work for the other user. The script should run as described without a shebang line #!/bin/python and adding one doesn't help.

:confused:

Thanks for the interest

---

### Post by ajgreeny on 2011-08-09
Firstly Ubuntu 7.10 is long out of support, so I suggest updating the distro version, probably to 10.04, the most recent LTS version.

Secondly, where is the script that you want to run located, and how are you trying to run it?

---

### Post by blesbok on 2011-08-09
Thanks for the reply, ajgreeny. Yes, 7.10 is dated and the partition it's on must be transformed into a new home directory. The children do like it, however...

The script is here: /home/apprentice/script.py

Logging in as apprentice and running it from the directory /home/apprentice with the line python script.py gives no output.

---

### Post by blesbok on 2011-08-09
It may be worth mentioning that the user which can run scripts is on a KDE desktop, while apprentice is on XFCE.

---

### Post by AlphaLexman on 2011-08-09
So we can see the permissions, what is the output of...
```
ls -l /home/apprentice/script.py
```

---

### Post by blesbok on 2011-08-09
> So we can see the permissions, what is the output of...
Code:

ls -l /home/apprentice/script.py


```
-rwxr-xr-x 1 apprentice apprentice 28 2011-08-09 01:13 /home/apprentice/script.py
```

---

### Post by AlphaLexman on 2011-08-09
Well, that wasn't the problem...

If the python script isn't confidential, post it and we will see if it contains any errors.

---

### Post by Synoc on 2011-08-09
perhaps I missed it, did you give us the error message you get when you try to  run it? or is there one?

---

### Post by blesbok on 2011-08-09
```
print 1+1

```

:redface:

and it actually runs!!

Okay, the addends weren't both 1 but apprentice wrote it and left out "print" which I overlooked! 

```
1+1
```

Needless to say, "print" was included on the other username.

Thanks and apologies, posters.  Thanks for helping me see what I should have seen all on my own and apologies for a non-question, non-thread.  

All that remains is to mark this solved.

---

