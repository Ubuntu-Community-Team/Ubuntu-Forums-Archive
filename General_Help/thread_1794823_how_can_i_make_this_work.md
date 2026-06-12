---
title: "how can i make this work"
date: 2011-07-01
forum: General Help
---

### Post by bettaproger on 2011-07-01
what i have is two command sets that i want to reduce to one single alias but i can not figure out how to make them work

alias 1='mkdir temp && mv *.xbox.avi temp && rm * 2> /dev/null'
alias 2='cd temp && mv * .. && cd .. && rm -r temp'

the problem is the last command in alias 1 always produces an error that stops the line so i had to break it into two pieces, but if it could be one piece streamline lots of operations
please help

---

### Post by WorMzy on 2011-07-01
If you just want to delete everything /except/ those .xbox.avi files, try this.

```
rm $(ls | grep -v ".xbox.avi")
```

This command will feed the output of

```
ls | grep -v ".xbox.avi"
```

into rm. The ls will list everything in the folder, but grep will filter out and filenames with ".xbox.avi" in their name.

You'll still get an error regarding any folders in the folder that you run the command in, but that's silenceable with the redirect you're already using.

Oh, and if you'd prefer to just fix the aliases you have, add a ; after the rm command, rather than a double ampersand.

Double ampersands mean "If the previous command doesn't give an error, run the next command"
Semi-colons mean "After the previous command finishes, run the next command"
Double pipes ( || ) mean "If the previous command gives an error, run the next command"

```
alias 1='mkdir temp && mv *.xbox.avi temp && rm * 2> /dev/null; cd temp && mv * .. && cd .. && rm -r temp'
```

---

### Post by bettaproger on 2011-07-01
thanks for the elegant solution

EDIT: not working with files that have spaces in the names. any ideas. i tried including  IFS='\n'

---

