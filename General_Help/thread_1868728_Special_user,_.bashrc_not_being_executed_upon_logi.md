---
title: "Special user, .bashrc not being executed upon login"
date: 2011-10-24
forum: General Help
---

### Post by ratcheer on 2011-10-24
I have started using the PostgreSQL database server. It created a special user, postgres, when I installed the package. Except for one little thing, it is working great.

When I "su - postgres" or "su -l postgres" (which should be equivalent), the .bashrc I created in user postgres's home directory is not being executed. If, after login, I run ". ./.bashrc", the profile is executed and does exactly what I want, which is just setting a couple of environment variables. I have verified that the user's shell is bash and that the .bashrc profile is in its home directory, owned by user postgres.

I even tried making the file executable, but that did not help.

I have read the man pages for both su and bash, and both seem to indicate that the profile should be being executed. What am I missing?

Thanks,
Tim

---

### Post by Paddy Landau on 2011-10-24
~/.bashrc is run on opening a new terminal, not when logging in.

Place your code at the end of ~/.profile instead and let me know if that works.

---

### Post by ratcheer on 2011-10-25
That did work, thank you. I guess I misunderstood the su manpage.

I always used .profile when I worked on Solaris systems, professionally, but for some reason I switched to using .bashrc when I moved to Linux. I think I was hitting some situations when .profile was not working the way I wanted it to on Linux. In Solaris, it had always worked whether I was opening a new terminal or running su from an existing terminal.

Thanks,
Tim

---

### Post by Paddy Landau on 2011-10-25
> **ratcheer said:**
> ... I misunderstood the su manpage.
It's not there; it's in the bash manual.

To summarise:

Bash runs the following scripts on login:

[LIST]
[*][FONT=Fixedsys]/etc/profile[/FONT]
[*]The first found of [FONT=Fixedsys]~/.bash_profile[/FONT], [FONT=Fixedsys]~/.bash_login[/FONT], [FONT=Fixedsys]~/.profile[/FONT] (Ubuntu by default uses the latter)
[/LIST]
On entering an interactive terminal, Bash also executes:

[LIST]
[*][FONT=Fixedsys]/etc/bash.bashrc[/FONT]
[*][FONT=Fixedsys]~/.bashrc[/FONT]
[/LIST]
On logout, Bash runs:

[LIST]
[*][FONT=Fixedsys]~/.bash_logout[/FONT]
[*][FONT=Fixedsys]/etc/bash.bash.logout[/FONT]
[/LIST]

---

### Post by ratcheer on 2011-10-25
Ok, thanks again. Here is the part that confused me:

```
The optional argument - may be used to provide an environment similar to what the user would expect had the user logged in directly.
```

Also, there are similar details in the explanation of the -l option.

Tim

---

### Post by felipe1982 on 2012-12-13
> **Paddy Landau said:**
> 
On entering an interactive terminal, Bash **also** executes:

[LIST]
[*][FONT=Fixedsys]/etc/bash.bashrc[/FONT]
[*][FONT=Fixedsys]~/.bashrc[/FONT]
[/LIST]

I don't think is ***also*** executes those. I think it only executes ~/.bashrc.
_[http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html](http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)_

---

### Post by Paddy Landau on 2012-12-14
> **felipe1982 said:**
> I don't think is ***also*** executes those. I think it only executes ~/.bashrc.
_[http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html](http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)_
You may not think so, but it does.

 I tested this today on Ubuntu, both 12.04 and 12.10.

When you enter an interactive terminal, Bash does indeed execute both [FONT=Lucida Console]/etc/bash.bashrc[/FONT] and [FONT=Lucida Console]~/.bashrc[/FONT].

---

### Post by felipe1982 on 2012-12-16
> **Paddy Landau said:**
> When you enter an interactive terminal, Bash does indeed execute both [FONT=Lucida Console]/etc/bash.bashrc[/FONT] and [FONT=Lucida Console]~/.bashrc[/FONT].
That's because a non-login shell calls .bashrc, which then sources /etc/bashrc. But an non-login shell does not call .bash_profile or /etc/profile.

**Interacitve Login**: The shell calls /etc/profile, then the first of .bash_profile, .bash_login, .profile.

**Interactive non-login**: The shell only calls .bashrc

If defined to do so, the files bash calls by default may subsequently call other files in the system.

---

### Post by Paddy Landau on 2012-12-17
> **felipe1982 said:**
> That's because a non-login shell calls .bashrc, which then sources /etc/bashrc. But an non-login shell does not call .bash_profile or /etc/profile.

**Interacitve Login**: The shell calls /etc/profile, then the first of .bash_profile, .bash_login, .profile.

**Interactive non-login**: The shell only calls .bashrc

If defined to do so, the files bash calls by default may subsequently call other files in the system.
Thanks for the clarification.

My .bashrc does not source [FONT=Lucida Console]/etc/bashrc[/FONT], so I don't know how it gets executed. I wonder if your system and my system are different? I am using Ubuntu 12.04.

---

### Post by felipe1982 on 2012-12-17
I use opensuse, centos, and rhel. I'm not a Debian-based-distro fan ;-), although  i have used them in the past...

You can try a few things to discover how your /etc/bashrc is being sourced by your shell, if your .bashrc isn't sourcing it.

[LIST=1]
[*]You can
```
egrep -rl '/etc/bashrc' $DIRECTORY
```Where $DIRECTORY can be `/' or `/etc' or $HOME
[*]You can remove, or rename, your startup files (.bash*) and try again.
[*]a non-login shell is (normally) one where you don't enter your password. So, after logging into your system, open a terminal, and just type "bash". That will launch a NEW interactive non-login shell.
[*]Lastly, maybe Ubuntu has a different way of doing things ???
[/LIST]
Cheers,
Felipe

---

