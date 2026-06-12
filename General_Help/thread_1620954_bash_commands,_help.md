---
title: "bash commands, help"
date: 2010-11-13
forum: General Help
---

### Post by da_n0n3 on 2010-11-13
Hello everyone

I have a question about a bash script... shell commands...

I have a script --> WEP.sh and i want to open severel new processes in a second shell

.
.
.
gnome-terminal -e "airmon-ng check"   #this is working... but is there any possibility to execute other commands in a row in that same newshell for example airmon-ng stop wlan1 or sleep 10 or echo....???? 
.
.
.

thx a lot for any suggestions!

---

### Post by nothingspecial on 2010-11-13
> **da_n0n3 said:**
>  but is there any possibility to execute other commands in a row 

When you say in a row, if you mean when one command exits, start another one, simply seperate them with &&

---

### Post by da_n0n3 on 2010-11-14
thank you for the quick answer!!

let me give you a sample with what i exactly want...

```

#!/bin/bash

# mother.sh
# this script is running as motherscript and should open a childshell, communicate and shutting it down...

clear

echo "where is my child?"
sleep 5


# this should open a new "childshell" and give out this line and stay alive for other commands....
gnome-terminal -e 'echo "Mam, I am here...!"' &       # is it possible to give this new shell a name like --> CHILDID=$!   ...  && will only run the following command in the mothershell:(


# now i want to go on in the motherscript... with the childshell staying open and waiting for a new command...
echo "Ahh ok, do you want something to eat?"
sleep 5

gnome-terminal -e 'echo "No, thank you...' &  # give out this line in the childshell...

echo "allright then!"

#kill CHILDID ?????????

exit 0
```


I hope this little example explains it  :confused:... And is it even possible to run a for or a while command in the new "childshell" and give parameters back to mothershell (in our example. "No, thank you..."??


thank you for the help

da_n0n3

---

