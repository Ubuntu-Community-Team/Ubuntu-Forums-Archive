---
title: "remote destop"
date: 2010-12-16
forum: General Help
---

### Post by sureshk89 on 2010-12-16
Hi
Can anyone tell me how to make my linux system as remote desktop(for windows). what should i do in linux .
I am new to linux help me please.
I need to access linux system from other computers.

Thanks and Regards
Suresh

---

### Post by mendhak on 2010-12-16
The simplest way is to enable VNC. You can do this from the System menu and it exposes the VNC server on port 5900.  System > Preferences > Remote Desktop > allow other users to view your desktop. It has other security options below it.

You'd then have to install a VNC client (such as tight vnc) on the Windows machine and in there specify the Linux box and you can connect.  

However, I don't think a lot of people will recommend that to you as it has security implications and inconvenience implications - in order to remote desktop to the Linux box, you need to be logged in to the Linux box.  Also, depending on what you selected you may need to actually click 'ok' on the linux box when connecting from the windows box.

If this isn't a problem to you then go for it - you may end up unchecking the "ask for your confirmation" checkbox.  

Look here: [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

It was a problem for me, so I used x11vnc.  If you start x11vnc or have x11vnc running on machine startup then you can use TightVNC, connect to it and you don't have to be logged in.

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

### Post by sureshk89 on 2010-12-16
Thanks guys.Will do that.
Regards 
suresh

---

### Post by sureshk89 on 2010-12-16
Hi
I enabled remote option in my linux. I also download vncviewer in linux and installed it.How to access that drom windows machine. I tried installing vnc and started connecting,""unable to connect to hosts""

Thanks
suresh

---

### Post by mendhak on 2010-12-17
What host and port did you use to connect to the Linux box?

Was VNC running on the Linux box? Did you use 5900? Which VNC server are you running now?

---

