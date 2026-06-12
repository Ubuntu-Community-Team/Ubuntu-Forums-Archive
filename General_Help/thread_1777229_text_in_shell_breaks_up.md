---
title: "text in shell breaks up"
date: 2011-06-07
forum: General Help
---

### Post by victor_sk on 2011-06-07
Hi all,

I work a lot with Unix bash shell environment.  Whenever I go down the directory tree to several subdirectories, i.e., /home/a/b/c/d/ and so on and type in a long command, what happens is that command text wraps around onto the new line but when trying to edit command I can only go back to the beginning of the new line.  So, for, instance, say I go to directory and type something like:

/home/a/b/c/d/find . -type f -exec sed -i  <- end of line
's/blah/blah/g' {} \;   <- new line 

Here, the problem is I can't go back to the real beginning of my command that starts with "find", I can only scroll to the beginning of the new line with the part "'s/blah/blah/g' {} \;" 

So I effectively loose control over what I typed and can't edit it when the command wraps to a new line.  Does anyone else experience this problem?

I also have this problem on our Debian servers so I always have to make sure I type the right command the first time because I can't move back and forth to edit it when it wraps to a new line.

Does anybody know a fix to this?

Thanks,
Victor.

---

### Post by TeoBigusGeekus on 2011-06-07
No problem here with xterm on arch.
Have you tried pressing the home button?

---

### Post by nothingspecial on 2011-06-07
I don't know what's wrong or how to fix it because I'm not seeing that here.

However, 2 suggestions until you do fix it.

If you need to type a really long command and make sure it's right before you execute it then hold down the Ctrl key and press X then E (one after another, not at the same time) that will bring up your default editor (nano in my case). When you save the file (which bash will do to a temp file) and exit the editor the command (or even script) will be executed.

So you should be able to edit your command with this method.

The other thing you can do is make an alias like this

```
alias wd='PS1="${debian_chroot:+($debian_chroot)}\u@\h:\W\$ "'
```

Next time you have a huge path to your working directory type wd and it will only display the name of the current directory not the full path. To change it back just type```
 . ~/.bashrc
```


```
ns@ns-pc:~/Ubuntu One/Journeys_Through_A_Changing_World/Block 3 Nile limits/Docs$ wd
ns@ns-pc:Docs$ . ~/.bashrc
ns@ns-pc:~/Ubuntu One/Journeys_Through_A_Changing_World/Block 3 Nile limits/Docs$ 
```

Maybe that will help a little till you get this fixed.

---

### Post by FormatSeize on 2011-06-07
> **victor_sk said:**
> 
 
So I effectively loose control over what I typed and can't edit it when the command wraps to a new line. Does anyone else experience this problem?
 
I also have this problem on our Debian servers so I always have to make sure I type the right command the first time because I can't move back and forth to edit it when it wraps to a new line.
 
I, too, have experienced this problem. At first I didn't realize that it was a problem until I typed up a really long command (about 8 lines), and realized that I had forgotten an "=" sign. I tried to go back and correct it, but I couldn't. 
 
I don't think that it's a problem with any distribution in particular, but rather just something that is inherent in the way the system works, much like all the hoops you have to jump through to get a DOS command line window to resize like you want it to. 
 
Once I ran into this problem (it was just last night), I had no choice but to input the faulty command (as root), and hope that nothing caught on fire. Luckily, though, the script exited with an error and didn't carry out any other parts of the command giving me a chance to go back and type it correctly. 
 
But, the second time, I didn't type it directly into the terminal. I used Kate, which is a combination of a text editor and a terminal (a super text editor, if you will), and I typed the command into the text editor so that I could give it the once over and make sure there are no mistakes, and then copy/pasted the command into the terminal to let it run.
 
I don't know how much of a real workaround that is, though. It does severely cripple productivity, but I do Linux as a hobby, personally. And I only do this if the command is several lines long.

---

### Post by Slim Odds on 2011-06-07
> **FormatSeize said:**
> ...
 
Once I ran into this problem (it was just last night), I had no choice but to input the faulty command (as root), and hope that nothing caught on fire. Luckily, though, the script exited with an error and didn't carry out any other parts of the command giving me a chance to go back and type it correctly.
...


You could have just pressed Ctrl-C. You didn't need to execute the "faulty" command.

I'm still not sure that I understand the original problem. I've used Linux for a long time with bash and I can edit long multi-line input without issue. All of the "standard" editing keys and features work just fine with multiple lines.

---

### Post by AlphaLexman on 2011-06-07
@ OP: Post your **/etc/inputrc** and **~/.inputrc** files. You may not have the second file, that's ok.

---

### Post by victor_sk on 2011-06-07
> **nothingspecial said:**
> 
```
alias wd='PS1="${debian_chroot:+($debian_chroot)}\u@\h:\W\$ "'
```


Hi,

Thank you very much for this suggestion and use of Ctrl.  These are neat tricks which I wasn't aware of.

---

### Post by victor_sk on 2011-06-07
> **AlphaLexman said:**
> @ OP: Post your **/etc/inputrc** 

Hi, this is my /etc/inputrc file as you requested:

```

# /etc/inputrc - global inputrc for libreadline
# See readline(3readline) and `info rluserman' for more information.

# Be 8 bit clean.
set input-meta on
set output-meta on

# To allow the use of 8bit-characters like the german umlauts, uncomment
# the line below. However this makes the meta key not work as a meta key,
# which is annoying to those which don't need to type in 8-bit characters.

# set convert-meta off

# try to enable the application keypad when it is called.  Some systems
# need this to enable the arrow keys.
# set enable-keypad on

# see /usr/share/doc/bash/inputrc.arrows for other codes of arrow keys

# do not bell on tab-completion
# set bell-style none
# set bell-style visible

# some defaults / modifications for the emacs mode
$if mode=emacs

# allow the use of the Home/End keys
"\e[1~": beginning-of-line
"\e[4~": end-of-line

# allow the use of the Delete/Insert keys
"\e[3~": delete-char
"\e[2~": quoted-insert

# mappings for "page up" and "page down" to step to the beginning/end
# of the history
# "\e[5~": beginning-of-history
# "\e[6~": end-of-history

# alternate mappings for "page up" and "page down" to search the history
# "\e[5~": history-search-backward
# "\e[6~": history-search-forward

# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

$if term=rxvt
"\e[8~": end-of-line
"\eOc": forward-word
"\eOd": backward-word
$endif

# for non RH/Debian xterm, can't hurt for RH/Debian xterm
# "\eOH": beginning-of-line
# "\eOF": end-of-line

# for freebsd console
# "\e[H": beginning-of-line
# "\e[F": end-of-line

$endif


```

---

### Post by AlphaLexman on 2011-06-07
It looks the same as mine, sorry that wasn't it.

---

### Post by victor_sk on 2011-06-07
> **AlphaLexman said:**
> It looks the same as mine, sorry that wasn't it.

Oh, ok.  Anybody else?

---

