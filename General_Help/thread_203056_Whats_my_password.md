---
title: "Whats my password???"
date: 2006-06-24
forum: General Help
---

### Post by charles.g.moore on 2006-06-24
I just installed Kubuntu and did the updates.

when I pull up a terminal window and try to su it asks for a password, i try to put my login password in  and it says thats not it, is there a default unix password that i should know so that i can change it to mine???

---

### Post by Sye d'Burns on 2006-06-24
Assuming you're using the first user created (the one with admin rights) it should just be your user password.

---

### Post by olsonar on 2006-06-24
try using sudo instead of su. by default ubuntu disables su for anyone except root. if you must use a root terminal, do sudo su.

---

### Post by skymt on 2006-06-24
[QUOTE=olsonar]try using sudo instead of su. by default ubuntu disables su for anyone except root. if you must use a root terminal, do sudo su.[/QUOTE]
"sudo -s" does the same thing as "sudo su", but with more error-checking.

---

### Post by aysiu on 2006-06-24
[QUOTE=skymt]"sudo -s" does the same thing as "sudo su", but with more error-checking.[/QUOTE]
That's good to know.

I've also seen people recommend ```
sudo -i
``` What's that and how does that differ from the other two?

---

### Post by charles.g.moore on 2006-06-24
Thanks guys , I did the sudo su, it prompted for password and it was the one i made during install!!! so i guess i should always use sudo su in order to gain the root permissions right?

---

### Post by aysiu on 2006-06-24
[QUOTE=charles.g.moore]Thanks guys , I did the sudo su, it prompted for password and it was the one i made during install!!! so i guess i should always use sudo su in order to gain the root permissions right?[/QUOTE]
Actually, I think skymt's recommendation was ```
sudo -s
``` instead of ```
sudo su
```

---

### Post by Ramses de Norre on 2006-06-24
I only understand it half myself but this is what man sudo tells about the difference between -i and -s:> -i  The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the user that the command
           is being run as.  The command name argument given to the shell begins with a - to tell the shell to run as a login
           shell.  sudo attempts to change to that user's home directory before running the shell.  It also initializes the
           environment, leaving TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, and unsetting all other environ-
           ment variables.  Note that because the shell to use is determined before the sudoers file is parsed, a runas_default
           setting in sudoers will specify the user to run the shell as but will not affect which shell is actually run.


-s  The -s (shell) option runs the shell specified by the SHELL environment variable if it is set or the shell as speci-
           fied in passwd(5).

So it seems to have influence on the environment variables the root shell uses.

---

### Post by aysiu on 2006-06-24
Yeah, that's beyond me, too, which is why I've never understood the whole RTFM thing. Even after I RTFM, I don't UTFM at all.

---

### Post by Ramses de Norre on 2006-06-24
What are RTFM and UTFM? =) (I think the R and U are root and user, derivating from the context)

---

### Post by aysiu on 2006-06-24
[QUOTE=Ramses de Norre]What are RTFM and UTFM? =) (I think the R and U are root and user, derivating from the context)[/QUOTE]
RTFM is frowned upon in these forums (and with good reason)--it stands for "read the fuc king manual."

UTFM I just made up and it stands for "understand the fuc king manual."

---

### Post by Ramses de Norre on 2006-06-24
Oh, ok:D I read a lot of man pages and I can derivate the right commands to use out of them most of the time, but there are also a lot of things I never understand. 
And some manuals (like the one for find) are so cryptic and long I don't even start to read them =)

---

### Post by aysiu on 2006-06-24
Same here.

---

