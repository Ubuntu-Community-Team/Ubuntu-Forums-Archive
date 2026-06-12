---
title: "How to show time of executed command"
date: 2009-12-27
forum: General Help
---

### Post by squinter on 2009-12-27
Hi,

I'm not sure how to ask this. It's better with example.

At the moment, when I start a command line window, it would look like:

sid@aeon:~$

Is it possible to put more info like time on that? For example to look like:

sid@aeon 13:00:~$

It would be very useful, because sometime I run same command again and again and often I lost track of the last time I run it.

---

### Post by g00f on 2009-12-27
Have a look in the file .bashrc in your home directory, ie /home/sid/.bashrc. There are lines in there that start "PS1=". These lines define the prompt, you can edit them to show pretty much anything you want. Google 'bash command prompt' or similar to find out the format to use.

Alternatively, you could append "; date" to your command line.




.

---

### Post by Vaphell on 2009-12-27
maybe there is an elegant way but i am not knowledgeable enough.

i have a lame idea - some script that would take the command as a parameter(s) and do 1. write the time 2. execute the command

it shouldn't be pita, because repeating command can be done with arrows going throug terminal history. I am not sure if it's easy to write the script to allow for any number of parameters though

---

### Post by sisco311 on 2009-12-27
> **squinter said:**
> Hi,

I'm not sure how to ask this. It's better with example.

At the moment, when I start a command line window, it would look like:

sid@aeon:~$

Is it possible to put more info like time on that? For example to look like:

sid@aeon 13:00:~$

It would be very useful, because sometime I run same command again and again and often I lost track of the last time I run it.

edit the *PS1=* line(s) in the ~/.bashrc file to something like:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] **$(date +%H:%M)**:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h **$(date +%H:%M)**:\w\$ '
fi

```

---

### Post by Cheesemill on 2009-12-27
For more than you ever wanted to know about customizing your bash prompt see here:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

You basically need to edit the line in your ~/.bashrc file with the PS1= declaration in it.
If you look at the page on escape sequences in the above link you can see that adding a \t to that line will insert the current time in 24 hour HH:MM:SS format.

Edit - Beaten to it. Although I'd still use **\t** rather than **$(date +%H:%M)**

---

### Post by sisco311 on 2009-12-27
> **Cheesemill said:**
> 
Edit - Beaten to it. Although I'd still use **/t** rather than **$(date +%H:%M)**

I didn't know about the \t  escape sequence, thanks for the info.

EDIT:
BTW, the complete list is documented in the man page:
```
man bash | less +3/"PROMPTING"
```

---

### Post by Cheesemill on 2009-12-27
> **sisco311 said:**
> I didn't know about the \t  escape sequence, thanks for the info.

There's loads more here:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html)

---

### Post by junapp on 2009-12-28
> **sisco311 said:**
> ```
man bash | less +3/"PROMPTING"
```

hey, thanks for the +3/"search string" - actually made me go read the man page for less to see what other little gems were in there.

---

### Post by squinter on 2010-02-16
Thanks for all the help and info. I've managed to configure it the way I want from info on this thread.

---

