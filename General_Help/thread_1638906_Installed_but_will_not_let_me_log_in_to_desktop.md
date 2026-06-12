---
title: "Installed but will not let me log in to desktop"
date: 2010-12-06
forum: General Help
---

### Post by testforecho on 2010-12-06
I installed ubuntu desktop and it seems to install w/o problems. I set up a name and password as part of the installation. When it re-boots to the login screen, it will not accept my name and password. I keep getting looped back to the login screen. 
 
I tried 3 re-installs with simple names & passwords and none work. I also tried checking 'log in automatically' on 2 of the 3 re-installs. No luck. Any suggestions?

---

### Post by TheAnachron on 2010-12-06
Are you sure you have added the correct keyboard layout?
If you choose a passwort like "Ärger" it may not see the typed letter as "ä" but whatever the keyboard language is set to.

Another example: In English the keys "z" and "y" are changed, so whenever you want to write an y on a german keyboard with english setting, you need to type the z.

---

### Post by airplanesimen on 2010-12-06
hey! i maybe know how to help you?

press ctrl+alt+F1 button,at the logon screen (to exit simply press ctrl+alt+F7) then it will come up a black scrren saying your computer name, and what account you want to log on with. there you have to type "root" with no passwd. then type "sudo passwd <your username>" and hit enter.
then you have to type yor new passwd. type exit and then "ctrl+alt+F7" and try again at the logon screen.
questions, please mail me... (faster answer) -->airplanesimen@gmail.com

---

### Post by testforecho on 2010-12-06
> **airplanesimen said:**
> hey! i maybe know how to help you?

press ctrl+alt+F1 button,at the logon screen (to exit simply press ctrl+alt+F7) then it will come up a black scrren saying your computer name, and what account you want to log on with. there you have to type "root" with no passwd. then type "sudo passwd <your username>" and hit enter.
then you have to type yor new passwd. type exit and then "ctrl+alt+F7" and try again at the logon screen.
questions, please mail me... (faster answer) -->airplanesimen@gmail.com

Thanks for the suggestions. I tried to use CTRL+ALT+F7. When I do that I get a screen that is ubuntu colors that are pixelated like the video is bad. But when I am at the normal login screen the video is fine so I don't think I have a card issue.  

That said, there's something not right about how ubuntu is working with the PC. I changed the login user to 'a' and made the password 's' to make it as simple as possible. It seems like when I login, ubuntu loops and tries to log me in and then comes back to the main screen and I have to try again, to no avail.  

Any ideas?

---

### Post by Bitrate on 2010-12-06
Caps lock on/off ?

---

### Post by testforecho on 2010-12-07
> **Bitrate said:**
> Caps lock on/off ?

tried both

---

### Post by airplanesimen on 2010-12-07
> **testforecho said:**
> Thanks for the suggestions. I tried to use CTRL+ALT+F7. When I do that I get a screen that is ubuntu colors that are pixelated like the video is bad. But when I am at the normal login screen the video is fine so I don't think I have a card issue.  

That said, there's something not right about how ubuntu is working with the PC. I changed the login user to 'a' and made the password 's' to make it as simple as possible. It seems like when I login, ubuntu loops and tries to log me in and then comes back to the main screen and I have to try again, to no avail.  

Any ideas?

Hello again... that seemed unknown to me... (btw we got the same passwd) have you tried the failsafeX mode in the recoveryconsole? maybe that can help you... just follow the steps i gave you, there:P if that doesnt work, you may have to use an older version of ubuntu:( (can you tell me what kind of computer/pcspecs you have?) Hey, i got the same problem with my vid. card! You dont have any proper driver innstalled. it is  just running in a compitable mode. (i got the same problem with the pixels when i was hitting ctrl+alt+F7, i had to restart my computer all the time)

---

### Post by testforecho on 2010-12-07
Ok. Thanks. I'll try an older version and your suggestions when I get some time.   Thank you for all of your help.

---

