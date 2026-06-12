---
title: "Can't send mail from Ubuntu Server"
date: 2011-05-25
forum: General Help
---

### Post by gordongoldin on 2011-05-25
[FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black]I installed mailutils, then mutt.
[FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=black]mail (GNU Mailutils 2.1)
 Mutt 1.5.20 (2009-06-14)[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
   
   After installing mailutils - the recomendation was to shut down the listener with the 2 commands listed below.
   But I don't think that did anything, because before I did that, I tried to send an email - didn't go.
   
    sudo apt-get install mailutils
    mail -s "Brewit Test" [EMAIL="gordongoldin@aim.com"]gordongoldin@aim.com[/EMAIL] 
    /etc/init.d/exim4 stop
   update-rc.d -f exim4 remove               !!! quit at line 57 -   NOTE: I didn't use sudo
   
   sudo apt-get install mutt
   
    
           I saw that mail without a proper REPLY-TO will get sieved out.  So I tried sending mail with reply-to:
  mail -s "getting anything?" -r [EMAIL="gordongoldin@aim.com"]myemail@aim.com[/EMAIL] [EMAIL="gordonconnect@gmail.com"]myemail@gmail.com[/EMAIL] < /home/myid/Email/Daily_Report.txt

telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 brewit ESMTP Postfix (Ubuntu)

 Any thoughts?
 
    
          Gordon
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

