---
title: "access a windows machine from linux machine?"
date: 2010-12-16
forum: General Help
---

### Post by behnam.mn on 2010-12-16
Hi every one,
I'm completely new Linux and I've just installed ubuntu 10.10 on my laptop. I need to access remotely to a windows machine from my laptop. does any body know how to do that?
thanks

---

### Post by Wtower on 2010-12-16
You need to enable remote desktop on the windows machine (if my memory serves me well it should be in computer properties). 

Then find out the ip of that machine (ipconfig on cmd or network card properties in network connections).

Last, on Ubuntu desktop, open terminal services client (should be installed by default) and fill in all details.

Regards

---

### Post by karthick87 on 2010-12-16
I personally prefer Team viewer,it's a  computer software package for remote control, desktop sharing, and file  transfer between computers. The software operates with  Microsoft  Windows,Linux based OS & Mac OS X, and is able to function while the  computers are protected by firewalls and NAT proxy....
  **Installing Team viewer:**
  For Ubuntu,you can download teamviewer [here]("http://www.teamviewer.com/download/teamviewer_linux.deb"). Once downloading is completed, you can install it easily by double  clicking the file.After installation you can find team viwer under the  Internet Menu.
  **Open the Team Viwer:**
  Applications -- >>Internet -->> Team Viwer
  [IMG]http://i.imgur.com/eWwZs.png[/IMG]
    Before establishing the remote desktop connection,you must know the  ID and Password of the remote system which is running Team Viwer.After  getting the ID and Password from your partner.Enter the ID and click  connect to partner, with in few seconds it will show a window prompting   for a password.Enter the password which you got from your partner and  click ok.Now you are connected to remote sytem.

---

### Post by HermanAB on 2010-12-16
Howdy,

If you have a proper version of Windows, then it will have Remote Desktop built in.  Activate it ans use rdesktop to connect from Linux.

Otherwise, if you have a crummy version of Windows, then you could use UltraVNC.

---

### Post by mendhak on 2010-12-16
> **behnam.mn said:**
> Hi every one,
I'm completely new Linux and I've just installed ubuntu 10.10 on my laptop. I need to access remotely to a windows machine from my laptop. does any body know how to do that?
thanks
You can use rdesktop (you may already have it installed?).  In terminal

rdesktop 192.168.1.3


You can also go Application > Internet > Terminal Server Client and in the large dialog, choose 'RDP' when connecting to the Windows machine.

---

### Post by behnam.mn on 2010-12-16
Hi everyone,
first of all thank you so very much for your replies.

the remote desktop is already activated on the target machine and I can access the machine from other windows machines but when I was trying to use "remote desktop viewer" in Linux, it failed to connect to it and says "Connection to host HOST NAME was closed"  

also in case of using team viewer, I already have been using this software but the pc that I'm trying to connect to, is a server and the admins do not allow users to install these softwares on it because of security concerns.

But I could connect to the target computer using "Terminal Server Client", so thank you again for you help. but does any of you can tell me why I couldn't connect to it by remote desktop viewer and what does this message that I get from it mean?

Regard

---

### Post by Wtower on 2010-12-16
Excellent. As far as I understand, you can access the windows machine with vinagre (the application that is accessed within the menu as remote desktop viewer) only if a vnc server is installed. For remote desktop you use terminal server client. It is a matter of supported protocols.

Regards

---

### Post by behnam.mn on 2010-12-16
Thank you for your clear answer to my question,
Best,

> **Wtower said:**
> Excellent. As far as I understand, you can access the windows machine with vinagre (the application that is accessed within the menu as remote desktop viewer) only if a vnc server is installed. For remote desktop you use terminal server client. It is a matter of supported protocols.

Regards

---

### Post by Wtower on 2010-12-16
I am very glad indeed. Please do mark the thread as solved!

---

