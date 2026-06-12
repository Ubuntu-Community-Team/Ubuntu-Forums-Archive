---
title: "No bash completion with sudo"
date: 2010-04-29
forum: General Help
---

### Post by Woody1987 on 2010-04-29
Just installed 10.04 64bit and in gnome-terminal i have no bash completion when sudo is used.

For example:
apt- gives apt-get
but 
sudo apt- does nothing, i get no suggestions from the terminal.

Help appreciated.

---

### Post by Woody1987 on 2010-04-29
After further investigation, it is not just sudo. In karmic, i could enter apt-get press tab and get a list of commands like, update, dist-upgrade etc, but this doesnt work either.

---

### Post by arrrghhh on 2010-04-29
Have you tried hitting tab 2x?  If there's more than one thing that matches, you have to hit it 2x to get available suggestions... I'm thinking you knew that tho because it was the same way in Karmic...

---

### Post by Woody1987 on 2010-04-29
> **arrrghhh said:**
> Have you tried hitting tab 2x?  If there's more than one thing that matches, you have to hit it 2x to get available suggestions... I'm thinking you knew that tho because it was the same way in Karmic...

Yes, i have hit tab many, many times.

---

### Post by arrrghhh on 2010-04-29
> **Woody1987 said:**
> Yes, i have hit tab many, many times.

LOL ok.  Let me do some digging.

Check your bash.rc per this blog post - [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

---

### Post by Woody1987 on 2010-04-29
> **arrrghhh said:**
> LOL ok.  Let me do some digging.

Check your bash.rc per this blog post - [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

Thanks, that worked, just needed to uncomment some lines in a file. Im surprised that they were commented out by default in the first place.

---

### Post by sisco311 on 2010-04-29
For bash completion you need two things:
1. the bash-completion package
2. source /etc/bash_completion

check out if /etc/bash_completion is sourced or not in ~/.bashrc or /etc/bash.bashrc

EDIT: too late :)

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

