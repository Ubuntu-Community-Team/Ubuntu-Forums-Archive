---
title: "Shell prompt coloring"
date: 2011-02-03
forum: General Help
---

### Post by l0uismustdie on 2011-02-03
Hello, I recently found a shell script to truncate my prompt  to a reasonable length.  What I am trying to do now is color code my  prompt but every time I add colors into the script the prompt will no  longer use multiple lines.

What I mean is that if I am typing a command that is too long to fit on  one line it will wrap around and continue typing on the same line.

The script I found is:
```

function truncate_pwd
{
if [ $HOME == $PWD ]
 then
   newPWD="~"
elif [ $HOME ==  ${PWD:0:${#HOME}} ]
 then
   newPWD="~${PWD:${#HOME}}"
else
   newPWD=$PWD
fi

local pwdmaxlen=15
if [ ${#newPWD} -gt $pwdmaxlen ]
 then
  local pwdoffset=$(( ${#newPWD} - $pwdmaxlen  ))
  newPWD=".+${newPWD:$pwdoffset:$pwdmaxlen}"
fi
}

PROMPT_COMMAND=truncate_pwd
PS1="${ttyname}@\[${HOST_COLOUR}\]\h\[${RESET_COLOR}\]:\${newPWD}\\$ "

```What I have done is make the following change:
```

PS1="\e[0;31m${ttyname}@\[${HOST_COLOUR}\]\h\[${RESET_COLOR}\]:\${newPWD}\\$ \e[m"

```However, adding in those color tags will cause the shell prompt to do 
whacky things, as mentioned above.  Anyone have any ideas about this?  
Or other good scripts for manipulating the shell prompt?

---

### Post by Habitual on 2011-02-03
[http://wiki.bash-hackers.org/doku.php](http://wiki.bash-hackers.org/doku.php)

---

