---
title: "Bash no longer supports the character 'i' for me"
date: 2011-03-25
forum: General Help
---

### Post by Dr_Rent on 2011-03-25
A very strange problem started for me today. I SSHed into a server and could not type the letter 'i'. It would work fine if I was not in an SSH session, but consistently and repeatedly broke when I started SSH. I rebooted my machine, and the problem now occurs any time I'm using Bash, whether SSHing or not. For the record, I'm doing all this in the standard gnome-terminal.

First: it is not a problem with my keyboard. As you can see, I am perfectly capable of typing the letter 'i' in a browser window. In fact, capital 'I' works fine in bash as well. If I start nano from Bash, I can type the letter 'i' all day long, but when I exit to the Bash prompt, again I am unable to. 

What's even more bizarre, I cannot even paste the letter 'i' into bash, either via Ctrl+Shift+v or by middle mouse clicking. This makes it impossible for me to type commands like 'vim' or 'exit'. Bash scripts, however, appear to have no problem with this particular character. 

Now, I've commented everything out of my .bashrc file, but that didn't help. I got rid of my custom .xmodmaprc file. Still nothing. Keyboard layout is U.S. English. I removed all Keyboard Shortcuts that involve the letter 'i'. Rebooted half a dozen times, still no luck. 

My workaround at present is to use zsh instead of bash. Everything works fine with it, but I'd really like to get this thing fixed. Anyone have any ideas?

---

### Post by PCNetSpec on 2011-03-25
Do you have a **~/.inputrc** file, if so rename it.

or see if it contains the letter i on its own line... and remove that line.

---

### Post by gmargo on 2011-03-25
Very strange.  Sounds like a **readline(3)** problem.  bash(1) uses readline but zsh(1) does not.

Is there a $HOME/.inputrc file?  Or anything strange in /etc/inputrc or /usr/share/readline/inputrc?

Can you show the output of "bind -p"?  (You'll have to create an alias for bind in your .bashrc)

---

### Post by KeyserSoze93 on 2011-03-25
> **Dr_Rent said:**
> A very strange problem started for me today. I SSHed into a server and could not type the letter 'i'. It would work fine if I was not in an SSH session, but consistently and repeatedly broke when I started SSH. I rebooted my machine, and the problem now occurs any time I'm using Bash, whether SSHing or not. For the record, I'm doing all this in the standard gnome-terminal.

First: it is not a problem with my keyboard. As you can see, I am perfectly capable of typing the letter 'i' in a browser window. In fact, capital 'I' works fine in bash as well. If I start nano from Bash, I can type the letter 'i' all day long, but when I exit to the Bash prompt, again I am unable to. 

What's even more bizarre, I cannot even paste the letter 'i' into bash, either via Ctrl+Shift+v or by middle mouse clicking. This makes it impossible for me to type commands like 'vim' or 'exit'. Bash scripts, however, appear to have no problem with this particular character. 

Now, I've commented everything out of my .bashrc file, but that didn't help. I got rid of my custom .xmodmaprc file. Still nothing. Keyboard layout is U.S. English. I removed all Keyboard Shortcuts that involve the letter 'i'. Rebooted half a dozen times, still no luck. 

My workaround at present is to use zsh instead of bash. Everything works fine with it, but I'd really like to get this thing fixed. Anyone have any ideas?

Interesting... What is $LANG set to - this could be causing the shell to misread the key sequences.

You could also try running the dash shell (just run "dash" from your bash shell), and see if this still misinterprets the "i".

---

### Post by Dr_Rent on 2011-03-25
Thank you. It looks like it was related to ~/.inputrc. All it contained was a line sourcing /etc/inputrc, but removing that line cleared up my problem.

There doesn't appear to be anything strange in /etc/inputc, but what follows is its contents:
```
set meta-flag on
set input-meta on
set convert-meta off
set output-meta on

# Completed names which are symbolic links to
# directories have a slash appended.
set mark-symlinked-directories on

$if mode=emacs

# for linux console and RH/Debian xterm
"\e[1~": beginning-of-line
"\e[4~": end-of-line
"\e[5~": beginning-of-history
"\e[6~": end-of-history
"\e[3~": delete-char
"\e[2~": quoted-insert
"\e[5C": forward-word
"\e[5D": backward-word
"\e[1;5C": forward-word
"\e[1;5D": backward-word

# for rxvt
"\e[8~": end-of-line

# for non RH/Debian xterm, can't hurt for RH/DEbian xterm
"\eOH": beginning-of-line
"\eOF": end-of-line

# for freebsd console
"\e[H": beginning-of-line
"\e[F": end-of-line
$endif

```

I didn't check "bind -p" until I solved the problem, but grepping for the character "i" now gives me the perfectly innocuous: '"i": self-insert'

I'm still confused as to why this happened, but thank you all for pointing me in the right direction.

---

