---
title: "Virtual Box Autostart"
date: 2009-10-18
forum: General Help
---

### Post by kevinrogers1977 on 2009-10-18
i am trying to get virtual box to auto run from boot.

i have installed VBoxGtk. (after experimenting with others vmplayer ,sun virtula box ose, found this to be only one that run in actully full screen (fills up the whole screen)

Senario

i am running ubuntu 9.04 with LAMP and want this sytem running all the time.
other users in the house hold use XP ,so i want this to run after ubuntu has started up(virtually).

i Have made a excucutible script to run the Virtul Box (windows XP)

VBoxSDL -vm "WindowsXP" -fullscreen

i used sudo chmod 755 /home/kev/Desktop/Run XP.sh  to make it executible.

i have tryed adding it to "startup applications" 
also i have tryed 
adding the command  to .rclocal in /etc
and also copying script into \etc\init.d 

all effort result in normall boot but

atm moment it have i icon in middle of desktop to run xp
 however i jus want this to run automaticall from boot
"this is easy on xp/vista/7"

:confused: puzeled to why the command dont work ,cuz it d:confused:oes from terninal or runing the script

---

### Post by falconindy on 2009-10-18
My first thought is: get rid of the space in the filename.

---

### Post by kevinrogers1977 on 2009-10-18
tried that but with no success

when there is a space in the filename i usually "/home/kev/my file" it.

but the command has no space why dont that work in .rclocal
 other commnads do work

i have .rclocal ,/opt/lamp start 

and pidgin in startup applications

---

### Post by kevinrogers1977 on 2009-10-19
i still  cant get i to run from boot, anyone else have any suggestions

thanks to the advice on the space , i thought that would be it.... 

still puzzeled
:confused:

---

### Post by P4man on 2009-10-19
How exactly are you trying to start this on bootup ?
If the command works in a terminal (does it ?) then add it to start up applications in system > preferences > startup applications.

> "this is easy on xp/vista/7"

Its only easy because you know how to do it.

---

### Post by kevinrogers1977 on 2009-10-19
i have already tryed that

and i confirme the command does work from terminal.

i have already tried startup applications.

i have read several different methods.

none successful.

thanks for the advice thou.

i gonna try find the full command location. and try that any ideas where it is located?

---

### Post by P4man on 2009-10-19
Perhaps you have to add a delay so the VB session gets initiated after something else is loaded.

Try adding this:
```

sleep 5 && VBoxSDL -vm "WindowsXP" -fullscreen
```

That will wait 5 seconds before attempting to start the vm.

---

### Post by kevinrogers1977 on 2009-10-19
good thinking i was wondering if a deley might be needed but dint know how to do it

but that what forums are for.
i will get back to you if it works

got baby to attend to

will post result


excellent thinking:P:P:P:P:P

---

### Post by kevinrogers1977 on 2009-10-19
Although adding the delay start "sleep 5 &&" did work in terminal adding a delay of exactly 5 seconds, it did not work in start up ...... just like to say thanks for this command cuz i wanna use it with another issue (wireless connection).

[B]However .... i got my thinking cap 
 
[/B]it runs in terminal why not in start application.

let run it in terminal as a command

:)**bingo:P** 

gnome-terminal --command="VBoxSDL -vm "WindowsXP" -fullscreen"

[B]WORKED

Thanks to the help it led me to find a soloution, Long live ubuntu,lol
 thanks [/B][falconindy]("http://ubuntuforums.org/member.php?u=863375") & [P4man]("http://ubuntuforums.org/member.php?u=412374"):P

now i have a server running with xp in  virtualbox automatcally 

boot sequence is rather amusing ,lol booted


:popcorn:

---

### Post by P4man on 2009-10-19
and how are they supposed to turn the machine off ? :p

---

### Post by kevinrogers1977 on 2009-10-19
it a server as well ,i dont want it tured off

but xp can be shutdown in normal way , and you can restart it by button on top and bottom toolbars and in middle of desktop..

:guitar:

it does what i wanted to do ,

---

