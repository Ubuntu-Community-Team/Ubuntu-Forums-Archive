---
title: "Users can't log in and SU and SUDO are broke"
date: 2010-10-05
forum: General Help
---

### Post by rsteinmetz70112 on 2010-10-05
I have a 10.04 machine that su and sudo will not work on. I am also unable to login as a user other than root.

I am haven't been to figure out what might the problem.

Obviously there is some kind of problem validating users, but I can't find it. 

Any suggestions?

---

### Post by Sergius14 on 2010-10-05
Whats happens if you try to change some user password?

passwd user

---

### Post by jfed on 2010-10-05
I know this may be stupid and way, way off, but it's just sortive a stab in the dark.

I think I recall once being told that sudo was a program, or downloadable package of some sort...try re-downloading it? How; I don't know...

---

### Post by rsteinmetz70112 on 2010-10-05
If I try to shange a password it seems to work and the contents of /etc/shadow are changed.

sudo is a program but so is su, if one or the other didn't work then a corrupt file could be a problem but since neither work and I can't log in for the console, I think the problem is probably deeped and ultimately simpler.

---

### Post by Sergius14 on 2010-10-05
I'm not a Linux/Ubuntu expert, but I can't find the relationship between su/sudo and login.

A failure with su/sudo can see something with the apps itself as you mention, or another thing. For ex. trying to use sudo with users that aren't allowed (they are not administrators maybe?). File permitions, and that kind of stuff.

But failing to login to the OS should be another thing (and maybe related). 

Have you tried to login to the console session?

That happened to me once, not so far. I can't exactly remember what was, but I think that I uninstalled by mistake 'gnome-session'.

---

### Post by rsteinmetz70112 on 2010-10-06
root can login in from the regular graphic login.

I think it may be a file permissson thing. I though it was pam, but I can't find anything different between a machine that works and one that doesn't

---

### Post by rnerwein on 2010-10-06
> **rsteinmetz70112 said:**
> root can login in from the regular graphic login.

I think it may be a file permissson thing. I though it was pam, but I can't find anything different between a machine that works and one that doesn't
hi
you say you can login as root ( that means you manuplate the system default ).
ok.
1. login as root
2. open two terminals.
3. in one of the terminal type: echo $$ (now you got the pid of that shell ).
4. in the other terminal type: strace -f -o blablu -p PID ( pid you got from the echo before ).
5. change the terminal again and there you type: su - anybody.
    after the su command failed -> next step.
6. quit your strace command with "CTRL C"


in the output file blablu you will find the part where the system call ( open ... etc failed ).
good luck
ciao

---

### Post by rsteinmetz70112 on 2010-10-06
Thank you for the tip.

I was eventually able to solve the issue the old fashioned way, reading the logs and Goggling the errors.

It turns out there were three separate problems, all as a result of prior configuration issues.

First there is a bug in the slapd upgrade routines that cause some failures see Bug #571057. Its supposed to be fixed but I apparently caught it before that.

Second I had a problem with my home directories that prevented a login from the console for any use whose home directory was in /home.

Finally I had modified /etc/pam.d/common-auth to get winbind to work a couple of releases ago. Winbind is now supported by the standard pam configuration by my prior edits were breaking it.

In short an accumulation of operator errors.

---

