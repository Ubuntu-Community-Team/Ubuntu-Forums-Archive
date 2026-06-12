---
title: "Ubuntu and Microsoft"
date: 2010-01-10
forum: General Help
---

### Post by ashvindora on 2010-01-10
Hello guys..I'm ashvin from Mauritius and new to linux..I have downloaded ubuntu desktop 9.6 and has already installed it..
I would like to ask if my ubuntu desktop can work on a windows server environment..

For example:
I have a windows server 2003 and i want the ubuntu desktop which i have installed to be a client of this server..Is this possible, i mean will it work? Or i need to installed the ubuntu server itself..

Thanks to let me know..

regards
ashvin

---

### Post by Brandon Williams on 2010-01-10
Please provide more detail about exactly what you're trying to do. There are lots of different ways you might expect the machine to interact with the server, and we need to know specifically what you're trying to do in order to answer your question.

In general, there are ways for linux clients to access file shares, e-mail, etc. from a Windows server. There are also ways to use the windows server for user login authentication.

---

### Post by steveneddy on 2010-01-10
Ubuntu desktop is not an application.

Ubuntu is an operating system.

Why do you need a GUI for a server?

Windows and Ubuntu are two completely different animals. You might as well ask if you can install Mac desktop on your Windows machine.

---

### Post by jusitndm on 2010-01-10
windows and ubuntu both can speak http ftp telnet and so on so i'd say they will work together although an ubuntu server would probably be better.

---

### Post by ashvindora on 2010-01-11
Thanks for the reply...i have installed a windows 2003 server, already configured active directory (domain controller)..As client i have installed ubuntu desktop 9.10 and want to know if i can add this client on my windows 2003 server to share files.
I mean, can a ubuntu client share files on a 2003 server..As u have told me before, it is possible to do it, even mail etc etc..But i would like to know if it's really reliable..
u know i'm only working on microsoft system since..but as things changes now, companies here want to shift from linux system cause ms licenses are very cheap..

---

### Post by ad_267 on 2010-01-11
Yes definitely. The samba client is used in Linux to access Windows shares and should be installed by default. Samba can also be used to share files with Windows computers from Linux. You should be able to access your Windows shares from Places -> Network.

---

