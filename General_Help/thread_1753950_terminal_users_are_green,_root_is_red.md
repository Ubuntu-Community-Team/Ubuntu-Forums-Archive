---
title: "terminal users are green, root is red"
date: 2011-05-09
forum: General Help
---

### Post by boblizar on 2011-05-09
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

idea (and a good majority of the code) stolen from linux from scratch


alt + f2
run
"gnome-terminal"

```
cat >> $HOME/.bashrc << "EOF"
# linux from scratch terminal colors
NORMAL="\[\e[0m\]"
RED="\[\e[1;31m\]"
GREEN="\[\e[1;32m\]"
if [[ $EUID == 0 ]] ; then
  PS1="$RED\u [ $NORMAL\w$RED ]# $NORMAL"
else
  PS1="$GREEN\u [ $NORMAL\w$GREEN ]\$ $NORMAL"
fi
#end of linux from scratch color modifications
EOF

```

your going to need to run this as your users if you have any besides the main user.

```
sudo su
```
enter password

then again drop this block of code.

```
cat >> $HOME/.bashrc << "EOF"
# linux from scratch terminal colors
NORMAL="\[\e[0m\]"
RED="\[\e[1;31m\]"
GREEN="\[\e[1;32m\]"
if [[ $EUID == 0 ]] ; then
  PS1="$RED\u [ $NORMAL\w$RED ]# $NORMAL"
else
  PS1="$GREEN\u [ $NORMAL\w$GREEN ]\$ $NORMAL"
fi
#end of linux from scratch color modifications
EOF

```

then drop this script to make all future users green / red mode to constantly remind you to log out of root

```

cat >> /etc/skel/.bashrc << "EOF"
# linux from scratch terminal colors
NORMAL="\[\e[0m\]"
RED="\[\e[1;31m\]"
GREEN="\[\e[1;32m\]"
if [[ $EUID == 0 ]] ; then
  PS1="$RED\u [ $NORMAL\w$RED ]# $NORMAL"
else
  PS1="$GREEN\u [ $NORMAL\w$GREEN ]\$ $NORMAL"
fi
#end of linux from scratch color modifications
EOF
exit

```

press enter to exit root mode and then restart your terminals or run

```

source $HOME/.bashrc

```
[http://www.linuxfromscratch.org/blfs/view/6.3/postlfs/profile.html](http://www.linuxfromscratch.org/blfs/view/6.3/postlfs/profile.html)
source the code was stolen and modified from.

[IMG]http://img828.imageshack.us/img828/9350/terminals.jpg[/IMG]

---

### Post by sanderd17 on 2011-05-09
in what format are the colors? I would like a darker green since I use a white background. But I don't see what kind of encoding is used for the colors.

btw: linux mint uses this too.

---

### Post by bodhi.zazen on 2011-05-09
*Thread moved to **General Help**.*

Not really a security question.

See also:

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)

---

### Post by boblizar on 2011-05-11
well windows 7 decided changing its partition size would be fun...  tested this script as a user = functioning...  sudo su then dropped script again, again functioning properly =)

i also updated from 10.10 to 11.04 (and had to recompile my own emerald from git to get it to work) but other than that 11.04 works....

you can drop the script, and if you dont like the colors you can remove the script....  its written to .bashrc at the end with ## comments to define the manipulated text.

---

