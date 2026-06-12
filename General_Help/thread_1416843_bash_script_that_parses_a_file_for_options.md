---
title: "bash script that parses a file for options"
date: 2010-02-26
forum: General Help
---

### Post by terranair on 2010-02-26
Hi!
Can anyone tell me (with some code if you can) how to make an interactive bash script that reads option from a file?

Something like this:

1 : $HOME/scripts/script1.sh
2 : $HOME/scripts/script2.sh
...

The script should look something like this:

Choose an option:
1 : $HOME/scripts/script1.sh
2 : $HOME/scripts/script2.sh
...

And the more options I add to the file the script should be able to detect them and when I choose 1 for example the first script should be executed and so on for the rest.

Please help!
TY!

---

### Post by richardjh on 2010-02-26
HI

The simpliest code would be something like this where the menu options are in a file called $HOME/scripts/options.txt:

```

#!/bin/bash

# Draw the menu as specified, the file $HOME/scripts/options.txt contains the 
# options
echo "Choose an option"
cat $HOME/scripts/options.txt

# show a prompt and read the answer and save as variable option
read -p ">" option
echo

# Using the format of number then colon in the options file
# we can find the line which starts with the number selected
# we use grep to do this and then cut to get the script name from 
# that line.

# Putting the output in backticks (`) executes the output rather than 
# echoing it.
`cat $HOME/scripts/options.txt | grep "^$option:" | cut -d":" -f2`

```IF you can get this running, post back if you need help with input validation etc.

---

### Post by terranair on 2010-02-26
It worked!
Thank you!
Have some Ubuntu beans on me.

---

### Post by richardjh on 2010-02-26
No worries. That was my first post and I am chuffed it was of some use.

---

