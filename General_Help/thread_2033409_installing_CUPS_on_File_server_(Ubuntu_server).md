---
title: "installing CUPS on File server (Ubuntu server)"
date: 2012-07-26
forum: General Help
---

### Post by Jorel on 2012-07-26
Hi guys,,

I got an old printer, Dell 1100 and Epson LQ 300 II, and i'm wondering, is there any specific way to install CUPS into my Ubuntu server 12.04? because most tuts are done via GUI,,, thats why i'm having hard time installing those old printers..

Thanks in advance...

---

### Post by Cheesehead on 2012-07-26
To install CUPS: sudo apt-get install cups

Install the printers using CUPS' web-based GUI: http://<ipaddr-of-server>:631 . You need to know the ip address of the server, and the server's firewall (if any) must leave port 631 open for the web connection and subsequent printing connections.

You can also install printers using the command line (via SSH, for example) using the [FONT="Courier New"]lpadmin[/FONT] command. See [FONT="Courier New"]apropos cups[/FONT] for the full list of cups commands.

Tip: Make sure the server's CUPS shares the printer. And make sure that your local CUPS looks for shared printers. Those are two common mistakes when setting up networked CUPS printers.

---

### Post by Jorel on 2012-07-28
> **Cheesehead said:**
> Tip: Make sure the server's CUPS shares the printer. And make sure that your local CUPS looks for shared printers. Those are two common mistakes when setting up networked CUPS printers.

is it by editing the samba.conf [printing]? 

Thanks Cheesehead

---

### Post by Jorel on 2012-07-30
sorry guys,, i cant really pick up what i supposed to do next,, i installed the CUPS in my headless and now i dont know what to do next,, i tried http//<ipadd>:631 and :63 and even with /admin, but still no good,, and in my /etc/cups/cupsd.conf, i cannot follow some instructions that im reading,,, im really lost..

hope you can help me guys,,

Thanks in advance.

---

### Post by Jorel on 2012-07-31
hi guys,,

in my search for an answer, i found this:

[http://www.techrepublic.com/article/control-printers-in-linux-from-the-command-line/5055067](http://www.techrepublic.com/article/control-printers-in-linux-from-the-command-line/5055067)

hope someone can testify that this link can help me later upon installing my printer because its way back from 2003... hope it give me a kick-start with my CUPS concerns..


thanks guys...

---

### Post by Jorel on 2012-08-01
help guys,,

i can't find my printer using lpstat -t, all i can see is:

no system default destination
lpstat: No destinations added.

thanks in advance..

---

### Post by Jorel on 2012-09-18
Hi guys,

I figured it out after a weeks of digesting headache,, hope this can help others too..

1st i edit
# /etc/cups/cupsd.conf
(checking the following if they are ok)

#Administrator user group
SystemGroup lpadmin

#Only listen for connections from the local machine
# listen localhost:631
    listen (ip-add):631
    listen /var/run/cups/cupsd.sock

#Show shared printers on the local network
  Browsing On
  Browse Allow all
  Browse Order allow,deny
  Browse Addess @LOCAL

#Default authentication type, when authentication is required...
  Default Auth Type Basic

#Restrict access to the server
  <Location/>
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  </Location>

#Restrict access to the admin pages...
  <Local /admin>
  Order allow,deny
  Allow @LOCAL
  </Location>

#Restrict access to configuration files
  <Location /admin/conf>
  Auth Type Default
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL
  </Location>

then i save, exit and restart the conf
# /etc/init.d/cupsd restart

then i go to [http://(ip-add):631/admin](http://(ip-add):631/admin)
-i go to Administrator Tab
-click Add printers (then follow instructions)
-set the Server settings with couple of checked boxes 
- add classes (choose an easy name to remember)

then on a windows machine:
-Device and printers
-choose Find printer by name TCP/IP address
- then type http://(ip-add):631/printers/"class name"-(its the one that you create on the classes)

then voilà.... i got connected and got the printer running... hope this one help....

---

