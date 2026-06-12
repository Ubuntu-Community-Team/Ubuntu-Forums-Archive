---
title: "wifi disconnection on ubuntu 10.04 Beta2"
date: 2010-04-20
forum: General Help
---

### Post by ashjas on 2010-04-20
Hi,

This has happened before with ubuntu 9.1 Beta2 build too that my wifi disconnects if im idle for 5 minutes... so i cant leave my lappy to download anything... i have to keep on continuously using it.. as soon i leave it idle for abt 5 minutes... wifi disconnects... and the pop up asking for password for wifi pops up...with the password already filled in... i just click on connect and it connects again... so whats the use of asking the password if the pre filled in pass works correctly... 

and this is happening on ubuntu 10.04 Beta2 too...

and the workaround is that just open any menu like the applications menu in the taskbar and keep it open... under this state the ubuntu idleness never activates and so the wifi gets never disconnected... this has been confirmed by me many times..

this seems to be repeating again and again... i dont know why...

and the second thing i want  to report is that there is no way to report this bug from ubuntu... the launchpad.net talks of going through bug reporting process which is done against a definite package... now how does a user know which package would be causing this error?? there should be a more clear process of reporting such bugs to ubuntu team...

thirdly the apport utility that reports crashing apps is totally uselss on 10.04 beta 2... as it collests information and reports that i cant submit the report because i dont have 100 other packages... without updating which i cant submit the report.... surely on a beta build there would be packages continuously being updated... so no system would be reported as fully updated... and so no practical apport reporting is possible??


please address these issues... really frustrating all this ...

im a big fan of ubuntu but these things really bug me...

and just to add fourthly... the suspend/hibernate feature has never ever worked on my toshiba m70-113 laptop... on any ubuntu version... always have to hard reboot after putting into suspend/hibernate mode..

on windows this has never been the case... why cant ubuntu beat windows in such cases too?? i would really like to see this soon...

Thanks.

---

### Post by agnes on 2010-04-20
Did you check your settings under System>Preferences>Power Management?
 
A workaround could be if you just prevent the laptop from going idle, by making mouse movements with a command line tool. symox, xmacro and xdotool can do that. Write a script that makes a mouse movement every few minutes and make it autostart.

---

