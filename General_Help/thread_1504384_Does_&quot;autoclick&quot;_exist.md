---
title: "Does &quot;autoclick&quot; exist?"
date: 2010-06-07
forum: General Help
---

### Post by dolphinsonar on 2010-06-07
Hi,

I can think of a lot of different situations when being able to "autoclick" would be really useful.  By autoclick, I mean that I want to be able to hold down the left-click button and have it rapidly clickity clickity clickity as fast as the processor can handle.

One example is games where I have a semi-automatic weapon and I have to hammer the mouse button with my finger.  It would be nicer to reduce the wear and tear on my trackpad.

Does such a thing exist?

---

### Post by dcstar on 2010-06-08
> **dolphinsonar said:**
> Hi,

I can think of a lot of different situations when being able to "autoclick" would be really useful.  By autoclick, I mean that I want to be able to hold down the left-click button and have it rapidly clickity clickity clickity as fast as the processor can handle.

One example is games where I have a semi-automatic weapon and I have to hammer the mouse button with my finger.  It would be nicer to reduce the wear and tear on my trackpad.

Does such a thing exist?

System-Preferences-Mouse.

---

### Post by Breambutt on 2010-06-08
Gonna have to try this myself...

...on [http://homokaasu.org/killeveryone/](http://homokaasu.org/killeveryone/)

---

### Post by sanderd17 on 2010-06-08
you could make a simple script with xdotool (I think it will be about 4 lines). it will be a simple bash script. than, you can use a shortkey to activate it I guess (if shortkeys work outside the game). 

You will have to find a way to stop it, maybe with another script and a kill command, maybe just let it shoot 10 times so you'll have to press 10 times less the key than you would click.

---

### Post by sanderd17 on 2010-06-08
made this script for 100 clicks:

```

#!/bin/bash

for i in {1..100} 
do
   xdotool click 1
done

```

save this code in a file click.sh

make it executable

Before you test it:

Do ctrl+alt+F1
login under your account
set the line 
```

killall click.sh

```
ready

go back with ctrl+alt+F7

test the scipt on a piece of text to see if it clicks, DO NOT MOVE THE MOUSE TO SOMETHING CLICKABLE.

When something goes wrong: go back to the terminal ctrl+alt+F1 en press enter to execute the kill command.

---

### Post by bkoltai9 on 2010-10-20
I used the code you wrote for this page with the following change:


#!/bin/bash

for i in {1..100000} 
do
   xdotool click 1
done


I use this for an autoclick program for approx. 20 minute gaming sequence.

I wonder if this encoded to include pauses or timeout between clicks.  This game sequence should only take about ten minutes, but the autoclick slows my processor so much that it slows it way down.

If I could put in a 5 second pause between clicks, I'm sure I could reduce the total number of clicks by a factor of 100.

Thanks for your help and thanks for the great code.

---

