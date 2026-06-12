---
title: "Specialized Display Scheduling"
date: 2011-02-05
forum: General Help
---

### Post by JGorden on 2011-02-05
After several weeks of tedious research and learning the basics of a new OS, I have successfully set up an Ubuntu based kiosk for my small business. The idea was to allow customers to self service their accounts and reduce paperwork. So far it has been successful. I'm already working less and getting more accomplished.
My issue is I would like to now configure a display schedule allowing the computer to enable the display during business hours and putting the display to sleep after hours. I realize that I could just turn it off and on again daily but I am simply not there to do it. I know that Ubuntu contains a scheduling program of some sort and ability to change the display settings through the terminal; how can I make these work together?
I haven't worked with a 'terminal' based/enabled OS since the DOS/Win 3.1 era, little sorry about that now. I was relatively sound in my abilities then, just in a foreign place now.  Whatever method is best to accomplish this task I'll take it, novice to expert.
Thanks,

---

### Post by Krytarik on 2011-02-05
You may try to use "xrandr" (manages outputs) in conjunction with "crontab" (scheduling), by using its "--off" option to disable the output and using its "--mode" option to enable it again. However, the "--off" option doesn't work at my machine, I guess because of the nvidia driver.

[http://manpages.ubuntu.com/manpages/maverick/en/man1/xrandr.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/xrandr.1.html)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

