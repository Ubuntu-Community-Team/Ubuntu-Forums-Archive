---
title: "bash prompt colors and line wrapping"
date: 2012-06-05
forum: General Help
---

### Post by fluca1978 on 2012-06-05
Hi all,
I'm trying to customize the bash shell prompt using the following in my .profile file:

```

# Reset
Reset='\e[0m'       # Text Reset

# Regular Colors
Black='\e[0;30m'        # Black
Red='\e[0;31m'          # Red
Green='\e[0;32m'        # Green
Yellow='\e[0;33m'       # Yellow
Blue='\e[0;34m'         # Blue
Purple='\e[0;35m'       # Purple
Cyan='\e[0;36m'         # Cyan
White='\e[0;37m'        # White

# Bold
BBlack='\e[1;30m'       # Black
BRed='\e[1;31m'         # Red
BGreen='\e[1;32m'       # Green
BYellow='\e[1;33m'      # Yellow
BBlue='\e[1;34m'        # Blue
BPurple='\e[1;35m'      # Purple
BCyan='\e[1;36m'        # Cyan
BWhite='\e[1;37m'       # White

# Underline
UBlack='\e[4;30m'       # Black
URed='\e[4;31m'         # Red
UGreen='\e[4;32m'       # Green
UYellow='\e[4;33m'      # Yellow
UBlue='\e[4;34m'        # Blue
UPurple='\e[4;35m'      # Purple
UCyan='\e[4;36m'        # Cyan
UWhite='\e[4;37m'       # White

# Background
On_Black='\e[40m'       # Black
On_Red='\e[41m'         # Red
On_Green='\e[42m'       # Green
On_Yellow='\e[43m'      # Yellow
On_Blue='\e[44m'        # Blue
On_Purple='\e[45m'      # Purple
On_Cyan='\e[46m'        # Cyan
On_White='\e[47m'       # White

# High Intensty
IBlack='\e[0;90m'       # Black
IRed='\e[0;91m'         # Red
IGreen='\e[0;92m'       # Green
IYellow='\e[0;93m'      # Yellow
IBlue='\e[0;94m'        # Blue
IPurple='\e[0;95m'      # Purple
ICyan='\e[0;96m'        # Cyan
IWhite='\e[0;97m'       # White

# Bold High Intensty
BIBlack='\e[1;90m'      # Black
BIRed='\e[1;91m'        # Red
BIGreen='\e[1;92m'      # Green
BIYellow='\e[1;93m'     # Yellow
BIBlue='\e[1;94m'       # Blue
BIPurple='\e[1;95m'     # Purple
BICyan='\e[1;96m'       # Cyan
BIWhite='\e[1;97m'      # White

# High Intensty backgrounds
On_IBlack='\e[0;100m'   # Black
On_IRed='\e[0;101m'     # Red
On_IGreen='\e[0;102m'   # Green
On_IYellow='\e[0;103m'  # Yellow
On_IBlue='\e[0;104m'    # Blue
On_IPurple='\e[10;95m'  # Purple
On_ICyan='\e[0;106m'    # Cyan
On_IWhite='\e[0;107m'   # White


# System information
#PS1="${Blue}["`uname -n -r` 
#PS1="$PS1]"


PS1="${Yellow}\u${Reset}"
PS1="${PS1}${Reset} @ "
PS1="${PS1}${BPurple}\h "
PS1="${PS1}${White}\w${Reset} "
PS1="${PS1}${Yellow}(\!)${Reset} "
PS1="${PS1}${Red} $ "
PS1="${PS1}${Reset}"


```

and this gives me the colorful aspect I want, but causes a problem with line wrapping: the prompt will accept no more than 4 digits and then will start overlapping with the prompt itself! I've checked the COLUMNS variable, and it is set to 116, so it should not be the problem.
What am I missing?

---

### Post by fluca1978 on 2012-06-14
Has anybody got a "colorful" version of Bash prompt working?

---

### Post by drmrgd on 2012-06-14
Have a look at this thread for a really nice one that I use:

[http://ubuntuforums.org/showthread.php?t=1932555](http://ubuntuforums.org/showthread.php?t=1932555)

There's also a larger How To thread here with a few ideas and suggestions on how to set this up:

[http://ubuntuforums.org/showthread.php?t=614743](http://ubuntuforums.org/showthread.php?t=614743)

---

### Post by Cheesemill on 2012-06-14
Try escaping your colour definitions:

```
PS1="\[$Yellow\]\u\[$Reset\]"
PS1="${PS1}\[$Reset\] @ "
PS1="${PS1}\[$BPurple\]\h "
PS1="${PS1}\[$White\]\w\[$Reset\] "
PS1="${PS1}\[$Yellow\](\!)\[$Reset\] "
PS1="${PS1}\[$Red\] $ "
PS1="${PS1}\[$Reset\]"
```

There's a good description of what you can do with your PS1 here:
[https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)

---

