---
title: "Atheros driver for Linux?"
date: 2011-05-22
forum: General Help
---

### Post by Ronkelaura on 2011-05-22
I got a laptop (Packard-Bell from 2010) with a broken harddrive. It´s a mini laptop without cd or dvd drive.  

I downloaded DamnSmall Linux in order to start from USB port ,to try to access the web until I get hold of a new hard drive - Then I probably wanna install Ubuntu or Fedora, because the internal Windows recovery option probably vanished with the broken Hdrive . 

Well, I got into the pc thru starting up DSLx from USB. However, the OS doesn´t find the built-in WLAN hardware.  

Apparently I need a driver for Atheros hardware that works on DSLx. 

I looked thru some webpages but it seems to me as if there are loads of Atheros drivers for Ubuntu, but not for DSLx? Or can I use the Ubuntu driver?  

Does anybody have an idea about how to solve the problem?

Thanks for any help.

---

### Post by Joe of loath on 2011-05-22
DSL uses the 2.4.x kernel. That means that basically, wireless is a no-no unless you fancy performing major hackage.

Puppy Linux performs a similar job to DSL, but includes way more wifi drivers. Maybe try that?

---

### Post by coldraven on 2011-05-22
A long time ago I installed Ubuntu 8.04 on an ancient Dell laptop (333MHz!). I stuck an Atheros card in it and with the madwifi driver it worked fine.

---

### Post by Joe of loath on 2011-05-22
8.04 used a 2.6 kernel, though ;)

---

