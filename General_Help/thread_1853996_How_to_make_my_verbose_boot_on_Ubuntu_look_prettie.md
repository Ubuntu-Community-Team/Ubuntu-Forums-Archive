---
title: "How to make my verbose boot on Ubuntu look prettier?"
date: 2011-10-03
forum: General Help
---

### Post by TuxIsAwesome on 2011-10-03
Basically I want to have when I boot in verbose mode

An Ubuntu logo in the upper left or right corner 
A background image. 
Colored Text output (Failed Processes=red, sucessful processes=green)

I dont want a splash such as plymouth and whatnot because I find those sorts of bootscreens to be useless and uninformative. I likes me smexy verbose output

How might I go about all this? I'd even be willing to drop the idea of having colored text output so long as I have a background image and an ubuntu logo.

---

### Post by mcduck on 2011-10-03
I have no idea about logo or background, but on the other hand I *can* tell you how to get the colored text... ;)

Failed processes should already be colored red by default, so you'll only have to worry about getting the green color for the OK messages. And to do that you'll need to edit */etc/lsb-base-logging.sh*

Find the *echo "[ OK ]"* -line inside the *log_end_msg ()* function and replace it with the following piece of code:
```

printf '[ '
$TPUT setaf 2 # green
printf OK
$TPUT op # normal
echo ' ]'
```
(I haven't tried this on 11.04, but it should work just fine. And at least for me the correct line to replace is number 108. Actually you'll see pretty similar section of code just underneath for the red colored "fail"-messages.)

---

### Post by TuxIsAwesome on 2011-10-03
> **mcduck said:**
> I have no idea about logo or background, but on the other hand I *can* tell you how to get the colored text... ;)

Failed processes should already be colored red by default, so you'll only have to worry about getting the green color for the OK messages. And to do that you'll need to edit */etc/lsb-base-logging.sh*

Find the *echo "[ OK ]"* -line inside the *log_end_msg ()* function and replace it with the following piece of code:
```

printf '[ '
$TPUT setaf 2 # green
printf OK
$TPUT op # normal
echo ' ]'
```(I haven't tried this on 11.04, but it should work just fine. And at least for me the correct line to replace is number 108. Actually you'll see pretty similar section of code just underneath for the red colored "fail"-messages.)

Yep! That definately give me my green succeeded messages! Thanks!

Now I just need to figure out the background and logo, if thats even still possible as of 11.10.

---

### Post by seawolf167 on 2011-10-03
And you don't want to use anything [like]("http://code.google.com/p/burg/") [*BURG*]("https://help.ubuntu.com/community/Burg")?

---

