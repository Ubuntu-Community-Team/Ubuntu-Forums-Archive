---
title: "How to run an oracle app through a network"
date: 2011-03-31
forum: General Help
---

### Post by MepisReign on 2011-03-31
This one is a little difficult
I have installed:
- Wine (configured correctly)
- Oracle (using wine)

Now that I have the application installed I need to run an exe file, in order for the software to run correctly it need to authenticate through a Windows Network. It is a sales application.

In windows the solution would be to right click on the exe file and type the route for the application to authenticate
On another system that is running windows the path is like this:
C:\orant\BIN\ifrun60.exe S:\mnu\fmer0000.fmx @orcl

On the path above S will be the server, the way that I see it on Ubuntu is by the IP 192.168.10.9, it is mounted and visible from the Ubuntu box.
I have placed a shortcut on my Desktop (Ubuntu) of the ifrun60.exe now what I need is that everytime I click on that shortcut (ifrun60.exe) to link the fmer0000.fmx over the network and run on Firefox, at the end the app will run as html.

I hope this is clear enough and somebody can help me on this matter

Kind Regards,

MepisReign

---

### Post by nsankar on 2011-08-01
Thanks buddy... It really worked for me too...
I was trying in different method (by using WINE) and Failed..... but, you method worked nice....

---

