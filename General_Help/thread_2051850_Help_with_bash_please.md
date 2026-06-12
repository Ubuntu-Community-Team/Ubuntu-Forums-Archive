---
title: "Help with bash please"
date: 2012-09-02
forum: General Help
---

### Post by mike177 on 2012-09-02
Hello everyone, this is my first post in Ubuntu Forums! ):P

I'm trying to convert a Windows "bat" file to a Ubuntu "sh" file but as much as I tried, I couldn't find the necessary commands. I'm not sure if it's even possible in bash. Here's the script:

@echo off
set /P URL= URL=
set /p a= Tabs=
set b=0
:loop
set /a b=b+1
start %url%
goto :if2
:if2
if %a%==%b% exit
if not %a%==%b% goto :loop

If anyone can help me I really appreciate it. Oh, and sorry if the thread doesn't belong to General Help #-o .Have mercy:)

---

### Post by Kopkins on 2012-09-02
What is the purpose of the script? It might be easier to write a new script instead of trying to substitute commands. 

If you want, [The Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/").

Note that this script is very incomplete, It won't do anything. I don't know what the url bit is about so left it doing nothing.

EDIT: After looking at the bat file more it looks like it is pretty simple. I can't figure out what the URL bit is about, but otherwise here...```

#!/bin/bash
#set URL variable.. not sure what this does.. setting to the value of browserurl
URL=$browserurl
#I'm guessing that this script has something to do with a browser. I don't know how to pull variables from a browser.
#set a to number of open tabs.. 
a=$tabs
b=0
while [ $a != $b ] 
do
let b+=1
#not sure what start does, just putting an echo.
echo $URL
done
exit

```
Best of luck,
Kopkins

---

### Post by mike177 on 2012-09-02
This script generates Youtube views. You enter the URL of the video and how many views you want. If you want 10 for example, when you hit enter it will open 10 tabs of that video.

EDIT:
Finally complete! Same functionality as the windows version! Here's the script:

#!/bin/bash 
read -e variable1
read -e number
COUNTER=0
         while [  $COUNTER -lt $number ]; do
             xdg-open $variable1
             let COUNTER=COUNTER+1 
         done
sleep 60

And thanks Kopkins for the quick reply!

---

