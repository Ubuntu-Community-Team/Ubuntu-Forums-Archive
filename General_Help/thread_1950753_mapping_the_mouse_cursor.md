---
title: "mapping the mouse cursor"
date: 2012-04-01
forum: General Help
---

### Post by MatMan on 2012-04-01
If I put this in the wrong forum, sorry.

I am a PhD student in biology, and I have videos of lizard to watch. I need to keep continual track of the lizards through time as they walk around a 2d arena. 

The solution I have is to hover the mouse over the lizard in the video, and follow it with the cursor. 

I am looking for a way to record X and Y coordinates of the mouse with a time keeper, possibly something like:

x     y     seconds
1     15    0
1     16    0.01
2     17    0.02


etc.  

Do you know a way I can do this?

---

### Post by HiImTye on 2012-04-02
```
sudo apt-get install xautomation
```MousePoll.sh
```
#!/bin/bash
while :; do
sleep 1
xmousepos >> mousepos.txt
done
exit
```output will be in the form of
x y x_RelativeToCurrentWindow y_RelativeToCurrentWindow

for example:
```
tye@T:~$ xmousepos
249 831 249 805
```it will update once every second. to make it more or less often, change the value of 'sleep #'

---

