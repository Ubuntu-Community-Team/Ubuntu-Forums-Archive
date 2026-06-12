---
title: "Script runs fine in terminal, but segfaults when run with crontab"
date: 2011-03-14
forum: General Help
---

### Post by b0ot on 2011-03-14
I have a script that I wish to start @reboot with root privileges. 
I added a line to my crontab to get the script @reboot. 
The script starts but it segfaults when it gets to the point that it calls a program to start my mpegencoder. 

I thought it might be something to do with the environment and I did confirm if I ran the script with env - in the terminal it would also segfault. However even after setting the $PATH and $TERM in the script the script still segfaults with crontab

---

