---
title: "problem connecting with vnc to ubuntu"
date: 2009-07-18
forum: General Help
---

### Post by Mia_tech on 2009-07-18
I have enabled Remote Desktop on my Ubuntu box, but I'm not able to connect with ultravnc from my vista machine; however, I connect from my 2k3 box, it connect no problem. I'm suspecting something with my vista machine, maybe this has happened to anyone. Another thing, I'm able to connect with tightvnc from any machine... does tightvnc works with Remote Desktop in Ubuntu, if I'm not mistaken when you enable Remote Desktop, basically you're installing Vino which is the default vnc for gnome

any help appreciated

---

### Post by philcamlin on 2009-07-18
use the remote deskop thing in vista i think 

thats what peopele use at my school

---

### Post by Mia_tech on 2009-07-18
> **philcamlin said:**
> use the remote deskop thing in vista i think 

thats what peopele use at my school


man rdp and vnc are two different protocols, the speak on different ports vnc: 5900 and rdp: 3389

---

### Post by doas777 on 2009-07-18
the tightvnc should work just fine. the ubuntu "remote desktop" service is called "vino", and the default client is the tight version for linux (xtightvncviewer).  do you require a password for access? that has caused problems for me before (didn't work till intrepid or jaunty). there are also problems when the ubuntu host is running visual effects, that cause the window to freeze and never redraw. the recomended is to login via ssh and run 'metacity --replace' before connecting, but it sounds like you can't connect at all. what encoding and encryption are you using, and if you download realvncviewer, does it do the same thing?

---

### Post by Mia_tech on 2009-07-18
> **doas777 said:**
> the tightvnc should work just fine. the ubuntu "remote desktop" service is called "vino", and the default client is the tight version for linux (xtightvncviewer).  do you require a password for access?

no I disabled the password because I thought that was the problem, but still I'm not able to connect with tightvnc windows version; however, I can connect with ultravnc no problem

---

### Post by doas777 on 2009-07-18
have you tried playing wiht teh encoding types and whatnot? is there any error message?

---

### Post by Mia_tech on 2009-07-18
> **doas777 said:**
> have you tried playing wiht teh encoding types and whatnot? is there any error message?

Yes "Failed to connect to server"

---

### Post by Pritamsng on 2009-07-24
Hi, All,
Actually i m trying to configure **[COLOR=#ff0000]vnc[/COLOR]** **[COLOR=#ff0000]server[/COLOR]**(multi user) on **[COLOR=#ff0000]ubuntu[/COLOR]**.. its working fine but one problem i m getting that is from the client system when i m connect to **[COLOR=#ff0000]server[/COLOR]** through **[COLOR=#ff0000]vnc[/COLOR]** i cant able to get the g[FONT=Times New Roman][SIZE=3]raphic.. a screen shoot i m attetching here. please any one can solve my prob then replay...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][IMG]http://i620.photobucket.com/albums/tt288/pritamsng/vncprob.jpg[/IMG] [/SIZE][/FONT]

---

### Post by Mia_tech on 2009-07-24
well, my problem was that using tightvnc you don't need to specify the port to which you are connecting like: 192.168.1.10:5900; therefore, giving me a connection error, like in the case of ultravnc the above scenario will work but not with tightvnc

---

### Post by Pritamsng on 2010-02-10
> **Pritamsng said:**
> Hi, All,
Actually i m trying to configure **[COLOR=#ff0000]vnc[/COLOR]** **[COLOR=#ff0000]server[/COLOR]**(multi user) on **[COLOR=#ff0000]ubuntu[/COLOR]**.. its working fine but one problem i m getting that is from the client system when i m connect to **[COLOR=#ff0000]server[/COLOR]** through **[COLOR=#ff0000]vnc[/COLOR]** i cant able to get the g[FONT=Times New Roman][SIZE=3]raphic.. a screen shoot i m attetching here. please any one can solve my prob then replay...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][IMG]http://i620.photobucket.com/albums/tt288/pritamsng/vncprob.jpg[/IMG] [/SIZE][/FONT]
He i got the solution,
just write "sh" in place of "exec"

---

