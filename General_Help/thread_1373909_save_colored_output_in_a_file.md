---
title: "save colored output in a file"
date: 2010-01-06
forum: General Help
---

### Post by michelkogan on 2010-01-06
is there any way to save a colored output, something like :
```
#!/bin/bash
#

# Program name from it's filename
prog=${0##*/}

# Text color variables
txtund=$(tput sgr 0 1)          # Underline
txtbld=$(tput bold)             # Bold
bldred=${txtbld}$(tput setaf 1) #  red
bldblu=${txtbld}$(tput setaf 4) #  blue
bldwht=${txtbld}$(tput setaf 7) #  white
txtrst=$(tput sgr0)             # Reset
info=${bldwht}*${txtrst}        # Feedback
pass=${bldblu}*${txtrst}
warn=${bldred}!${txtrst}

# Display usage if full argument isn't given
if [[ -z "$@" ]]; then
  echo " $prog <input> - description"
  exit
fi

# Successful command, Information, Alert
echo -e "${info} "
echo -e "${pass} "
echo -e "${warn} "


```
into a file ... 

this save output in a file but colors missing:

```
./coloroutput.bash > file.txt
```

---

### Post by geekshlby on 2010-01-06
```

#!/bin/bash

YELLOW="\033[38;5;226m"
BLUE="\033[38;5;21m"
RED="\033[38;5;196m"
NORMAL="\033[39m"

echo "$YELLOW Hi there, I'm yellow :) $NORMAL"
echo "$BLUE Hi there, I'm blue :) $NORMAL"
echo "$RED Hi there, I'm red :) $NORMAL"
echo "And now I am normal"

```

You can redirect the output to a file, and the color codes will be save to the file as well.  
If you cat the file you redirected the script to it will display the colors.  

An easy method to determine color codes is with colortest (a perl script).  
Colortest [http://www.vim.org/scripts/script.php?script_id=1349](http://www.vim.org/scripts/script.php?script_id=1349)

---

### Post by michelkogan on 2010-01-06
> **geekshlby said:**
> ```

#!/bin/bash

YELLOW="\033[38;5;226m"
BLUE="\033[38;5;21m"
RED="\033[38;5;196m"
NORMAL="\033[39m"

echo "$YELLOW Hi there, I'm yellow :) $NORMAL"
echo "$BLUE Hi there, I'm blue :) $NORMAL"
echo "$RED Hi there, I'm red :) $NORMAL"
echo "And now I am normal"

```

You can redirect the output to a file, and the color codes will be save to the file as well.  
If you cat the file you redirected the script to it will display the colors.  

An easy method to determine color codes is with colortest (a perl script).  
Colortest [http://www.vim.org/scripts/script.php?script_id=1349](http://www.vim.org/scripts/script.php?script_id=1349)

many tahnks ... is there any way to convert bash output to html tags?? for example if there is a red text in output, convert it to <font style="color: red;"> red txt </font>

---

