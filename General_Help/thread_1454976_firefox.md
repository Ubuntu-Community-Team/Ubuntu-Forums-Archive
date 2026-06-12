---
title: "firefox"
date: 2010-04-15
forum: General Help
---

### Post by cragtom on 2010-04-15
Please help I have vista and linux through the wubi site and I cannot use the internet function all of a sudden , I have run the tests and all is well but when I try to load firefox all I get is the rotating circle .
The internet is fine as I am talking through vista( note sometimes I load vista and at others use ubuntu , especially like the O,o,s function). I DO NOT WANT ONLY INTERNET IN LINUX BUT IN VISTA AS WELL .

---

### Post by ene_dene on 2010-04-15
I'm not sure I understand correctly. So I'll try to answer with following assumptions:
1. Internet works well in Windows Vista
2. Internet works in Ubuntu as well, but you can't start firefox

Let's try to reinstall firefox in Ubuntu. Don't start firefox at the start of Ubuntu.
Go to Applications->Accessories->Terminal. And then write in terminal:
```
sudo aptitude reinstall firefox firefox-3.5
```
It will ask you for your password, put it and press ENTER. After reinstallation is finished try to run it again.

If I got it wrong, maybe someone else will have better luck. Or you can explain your problem more precisely, for it seems that in one part you say that you don't have internet in Vista and in other in Ubuntu.

---

### Post by cragtom on 2010-04-15
thanks for the tip it is firefox will not work in linux sorry for confusing you

---

