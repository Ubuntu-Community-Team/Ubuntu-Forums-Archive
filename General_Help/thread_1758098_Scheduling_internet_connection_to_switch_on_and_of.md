---
title: "Scheduling internet connection to switch on and off"
date: 2011-05-14
forum: General Help
---

### Post by Raguraman on 2011-05-14
Hello i am Raguraman and i live in India. The broadband access here is charged according to the data usage and it is free from 2 am to 8 am.
My problem is i need the eth0 connection up at 2 am and down at 8 am.
I have manged to find out that the command 
sudo ip link set eth0 up/down 
does the job from the terminal but the problem is it prompts for the password each time it is executed so when i schedule it using crontab it does not work. Is there anyway of that the above problem can be acheived. I am new to ubuntu and i faced a similar problem in windows and managed to solve it using the .bat scripting and the windows scheduler.
Thanks for the help.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by dabl on 2011-05-14
It would have to be a shell script running with root privileges. Assuming that you have written the script that checks the time once per minute, and activates/deactivates eth0 at 2:00 a.m. and 8:00 a.m., then you would start the script with "sudo":

```
sudo sh eth0monitor.sh
```

and just let it run.

---

