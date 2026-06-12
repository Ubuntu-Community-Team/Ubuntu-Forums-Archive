---
title: "Remote Desktop to Windows Domain"
date: 2009-11-18
forum: General Help
---

### Post by Abadon125 on 2009-11-18
I have a Windows Server 2008 computer that is a domain controller, and my laptop wit Ubuntu is not on that domain.  What is the best way to remote desktop into it?  (I would prefer to not have to install a VNC Server on my Server, using the Windows built in tool would be best)  The screen shot shows the error I get when I try to log in
-Thanks!

---

### Post by Abadon125 on 2009-11-22
bump

---

### Post by m3741 on 2009-11-22
That's... interesting. I have the same thing as you, Server 2008 and Karmic on my laptop and I use the Terminal Server Client that came with Ubuntu. Are you able to TS into the server from a Windows box?

---

### Post by Abadon125 on 2009-11-22
Yea with no problem.  Maybe I am not using all the right information.  
I use the IP address instead of the hostname, just to make sure.  Then I am using the Administrator account because I know for sure it works, and the password, and I use RDPv5 and the correct domain name.  anything else I need to fill in?

---

### Post by m3741 on 2009-11-22
Have you changed any settings in the Terminal Services snap-in on the server? I know if you crank the encryption level and such up a little high the Ubuntu client will have problems.

EDIT:
[This]("http://ubuntuforums.org/showthread.php?p=7806861") thread has some info pretty much along the lines of what I'm talking about.

---

### Post by Abadon125 on 2009-11-22
Haha, i actually had just thought about that.  Turns out I had changed it to only allowed computers with Network Level Authentication (or something like that).  If you turn it down so it just uses the regular encryption level then it works perfect.  :)

Thanks for your help!

---

