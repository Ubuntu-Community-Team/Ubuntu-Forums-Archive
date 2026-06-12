---
title: "*What thing* is messing (adding things) to my prompt?"
date: 2012-08-31
forum: General Help
---

### Post by zazuzimbo on 2012-08-31
Hello,

I was trying to set window or tab titles on my gnome-terminal.

But there is [[COLOR="Blue"]lots of confusion[/COLOR]]("http://ubuntuforums.org/showthread.php?t=448614") and a [[COLOR="blue"]few things[/COLOR]]("http://www.mrj0.com/2011/02/09/setting-gnome-terminal-title-bash/") might not work as expected (apparently, but I know now that they do...).

Eventually I got to the point where I find that $PS1 is the culprit. I use a fancy and colorfull prompt, set on my own .bashrc. The line that sets it on my .bashrc is something like (keeping it simple):

PS1='\t bla bla bla \$'

But when I open a new terminal and **echo $PS1** I see that a few things are being added to my prompt. And these are what prevents me from changing the tab or window titles as I pleased:

[COLOR="Red"]\[\e]0;\u@\h: \w\a\][/COLOR]\t bla bla bla \$

**The questions is:** what thing is adding the above to PS1, and how do I stop it?

My gnome-terminal is configured to replace its title when a command sets it. And my shell is bash. The above string is not found on /etc/profile, /etc/bash.bashrc or my own .bashrc.

---

### Post by dodo3773 on 2012-08-31
Look at $PROMPT_COMMAND in /etc/bash.bashrc

---

### Post by zazuzimbo on 2012-08-31
> **dodo3773 said:**
> Look at $PROMPT_COMMAND in /etc/bash.bashrc

I already have done it. The lines are (and were) commented on /etc/bash.bashrc:

```

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

```

Further, this won't "fix" $PS1 to stopping from changing title again... :( And I'm not using xterm.

---

### Post by dodo3773 on 2012-08-31
Did you comment out all the lines in that file? Try temporarily renaming that file and see if that works maybe.

---

