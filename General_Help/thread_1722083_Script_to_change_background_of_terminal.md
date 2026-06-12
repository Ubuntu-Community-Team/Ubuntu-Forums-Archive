---
title: "Script to change background of terminal"
date: 2011-04-05
forum: General Help
---

### Post by Spyderkid on 2011-04-05
I want to make a script to ask what colour you want the terminal background to be.

However this seems to be quite hard for a newbie on bash scripts.

What I've got so far is this...
```

#! /bin/bash

COLOR=blue
setterm -term linux -back $COLOR -fore white -clear
echo "It's a $COLOR day!"
sleep 1

fi

```

how do I add a beggining to the script to make it so it asks you what colour you want and then processes that into the variable.

what i've got so far for that is this.. (it doesn't work)

```

echo "What colour would you like?"
read answ
if [ "$asnw" = (not sure what to put here) ]
then
          (don't know what to do from here on)

```


Help anyone?
:guitar:

---

### Post by blind2314 on 2011-04-05
> **Spyderkid said:**
> I want to make a script to ask what colour you want the terminal background to be.
 
However this seems to be quite hard for a newbie on bash scripts.
 
What I've got so far is this...
```

#! /bin/bash
 
COLOR=blue
setterm -term linux -back $COLOR -fore white -clear
echo "It's a $COLOR day!"
sleep 1
 
fi

```
 
how do I add a beggining to the script to make it so it asks you what colour you want and then processes that into the variable.
 
what i've got so far for that is this.. (it doesn't work)
 
```

echo "What colour would you like?"
read answ
if [ "$asnw" = (not sure what to put here) ]
then
          (don't know what to do from here on)

```
 
 
Help anyone?
:guitar:
 ```

echo "What color would you like?"
read COLOR
setterm -term linux -back $COLOR -fore white -clear
echo "It's a $COLOR day!"
sleep 1

```
 
There you go, no need for any conditional statements.

---

### Post by tredegar on 2011-04-05
Well, you've made a start, so here's a little help......
```
echo "What colour would you like?"
read answ
setterm -term linux -back $answ -fore white -clear
```
There's no error checking though. For that you might look at
```
case $answ in
red)
code goes here
;;
blu|blue|lightblue)
code goes here
;;
*)
Echo "I don't know that colour"
exit 1
```

---

### Post by Spyderkid on 2011-04-05
Edit out

---

### Post by nsk tacticzz on 2011-04-05
> **Spyderkid said:**
> Edit out

once u finished it, can u send me script so i can change my background colour :)

---

### Post by tredegar on 2011-04-05
> **Spyderkid said:**
> Edit out
What is that supposed to mean?

---

### Post by Spyderkid on 2011-04-06
> **tredegar said:**
> What is that supposed to mean?

I made a post and decided i didn't mean to so i edited it out

---

### Post by Spyderkid on 2011-04-06
Here's my finished script, it now asks you for background and foreground colour....
```

#! /bin/bash

#script to change colour of terminal.
echo "What background colour would you like?"
read BACK
echo "What foreground colour would you like"
read FORE
setterm -term linux -back $BACK -fore $FORE -clear
echo "It's a $BACK and $FORE day!"
echo "Press a key to exit"
read -n 1
echo "\nYou pressed a key!"

sleep 2

fi
```

---

