---
title: "gettins samba to work properly"
date: 2010-06-06
forum: General Help
---

### Post by mick463 on 2010-06-06
Hi there i have two computers one running windows 7 and one running ubuntu 10.04.
I have installed samba on the ubuntu system and configured shares on the ubuntu comouter,I can see and write to the ubuntu comp from the windows comp but i can not see the windows computer from the ubuntu computer. When i go to  places network then click on windows network then workgroup all i get is that it is unable to mount location failed to retrieve share list from server.I am at a loss have i missed something.
Thank you in advance.

---

### Post by MedianMajik on 2010-06-06
[Check out this]("http://orice.ubuntuforums.org/showthread.php?t=1502724") to see how to resolve your problem.

---

### Post by spiky001 on 2010-06-06
is the firewall on windows blocking it
have you allowed sharing on win machine

---

### Post by mick463 on 2010-06-06
The firewall is on but it is not blocking it as i forgot to tell you that i also have a laptop running ubuntu 10.04 and i can see it from the windows computer but the other ubuntu machine cannot see it as well i get the same message and the other ubuntu laptop dose not have a firewall on it.

---

### Post by spiky001 on 2010-06-06
have you enabled sharing in windows

---

### Post by mick463 on 2010-06-06
i have sharing on but as i said before it may not be a windows thing as the two ubuntu computers that i have cannot see the shared files that they have i get the same error message.

---

### Post by spiky001 on 2010-06-06
I found this
[http://superuser.com/questions/110590/file-sharing-problem-with-windows-7-and-ubuntu-9-10](http://superuser.com/questions/110590/file-sharing-problem-with-windows-7-and-ubuntu-9-10)
post2 have a read

---

### Post by mick463 on 2010-06-06
bugger i do not have the file in the regedit   "LmCompatibilityLevel" .
It has me stumped.

---

### Post by spiky001 on 2010-06-06
is win 7 a Home addition if so you have to create file
[http://forum.qnap.com/viewtopic.php?f=11&t=27509](http://forum.qnap.com/viewtopic.php?f=11&t=27509)

---

### Post by mick463 on 2010-06-06
did it and got the same error.

---

### Post by spiky001 on 2010-06-06
Think i,m all out of ideas I havn't got Win7 so cant try things only xp or ubunutu which all connect sorry btw if you want to connect 2 linux you need ssh server

---

### Post by mick463 on 2010-06-06
Thank you for all your help and advice it has been appreciated.

---

### Post by spiky001 on 2010-06-06
maybe try win 7 forum see if they can shed some light on it

---

### Post by mick463 on 2010-06-06
Hi spike i found a work around or maybe i am just a bit of a noob but i was trying to get into the windows folders buy going to places then network and then clicking on the windows icon.
What i did in the end was to go to connect to server then selected windows share then typed in my ip address and the shares came up no probs.So i will do it that way from now on. On another note i have a problem with ssh between 2 ubuntu computers now but that is for another thread so thank you for all of your efforts i really appreciate it a lot .

---

