---
title: "Script to make a process restart after quit?"
date: 2010-05-19
forum: General Help
---

### Post by Darkness Des on 2010-05-19
I have a drop down terminal called Guake. Every time I edit my .bashrc file, I have to restart it to get it to accept that changes. I also have to restart it often for other various reasons. I want to make a script that will reopen Guake everytime it is closed, and stop when I kill the script. Is this possible?

---

### Post by utnubuuser on 2010-05-19
Search around a little, you might just find the command to 'refresh' guake instead of restarting - as can be accomplished in bash, then all you'd need is an alias in your bashrc file to execute...

---

### Post by Darkness Des on 2010-05-19
Although I may know the basics of BASH, I apparently have a lot to learn. Thank you, I found a working solution. After I edit the file, all I have to do is
```
source ~/.bashrc
```
and Guake will recognize the changes I've made. That was a lot less complex than I was trying to make it be.

---

