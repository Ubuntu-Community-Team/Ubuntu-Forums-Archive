---
title: "Scripting Help"
date: 2010-01-18
forum: General Help
---

### Post by Lambchopper on 2010-01-18
I'm new to Linux Scripting but I've written quite a few VBScripts and Batch scripts on Windows in my time.  I can't seem to figure out why I can't get the IF statement to evaluate True so that the script exits if the user enters anything other than y. I also found very similar code that uses this very same syntax and format, but my code won't eval true to exit the script and I can't figure out why.  Any Ideas?

```
echo "This will empty the Trash, procede with script (y/n)?"
read REPLY

if [[ $REPLY -ne "y" ]]; then
     exit
fi
```

I've tried it with the $REPLY variable both quoted and unquoted.

---

### Post by synapsys on 2010-01-18
What does it do if the answer is "y" ??

---

### Post by Lambchopper on 2010-01-18
y should just continue the script and n or any other unrecognized user input (e.g. typo) should eval true and terminate the script.

In other words, if the user enters anything other than y exit the script.

---

### Post by synapsys on 2010-01-18
Have you tried declaring "y" as a string e.g.

```
yes=y
echo "This will empty the Trash, procede with script (y/n)?"
read REPLY

if [[ "$REPLY" -ne "$yes" ]]; then
     exit
fi
```

---

### Post by kaibob on 2010-01-18
Change '-ne' which is meant to be used with integers to '!=' which is meant to be used with a string, and the script will work as you want. The script doesn't do anything other than exit, but I guess you know that.

```
#!/bin/bash

echo "This will empty the Trash, procede with script (y/n)?"
read REPLY

if [[ $REPLY != "y" ]]; then
   echo "You did not answer yes!"
   exit
fi
```

---

### Post by Lambchopper on 2010-01-19
> **kaibob said:**
> Change '-ne' which is meant to be used with integers to '!=' which is meant to be used with a string, and the script will work as you want. The script doesn't do anything other than exit, but I guess you know that.

```
#!/bin/bash

echo "This will empty the Trash, procede with script (y/n)?"
read REPLY

if [[ $REPLY != "y" ]]; then
   echo "You did not answer yes!"
   exit
fi
```



Sweet, that was the ticket!   Thank you!!!

---

