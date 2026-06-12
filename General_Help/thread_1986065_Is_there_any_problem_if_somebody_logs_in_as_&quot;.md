---
title: "Is there any problem if somebody logs in as &quot;root&quot; by mistake?"
date: 2012-05-24
forum: General Help
---

### Post by arroy_0209 on 2012-05-24
The root password is locked in ubuntu. However while trying to use the command "sudo netstat -nPi", by mistake I used the command "sudo -nPi" and as a result, the terminal prompt changed from "arroy@arroy-deskto-:~$" to "root@arroy-deskto-:~$". I am confused if I really logged in as root or not. Can anybody please point out if there is a problem due to this and what I should do to reverse the bad effects of this if any. In particular will it cause security issues?

---

### Post by MadmanRB on 2012-05-24
No as Ubuntu doesnt use root, it uses sudo.
Just be careful with the terminal and keep your password up to date and you should do fine.

---

### Post by arroy_0209 on 2012-05-24
Thanks for the reply. 

I am worried particularly because in the ubuntu guidelines on "rootsudo" ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)), there is clear warnig aginst use of the command, "sudo -i" which is exactly what I used by mistake. Since I do not fully understand all the issues involved, I am looking for a bit explanation in this regard.

---

### Post by nothingspecial on 2012-05-24
You ran sudo with these options

```
       -n          The -n (non-interactive) option prevents sudo from
                   prompting the user for a password.  If a password is
                   required for the command to run, sudo will display an
                   error messages and exit.
```

```
       -P          The -P (preserve group vector) option causes sudo to
                   preserve the invoking user's group vector unaltered.
                   By default, the sudoers policy will initialize the
                   group vector to the list of groups the target user is
                   in.  The real and effective group IDs, however, are
                   still set to match the target user.

```

```
i [command]
                   The -i (simulate initial login) option runs the shell
                   specified by the password database entry of the target
                   user as a login shell.  This means that login-specific
                   resource files such as .profile or .login will be read
                   by the shell.  If a command is specified, it is passed
                   to the shell for execution via the shell's -c option.
                   If no command is specified, an interactive shell is
                   executed.  sudo attempts to change to that user's home
                   directory before running the shell.  The security
                   policy shall initialize the environment to a minimal
                   set of variables, similar to what is present when a
                   user logs in.  The Command Environment section in the
                   sudoers(5) manual documents how the -i option affects
                   the environment in which a command is run when the
                   sudoers policy is in use.

```

Type ```
man sudo
``` to see more.

And no, aslong as you didn't do anything there is no problem :)

---

### Post by MadmanRB on 2012-05-24
well logically if something is telling you dont do something,. then you shouldnt do it then.
Never use the command line unless it is 100% needed, as most things in ubuntu these days can be done in a GUI

---

### Post by wyliecoyoteuk on 2012-05-24
> **MadmanRB said:**
> well logically if something is telling you dont do something,. then you shouldnt do it then.
Never use the command line unless it is 100% needed, as most things in ubuntu these days can be done in a GUI

Not on my headless Ubuntu server, you can't. ;)

---

### Post by muteXe on 2012-05-24
> **MadmanRB said:**
> Never use the command line unless it is 100% needed, as most things in ubuntu these days can be done in a GUI

this is silly advice if you've installed ubuntu with the intention of learning about linux.

(Although actually, if you want learn linux i wouldnt recommend ubuntu).

---

### Post by eleftg on 2012-05-24
As long as you DID NOT type

<snip>

right after your mistake with sudo, everything still works fine :-D

---

### Post by arroy_0209 on 2012-05-24
Thanks for the assurances. I did not do anything stupid like what you mentioned (rm -rf / ). I immediately pressed ctrl+d and came out. 

Those things apart, here is a related question, when I enter the command ls -l, inside / the result for root/ is:
```
drwx------  11 root root  4096 2012-04-21 13:04 root/
``` Can anybody please tell me what the date (2012-04-21) and time imply? I guess these would have been changed if I had used any command as root today. Is that correct? But why does it not get affected since I practically everyday use "sudo <command>"?

---

