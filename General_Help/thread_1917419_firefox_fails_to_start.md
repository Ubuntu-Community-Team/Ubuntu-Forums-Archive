---
title: "firefox fails to start"
date: 2012-01-30
forum: General Help
---

### Post by fuzzman17 on 2012-01-30
I'm a semi-noob to Linux.  I did a complete reinstall of Ubuntu 11.10. I had backed up my personal settings folder in firefox before the reinstall. I had started firefox to make sure my networking was okay. I shut down firefox and started Nautilus from termial using "sudo nautilus"  I deleted the personal settings file created when firefox first ran and renamed my backup the same as the deleted file and replaced it. Then I closed terminal and then closed nautilus. I think this may be where I screwed up. anyway now every time I try and start firefox I get an error message. 

"Firefox is already running , but is not responding. To open a new window you must first close the existing firefox process or restart your computer." 

I have to run firefox from terminal using "sudo firefox". Firefox is not listed as running under system monitor and I have rebooted the computer several times. I haven't tried to uninstall and reinstall firefox yet fearing it might make things worse. Any one have any ideas as to what I should do?

---

### Post by carl4926 on 2012-01-30
Firefox settings are in /home/yourusername/.mozilla
sudo is not required
So I am wondering what exactly you have been doing.

All I ever do is keep a backup of ~/.mozilla

---

### Post by fuzzman17 on 2012-01-30
I had done it once before with an earlier version of firefox in terminal. I remembered having to have super user privileges to do it then, I just assumed the same would still be true. I do recall the instructions saying that I had to find the hidden file and then instructing on how to do it. I guess it's true, I do know just enough to be dangerous. :D

---

### Post by sikander3786 on 2012-01-30
Did you simply try re-installing Firefox?

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

If it still says that Firefox is already running, from Terminal, trying killing any running instances:

```
ps axjf | grep firefox
```

And try opening it again.

Also try opening Firefox in safe mode from the Terminal and see if any extensions are causing the problem:

```
firefox -safe-mode
```

---

### Post by fuzzman17 on 2012-01-30
I'll try it in the morning. had a rather lengthy question a had to answer for my nephew. off to bed now.

---

### Post by fuzzman17 on 2012-01-30
Okay  I laid in bed for nearly an hour and couldn't sleep so I thought I'd give Sikander3786's suggestions a try. None of them worked. I gave some thought to what could make the system think firefox was still running. It hit me that a file that the system though was in use for some reason might do it. The only files that I knew of that weren't removed during the purge where the ones in the .mozilla folder. I uninstalled firefox again, deleted the .mozilla folder, did a cold reboot to be safe, and reinstalled firefox.  Everything is working fine now. 
Thanks Sikander3786, You got me close enough to fix it.

---

### Post by goofey24 on 2012-01-30
glad you got it sorted.
please go to 'Thread Tools' and mark 'Solved'

---

### Post by moonport on 2012-01-30
Thanks for the tip, fuzzman17. I've the same issue.
Best.

---

