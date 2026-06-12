---
title: "Desktop is not working!!!!!!!!Need urgent help"
date: 2009-09-14
forum: General Help
---

### Post by nabeelsadiq on 2009-09-14
so every time i turn on my computer it takes me to the log in screen, i type my username and psswrd, but then it just takes me to a blank pinkish screen, there is absolutely nothing on the screen except for the mouse, so i tried something: i plugged in my ipod and the file manager came up, through that i was able to access the internet, do you guys have any idea how i can get my desktop back? is there something i can do through the terminal, cuase i am also able to open that....any help will be greatly appreciated, a thanks in advance

---

### Post by nabeelsadiq on 2009-09-14
so every time i turn on my computer it takes me to the log in screen, i type my username and psswrd, but then it just takes me to a blank pinkish screen, there is absolutely nothing on the screen except for the mouse, so i tried something: i plugged in my ipod and the file manager came up, through that i was able to access the internet, do you guys have any idea how i can get my desktop back? is there something i can do through the terminal, cuase i am also able to open that....any help will be greatly appreciated, a thanks in advance

---

### Post by MelDJ on 2009-09-14
try typing **xfce-panel** in terminal

---

### Post by nabeelsadiq on 2009-09-14
tried it...no luck it says command not found      :(, thanks though

---

### Post by MelDJ on 2009-09-14
did you try xfce4-panel?

---

### Post by scouser73 on 2009-09-14
You could try the instructions in this tutorial: [[COLOR="Red"]**Xubuntu**[/COLOR]]("http://www.psychocats.net/ubuntu/xubuntu")

---

### Post by nabeelsadiq on 2009-09-14
so every time i turn on my computer it takes me to the log in screen, i type my username and psswrd, but then it just takes me to a blank pinkish screen, there is absolutely nothing on the screen except for the mouse, so i tried something: i plugged in my ipod and the file manager came up, through that i was able to access the internet, do you guys have any idea how i can get my desktop back? is there something i can do through the terminal, cuase i am also able to open that....any help will be greatly appreciated, a thanks in advance

---

### Post by nabeelsadiq on 2009-09-14
oh my god thank you sooooo much, it brought back the desktop,
but there is still a problem
i still dont have the bar on the top that lets you close/minimize buttons, and as i open new windows they dont appear on the task bar at the bottom, i also dont have workplaces, any idea whats up with that?

---

### Post by MelDJ on 2009-09-14
right click the panel and press add to panel. then you will be able to add all the applets. by the way, dont triple post the same problem in different places. be more patient :popcorn:

---

### Post by nabeelsadiq on 2009-09-14
strange.. the taskbar on the bottom disappeared as well

---

### Post by MelDJ on 2009-09-14
right click the panel you have and press new panel. then drag it to wherever you want it...top, bottom,right or left

---

### Post by nabeelsadiq on 2009-09-14
haha, you are right, i should be more patient
ok i am not exactly sure where you want me to right click, what is the panel? do you mean on the window? sorry i have little knowledge on these things

---

### Post by MelDJ on 2009-09-14
its the bar on top of your desktop with applications menu,the time, etc

---

### Post by nabeelsadiq on 2009-09-14
oh well thats on the bottom on my computer, well it was on the bottom, now its gone

---

### Post by MelDJ on 2009-09-14
did you close the terminal?

---

### Post by nabeelsadiq on 2009-09-14
i believe so , theres no way me to find out, i have to close out from firefox to see cause i am unable to move this window
but if i did close it, is that the reason the panel went away?

---

### Post by MelDJ on 2009-09-14
yes. add a new panel then close it. you can press alt then tab to switch between windows too

---

### Post by nabeelsadiq on 2009-09-14
alt+tab didnt work for me i had to close the terminal again to get to firefox, so the panel again is gone

---

### Post by MelDJ on 2009-09-14
then write the steps i told you to do on a piece of paper, then do them. then you wont need to go to firefox:popcorn:

---

### Post by nabeelsadiq on 2009-09-14
add new panel wasnt one of the options when i right clicked it, there was a customize panel, move, proerties, but still every window i open still doesnt have the close/minimize button on the top bar, and they dont show up on the panel

---

### Post by MelDJ on 2009-09-14
try customize panel

---

### Post by nabeelsadiq on 2009-09-14
ok so i made another panel, which also went away when i closed the terminal

---

### Post by nabeelsadiq on 2009-09-14
ok i have to go now, ill check this later tomorrow, thank you so much for your help!! i dont believe how nice people like you are, just going on forums and helping people, we need more people like you in this world :D

---

### Post by MelDJ on 2009-09-14
try this in terminal:
sudo apt-get install --reinstall xfce4-panel
or sudo apt-get remove xfce4-panel then sudo apt-get install xfce4-panel

---

### Post by cariboo on 2009-09-14
A bump for the merge

---

### Post by nabeelsadiq on 2009-09-18
hello again,
ok so now when i open my computer i have the panel and the desktop running
but for some reason, all the windows close randomly, like firefox, and opera,
it just closes, and also, i dont have Thunar anymore, so i downloaded it from their web site, and unzipped it, but when i enter the ./configure command, it says 

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

so i cant install it, so i cant access my file manager

---

