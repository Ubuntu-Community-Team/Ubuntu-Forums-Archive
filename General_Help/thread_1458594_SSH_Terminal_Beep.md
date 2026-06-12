---
title: "SSH Terminal Beep"
date: 2010-04-20
forum: General Help
---

### Post by jeffrey296 on 2010-04-20
Hey all, this should be a quick fix, I just don't know where to look.

I've got a computer running Ubuntu 9.10 set up as an SSH server. Whenever I ssh into it from another computer, I get a terminal beep upon every press of the return key. I'm pretty sure this is a server-side setting, but if it's client-side that'd be helpful to know. If anyone knows how to get rid of this beep, I'd appreciate it.

NOTE: I looked in the sshd_config file and didn't find anything, but that DOESN'T mean it's not there ;)

Thanks all.

---

### Post by _0R10N on 2010-04-20
The beeps come from the server or the clients???. The clients run windows or Linux?? If the sound comes from the server, there's a quick fix. You can go to System->Preferences->Sound and uncheck an option labeled something like "system bell"...

Kind regards!

_0R10N >>

---

### Post by gmargo on 2010-04-20
This is most likely a shell prompt (PS1 or PROMPT_COMMAND) problem.

Try this on the command line:
```

PS1='$ '

```Has the beep now gone away?  If not try "unset PROMPT_COMMAND" if it's set.


If the beep went away with PS1, here's the problem.  The default .bashrc has this segement:
```

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

```If your terminal is not full xterm compatible, that "\a" can cause a beep.  Comment out that line and see if it helps.

---

