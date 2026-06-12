---
title: "tab autocomplete stopped working"
date: 2011-05-04
forum: General Help
---

### Post by geoffm on 2011-05-04
I did a bunch of uninstalls and reinstalls lately, trying different distros. Now I'm back to Ubuntu but tab autocomplete in terminals doesn't work anymore. It is quite less convenient now to use the terminal. I tried changing interpreter to /bin/bash and it doesn't work. I use guake.

---

### Post by compmodder26 on 2011-05-04
See if this fixes you up:

[http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

Note: The steps in the page change that for all users.  If you want it to just apply to your specific user, change it in ~/.bashrc

---

### Post by geoffm on 2011-05-04
> **compmodder26 said:**
> See if this fixes you up:

[http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

Note: The steps in the page change that for all users.  If you want it to just apply to your specific user, change it in ~/.bashrc

Sweeet! That did it. Thanks.

For others with the same problem:

Edit your /etc/bash.bashrc file. 
quick shortcut: (Alt + F2, "gksudo gedit /etc/bash.bashrc")

Uncomment the following lines, by removing the # in the beginning of the lines:
```
#if [ -f /etc/bash_completion ]; then
# . /etc/bash_completion
#fi
```

---

