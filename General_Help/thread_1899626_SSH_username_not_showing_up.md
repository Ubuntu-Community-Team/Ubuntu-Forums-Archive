---
title: "SSH username not showing up"
date: 2011-12-24
forum: General Help
---

### Post by theone419 on 2011-12-24
ok so im using SSH to login to my account and everything works fine, then i mess around with something i shouldn't of and now i need help.

When you login to ssh your terminal shows

Username@host:~$ 

now it says

/ $ 

Im in the root and lets say i want to go to /home/username the command line will show 
/home/username $

but my username does not show up anymore. How can I fix this anyone? Thanks...

Ive tried looking at the bash and running chs -s /bin/sh but no luck.

---

### Post by Lars Noodén on 2011-12-24
What did you change?  If you messed with [font=Courier New].bashrc[/font] and [font=Courier New].profile[/font], you can restore them to their defaults by copying them from [font=Courier New]/etc/skel[/font]

---

### Post by theone419 on 2011-12-24
> **Lars Noodén said:**
> What did you change?  If you messed with [FONT=Courier New].bashrc[/FONT] and [FONT=Courier New].profile[/FONT], you can restore them to their defaults by copying them from [FONT=Courier New]/etc/skel[/FONT]

Sorry it does not exist. Just to let you know I have Jailshell so im limited to what i can do, but somehow I messed that up.

Here is the ENV output

 ```
$env
MANPATH=/usr/lib/courier-imap/man:
HOSTNAME=server.myserverhosts.com
TERM=xterm
SHELL=/usr/local/cpanel/bin/jailshell
HISTSIZE=1000
SSH_CLIENT=000.000.000.xxx 50945 8982
PERL5LIB=/home/eastcoas/perl5/lib/perl5/x86_64-linux-thread-multi:/home/eastcoas/perl5/lib/perl5
OLDPWD=/home
PERL_MB_OPT=--install_base /home/eastcoas/perl5
SSH_TTY=/dev/pts/0
USER=eastcoas
LS_COLORS=no=00:fi=00:di=01
MAIL=/var/spool/mail/eastcoas
PATH=/usr/local/jdk/bin:/home/eastcoas/perl5/bin:/usr/kerberos/bin:/usr/lib/courier-imap/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin:/home/eastcoas/bin
INPUTRC=/etc/inputrc
PWD=/
JAVA_HOME=/usr/local/jdk
EDITOR=pico
SHLVL=1
HOME=/home/eastcoas
LS_OPTIONS=--color=tty -F -a -b -T 0
PERL_LOCAL_LIB_ROOT=/home/eastcoas/perl5
LOGNAME=eastcoas
VISUAL=pico
CVS_RSH=ssh
CLASSPATH=.:/usr/local/jdk/lib/classes.zip
SSH_CONNECTION=000.000.xxx.00 50945 XXX.192.220.100 8982
LESSOPEN=|/usr/bin/lesspipe.sh %s
HISTTIMEFORMAT=%m-%d-%Y %H:%M:%S
PERL_MM_OPT=INSTALL_BASE=/home/eastcoas/perl5
G_BROKEN_FILENAMES=1
_=/bin/env
```

---

### Post by btindie on 2011-12-24
It's the PS1 variable that controls what is displayed at the prompt, you just need to set it back to what it was originally. On Ubuntu, PS1 usually gets set in ~/.bashrc

---

### Post by theone419 on 2011-12-24
> **btindie said:**
> It's the PS1 variable that controls what is displayed at the prompt, you just need to set it back to what it was originally. On Ubuntu, PS1 usually gets set in ~/.bashrc

So simple, thanks that fixed it.

---

