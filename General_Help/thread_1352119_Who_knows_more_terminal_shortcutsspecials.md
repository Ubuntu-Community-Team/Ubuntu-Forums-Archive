---
title: "Who knows more terminal shortcuts/specials"
date: 2009-12-11
forum: General Help
---

### Post by Charlietje on 2009-12-11
Hi,


Does someone know shortcuts like this:

sudo !!

to execute the last command as sudo.

---

### Post by blackened on 2009-12-11
> **Charlietje said:**
> Hi,


Does someone know shortcuts like this:

sudo !!

to execute the last command as sudo.

Yep, though mine takes more keystrokes:

Up-arrow, Home Key, sudo<space>, and enter.

There may be better ways.

---

### Post by ManDay on 2009-12-11
> **blackened said:**
> Yep, though mine takes more keystrokes:

Up-arrow, Home Key, sudo<space>, and enter.

There may be better ways.

Wow, that's some complicated shortcut - do you have a mnemonic for it?

---

### Post by SuperSonic4 on 2009-12-11
To go back to the last folder used:```
cd -
```

To create a directory and it's parents ```
mkdir -p
```

To only copy new files ```
cp -u
```

Check the size of a directory ```
ls -Ash | head -n1
```

To grab a list of files in a directory (eg mp3) and pipe them to a file: ```
find /media/Music -name *.mp3 > ~/mp3
```

To list (or copy, delete, move etc) ```
ls $(cat ~/mp3)
```

---

### Post by MelDJ on 2009-12-11
a special 
apt-get moo

---

### Post by Charlietje on 2009-12-11
thanks,
this is getting very interesting!

---

### Post by blackened on 2009-12-12
> **ManDay said:**
> Wow, that's some complicated shortcut - do you have a mnemonic for it?

Not complicated at all: Up-Arrow to recall the last terminal command entered, Home-Key to go to the beginning of the line, sudo<space> and enter. Fairly universal text manipulation tactics.

---

### Post by fancypiper on 2009-12-12
You can actually make your own commands with aliases.

Create a file named .bash_aliases in your /home/<user> directory, then command:

source .bash_aliases

Now, when you log in or open a new terminal, you have your home made commands.
See:
man aliases
info aliases

```
## tinwhistle box ~/.bash_aliases file for user
# User specific aliases and functions

# Clear the terminal
alias cls='clear'

# Start X server
alias x='startx'

# Change bash prompt. See the article
# http://www-106.ibm.com/developerworks/linux/library/l-tip-prompt/
export PS1='\d \@ \[\e[32;1m\]\u\[\e[34;1m\]@\[\e[36;1m\]\H \[\e[34;1m\]\w\[\e[32;1m\] $ \[\e[0m\]'

# Monitor logs
# alias syslog='sudo tail -100f /var/log/syslog'
# alias messages='sudo tail -100f /var/log/messages'

# Keep 1000 lines in .bash_history (default is 500)
export HISTSIZE=1000
export HISTFILESIZE=1000

#Stop bash from caching duplicate lines.
HISTCONTROL=ignoredups

# Disk free in human terms
alias df='df -h'

# List paths
alias path='echo -e ${PATH//:/\\n}'

# Upgrade/update system
# alias upgrade='sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove'

# Encode wav files to flac and delete the wav file
alias zipwavd='flac -V --best --delete-input-file *.wav'

# Encode wav files to flac and keep the wav file
alias zipwav='flac -V --best *.wav'

# Decode flac files to wav format
alias uzipwav='flac -d -V *.flac'

# Encode wav to ogg
# alias oggem=oggenc -n *.wav -o *.ogg

# Allow local users to use my X session
# xhost +local:

# I can't remember the new gnome command!
alias gtop='/usr/bin/gnome-system-monitor'

# Alter the ls command
alias ll='ls --color --time-style="+%b %d %Y %H:%M"'
alias ls='ls -ac'
alias lls='ls -lac'
alias la="ls --color -lAGbh --time-style='+%b %d %Y %H:%M'"

# Set background in Fluxbox
# alias bg='fbsetbg -a /home/phil/Pictures/kells/kelljesusarrest.gif'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/KellsFol114rArrestOfChrist.jpg'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/KellsFol007vMadonnaChild.jpg'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/4evangelists.jpg'

# Become system administrator
alias god='sudo -i'
alias root='sudo -i'

# Because less is more and more is less
alias more='less'

# xterm
# alias xterm='xterm -bg black -fg green'

# Launch links or w3m with my linux links page
alias web='links2 /home/phil/bookmarks.html'
alias wweb='w3mmee /home/phil/bookmarks.html'

# For nano editor
alias nano='nano -w'

# Start gkrellm after stopping it in x
alias gkrellm='gkrellm -w &'

# Kill mplayer
alias kmp='killall -9 mplayer & killall -9 gnome-mplayer'
```

---

