---
title: "shortcut or alias"
date: 2012-06-13
forum: General Help
---

### Post by p3aul on 2012-06-13
I have a command that I use a lot in the terminal called ebook-convert I would like to be able to use ebk as an alias for it. Can someone tell me how to do this?
Thanks,
Paul

---

### Post by d2btoo on 2012-06-13
Add
```

alias ebk=command-goes-here

```

in your **~/.bashrc** file, perhaps....

for example I've one alias "ll" as :
```
alias ll='ls -lah'
```

---

### Post by Vaphell on 2012-06-13
open .bashrc located in your home (ctrl+h to unhide hidden files) and look how it's done. You can put your alias there or do as its suggested - create .bash_aliases file and put your alias there, it should be picked up next time you run terminal.

alias aliasname='some-command some parameters'

---

### Post by ajgreeny on 2012-06-13
Aliases are incredibly useful and I use many, which you may like to view and use, if they are useful to you.

```
alias addppa='sudo add-apt-repository'
alias am='alsamixer'
alias db='sudo updatedb'
alias df='df -h'
alias dl='vnstat -d'
alias dldays='vnstat -d > /tmp/$(date +%F-%T)-DLs && gedit /tmp/*DLs & exit'
alias dll='vnstat -l'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias free='free -m'
alias fsck='sudo touch /forcefsck'
alias gip='get_iplayer'
alias gipg='get_iplayer -g'
alias gipi='get_iplayer --info'
alias gipr='get_iplayer --type radio'
alias grep='grep --color=auto'
alias hw='sudo lshw -html > hw.html'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -l'
alias ls='ls --color=auto'
alias menu='grep menuentry /boot/grub/grub.cfg'
alias mv='mv -i'
alias q='exit'
alias rm='rm -i'
alias scan='sudo tune2fs /dev/sda1 -l'
alias scanhome='sudo tune2fs /dev/sda2 -l'
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias stk='cd /home/$USER/Downloads/supertuxkart-0.7.3 && ./run_game.sh'
alias temp='sudo mbmon'
alias temp5='sudo mbmon -c 5'
alias up='uptime'
alias version='uname -a && lsb_release -a'
alias xorg='cat /etc/X11/xorg.conf'
```

---

### Post by p3aul on 2012-06-13
hmmm. I don't seem to have .bashrc folder :( In fact I don't seem to have any "." folders beginning with b at all. I assume there is supposed to be aa text file in the folder were you put all your alias commands? could I create a folder and a file? what would be it's name? but you seem to be referring to a hidden file not a folder. What folder is it in? 
paul

---

### Post by d2btoo on 2012-06-13
.bashrc is a file not a folder :)

Alright do this...
press ctrl+Alt+t
After terminal opens, type
```

cat ~/.bashrc

```

now can you see your .bashrc file...
if yes then you can use gedit to edit it. (do make a backup first, in-case something goes wrong.)

---

### Post by p3aul on 2012-06-13
Hey thanks d3btoo! that worked pefectly. I just clicked under another entry and using that one for an example, added my on.
Thanks, everyone!):P

---

