---
title: "sending a SSMTP from a script doesn't work"
date: 2011-12-06
forum: General Help
---

### Post by ski20 on 2011-12-06
Hi All,

Have a script running from crontab to check if a certain Process is still running!, in the case of the Process NOT running a Entry is made in a log i have created and a Email sent using ssmtp. The problem is in the event of that happening the script makes the log entry and calls the line with the ssmtp ... BUT no Email ever arrives at its destination. Although when I run the script by hand as root the email is recieved at destination. In the system mail.log i can see a diffence in what happens when i start the script and when "crontab" strarts the script. This log entry is made when "crontab" starts the script (no email recieved):

Dec  5 17:50:06 ubuntu1 sSMTP[8905]: Sent mail for [EMAIL="root@googlemail.com"]root@googlemail.com[/EMAIL] (221 2.0.0 closing connection em4sm28858193wbb.20) uid=0 username=root outbytes=641

and this when start the script by hand from the shell as root (mail recieved at dest. )):

Dec  5 17:51:32 ubuntu1 sSMTP[8917]: Sent mail for [EMAIL="myServerEmial.address@gmx.net"]myServerEmial.address@gmx.net[/EMAIL] (221 2.0.0 closing connection hb10sm5704338wib.16) uid=0 username=root outbytes=442

Here the line from my script:

cat email.txt | ssmtp -v [EMAIL="MyIphone.EmailAddress@gmx.de"]MyIphone.EmailAddress@gmx.de[/EMAIL]  >> /usr/local/bin/inadyn.log & 




email.txt
#########

From: [EMAIL="myServerEmial.address@gmx.net"]myServerEmial.address@gmx.net[/EMAIL]
To: [EMAIL="MyIphone.EmailAddress@gmx.de"]MyIphone.EmailAddress@gmx.de[/EMAIL]
Subject: Server Report

The Inadyn client Process has packed up !!!



What do I need to to change so that when Crontab calls the script that a Email is sent and recieved as when I call the same script by hand from the shell ??

Thanks for your hepl

---

