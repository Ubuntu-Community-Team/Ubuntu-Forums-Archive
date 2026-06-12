---
title: "sound device not working"
date: 2010-11-20
forum: General Help
---

### Post by vik.gelin on 2010-11-20
hi i am using ubuntu karmic 9.10..it was working fine .but suddenly the sound device stopped working.now the option for increasing sound is not visible only.when i click on the ''sound'' in preference menu..it is not opening anything.what can i do now...plz help ...this problem started when an error occurred in my system .....''cant update .ICEauthority file in home/vikram/.ICEauthority '' when i start my system ,,after entering password in the login window this error appears.and when i cancel it ,,then ,my desktop loads.
no sound is on my system now....whether i play vlc or anythng..

and skype call recorder is also unable to record anythng due to this ...
plz help.

---

### Post by vik.gelin on 2010-11-20
guys plz help me.....ok it tell u the whole storey how it started ,,,recently i started one more thread related to my system and after that problem was solved the new one started as follows:::
<''cant update .ICEauthority file in home/vikram/.ICEauthority ''
Verback helped me by this way:

the error you're getting means the system cant write to the file: its an   authentication file used by programs. to fix it, after logging in, run   the following commands in a terminal.

 	Code:
 	sudo chown vikram:vikram /home/vikram/.ICEauthority 
 	Code:
 	sudo chmod 600 /home/vikram/.ICEauthority 
then log out and login as he mentioned adove but still it is showing   the same message that ""cannot update .ICEauthority file '' and it is   showing two more problems .they   are
 1.-->my sound device is not showing up ,,i cannot increase or   decrease the volume of my system,,i am able to hear the files playing in   vlc and can increase and decrease it by the vlc volume control ....but  i  cannot see the ubuntu volume control in control menu or in the   preference menu when i click on 'sound' option it fail to  open it. how   to bring my sound device working .......when later i was talking on   skype ,i was able to hear the other person speaking but my microphone   was not responding ...other person was not at all able to hear me,,i   tried a lot to bring sound control ,,but failed .... please help me..   
 2.--> my skype call recorder is also not working:cry: ,,may be it is also related to the above mentioned sound device problem....

  the name of thread is the previous thread is this[   ubuntu 9.10 crashing]("http://ubuntuforums.org/showthread.php?t=1623765")

---

### Post by vik.gelin on 2010-11-27
guys please help ..i am not able to resolve this problem

---

### Post by tajiknomi on 2010-11-27
[SIZE=2]Follow the same thread > [/SIZE][http://ubuntuforums.org/archive/index.php/t-1590835.html](http://ubuntuforums.org/archive/index.php/t-1590835.html)[]("http://ubuntuforums.org/showthread.php?p=9256244")

---

