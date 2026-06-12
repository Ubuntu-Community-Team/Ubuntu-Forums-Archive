---
title: "FTP server installation and configuration"
date: 2011-04-07
forum: General Help
---

### Post by suresh_vandiyur on 2011-04-07
Hi All,

I need to configure FTP server on the Ubuntu Desktop Edition 10.10. Is it possible to configure the FTP Server in ubuntu desktop 10.10. please tell me how to configure the FTP server

Thank you,

---

### Post by Fire_Chief on 2011-04-07
Here's a good place to start.

[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")

Cheers!

---

### Post by suresh_vandiyur on 2011-04-08
> **Fire_Chief said:**
> Here's a good place to start.

[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")

Cheers! 

I did not put the public ip. i try connecting through lan i get this is error.

500 OOPS: cannot change directory:/home/notionink
Error:	Critical error
Error:	Could not connect to server
 How to fix this 

Thank you,

regards,
Suresh

---

### Post by suresh_vandiyur on 2011-04-08
> **Fire_Chief said:**
> Here's a good place to start.

[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")

Cheers!

Hi,

I have installed and configured how to the FTP server is working or not.please help me

Thank you,

Regards,
Suresh

---

### Post by uncle-c on 2011-04-08
Hi Suresh,
Have you checked if your firewall is allowing ftp traffic ?

---

### Post by suresh_vandiyur on 2011-04-08
> **uncle-c said:**
> Hi Suresh,
Have you checked if your firewall is allowing ftp traffic ?

Hi,

#netstat -a | grep ftptcp        0      0 *:ftp                   *:*                     LISTEN

i got this output means FTP server is running. i want know FTP server is working in LAN or not

Thank you,

Regards,
Suresh

---

### Post by uncle-c on 2011-04-08
Can you ping to your ftp server from a computer on your LAN ? Is you FTP server "firewalled" so as to block access from anywhere on the LAN ?

---

### Post by suresh_vandiyur on 2011-04-09
> **uncle-c said:**
> Can you ping to your ftp server from a computer on your LAN ? Is you FTP server "firewalled" so as to block access from anywhere on the LAN ?

Hi,

Thank your reponse. Right now its working on lan. i want one more help. i want create the FTP users only that users can not be login in system and the FTP users only download files and upload files.. they dont delete any file. how to setup above things. please help me

Thank you,

regards
suresh

---

