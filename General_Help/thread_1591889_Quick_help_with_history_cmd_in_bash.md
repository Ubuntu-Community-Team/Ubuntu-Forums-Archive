---
title: "Quick help with history cmd in bash"
date: 2010-10-10
forum: General Help
---

### Post by juil on 2010-10-10
When I type history at the prompt I should be getting a list of all the commands that i used but instead i'm getting this message:

```
skynet@skynet-desktop~ $ history
bash: $1: unbound variable

```

Can anyone tell me why and how i can fix this?

---

### Post by juil on 2010-10-10
bump

---

### Post by luvshines on 2010-10-10
Though I am not sure, but can you try this:
```
echo $anything
```

---

### Post by juil on 2010-10-11
Thanks for your reply but that didn't solve the problem for me.

```
skynet@skynet-desktop~/Documents $ echo $anything
bash: anything: unbound variable

```

---

### Post by papibe on 2010-10-11
The command:
```
$ set -u
```
produces a similar behavior. You can reset it like this:
```
$ set +u
```
However, if it happens always you open a terminal, it means it is set in some of the bash files. Have you mod any of these files?
[INDENT]/etc/profile
/etc/bash.bashrc
/etc/bash.bash.logout
~/.bash_profile
~/.bashrc
~/.bash_logout
~/.inputrc[/INDENT]

---

### Post by luvshines on 2010-10-11
> **juil said:**
> Thanks for your reply but that didn't solve the problem for me.

```
skynet@skynet-desktop~/Documents $ echo $anything
bash: anything: unbound variable

```

That won't change anything. Actually I was just checking whether your shell is behaving like "set -u" or not. Looks like it is

Did you try what papibe said ? I am not able to reproduce your error if I set 'set -u' in my active shell so can't say if papibe's solution will help or not

---

### Post by juil on 2010-10-11
Thanks for your reply!
I executed the set +u command but it's not behaving like it should.
Instead it's giving me a list of what the most recent activities are.
And YES, maybe a month ago I downloaded a Terminal theme, copied and pasted over the existing .bashrc texts. I have it saved somewhere else. Should I have copied it below the exisitng .bashrc text?

So here is what I get when i type history:


```
2010-10-11 03:12:00 status half-configured avant-window-navigator-data-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:00 status installed avant-window-navigator-data-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:00 configure avant-window-navigator-trunk 0.4.1~bzr743+201009122042~lucid1 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:00 status unpacked avant-window-navigator-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:00 status half-configured avant-window-navigator-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:00 status installed avant-window-navigator-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:00 status triggers-pending libc-bin 2.11.1-0ubuntu7.2
2010-10-11 03:12:01 configure awn-applets-c-core-trunk 0.4.1~bzr1435-1.10.04 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status unpacked awn-applets-c-core-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status half-configured awn-applets-c-core-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status installed awn-applets-c-core-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 configure awn-applets-c-extras-trunk 0.4.1~bzr1435-1.10.04 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status unpacked awn-applets-c-extras-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status half-configured awn-applets-c-extras-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status installed awn-applets-c-extras-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 configure awn-applets-python-core-trunk 0.4.1~bzr1435-1.10.04 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:01 status unpacked awn-applets-python-core-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 status half-configured awn-applets-python-core-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 status installed awn-applets-python-core-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 configure awn-applets-python-extras-trunk 0.4.1~bzr1435-1.10.04 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 status unpacked awn-applets-python-extras-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 status half-configured awn-applets-python-extras-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 status installed awn-applets-python-extras-trunk 0.4.1~bzr1435-1.10.04
2010-10-11 03:12:02 configure awn-settings-trunk 0.4.1~bzr743+201009122042~lucid1 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:02 status unpacked awn-settings-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:02 status half-configured awn-settings-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:02 status installed awn-settings-trunk 0.4.1~bzr743+201009122042~lucid1
2010-10-11 03:12:03 trigproc libc-bin 2.11.1-0ubuntu7.2 2.11.1-0ubuntu7.2
2010-10-11 03:12:03 status half-configured libc-bin 2.11.1-0ubuntu7.2
2010-10-11 03:12:03 status installed libc-bin 2.11.1-0ubuntu7.2
```

---

### Post by luvshines on 2010-10-11
Atleast it gives something now :)

**For future, first backup the working files and then try nething new**

For now, just check if history command has not be aliased:
```
alias | grep -i history
```

Also, check the following:
```
set | grep "^HIST"
```

If you find something like HISTFILE, open the specified file and see if history is actually there or not(No need to paste it here)

---

### Post by juil on 2010-10-11
Much appreciated!
The HISTFILE which is [COLOR="Blue"].bash_history[/COLOR] DOES show all the list of commands I executed so it's saving it, and that's good.

As for the aliasing when i typed '[COLOR="Red"]alias | grep -i history[/COLOR]', it shows this:

```
skynet@skynet-desktop~/Documents/Test $ [COLOR="red"]alias | grep -i history[/COLOR]
alias alert_helper='history|tail -n1|sed -e "s/^\s*[0-9]\+\s*//" -e "s/;\s*alert$//"'
alias h='history | grep $1'
alias hgrep='history | grep --color=always'
alias history='apt-history'
alias historyi='apt-history install'
alias historyre='apt-history remove'
alias historyro='apt-history rollback'
alias historyu='apt-history upgrade'
alias top-commands='history | awk "{print $2}" | awk "BEGIN {FS="|"} {print $1}" |sort|uniq -c | sort -rn | head -10'
```

So, this is from the .bashrc theme that i said i pasted about a month ago. I'm going to guess at this but should it be:

```
alias history='history'
```

I don't even know why the theme creator even aliased history...
Also I did have the default [COLOR="Blue"].bashrc[/COLOR] saved as [COLOR="blue"].bashrc-backup[/COLOR], so i can retrieve it anytime.

---

### Post by luvshines on 2010-10-11
> **juil said:**
> Much appreciated!
The HISTFILE which is [COLOR="Blue"].bash_history[/COLOR] DOES show all the list of commands I executed so it's saving it, and that's good.

So, this is from the .bashrc theme that i said i pasted about a month ago. I'm going to guess at this but should it be:

```
alias history='history'
```

I don't even know why the theme creator even aliased history...
Also I did have the default [COLOR="Blue"].bashrc[/COLOR] saved as [COLOR="blue"].bashrc-backup[/COLOR], so i can retrieve it anytime.

Actually it should not be aliased at all. **To run it unaliased temporarily, just do**:
```
unalias history; history
OR
\history
```

unalias keywork will last only for the session in which it was invoked. The '\' calling will be only for that single instance of call

**For a permanent solution**, just see where the aliases have been defined for history, comment them out, save it and exit that shell. Then open a new one to see the changes.
PS: Oh by the way, for the set +u thing, where did you make the change ??

---

### Post by juil on 2010-10-12
Much thanks for your help!
It all makes sense how we got to this point, but I think i need someone to guide me. :)

So, yes it worked. I uncommented the history alias in .bashrc.
Wanna see what it looked like when i found it?:

```
##### Apt-history Stuff
**[COLOR="Red"]alias history='apt-history'[/COLOR]**
alias historyi='apt-history install'
alias historyu='apt-history upgrade'
alias historyre='apt-history remove'
alias historyro='apt-history rollback'
```

I'm guessing the person who made the them thought the history command was not very useful. 

The set +u command?... i ran it in terminal. I'm not sure if that's the answer you were expecting.

Now, i'm learning command lines right now so, i'm concerned that it may run into a similar problem when i experiment with other commands. Should I append the terminal theme text to the original .bashrc file which i backed up?

EDIT: Dang, i think this guy broke the command lines or something. :mad: I tried apt-history on the terminal and now it's giving me the same error i got when i had the history problem.... I'm still marking it solved because you help me solve my original problem. When i checked the .bashrc file it only gave me these results for apt-history.

```
##### To show Apt Log History

function apt-history(){
      case "$1" in
        install)
              cat /var/log/dpkg.log | grep 'install '
              ;;
        upgrade|remove)
              cat /var/log/dpkg.log | grep $1
              ;;
        rollback)
              cat /var/log/dpkg.log | grep upgrade | \
                  grep "$2" -A10000000 | \
                  grep "$3" -B10000000 | \
                  awk '{print $4"="$5}'
              ;;
        *)
              cat /var/log/dpkg.log
              ;;
      esac
}
```

That's it. Nothing else on apt-history. No aliasing. Although when i checked the backup bashrc file, there is nothing on apt-history. Your thoughts?

---

