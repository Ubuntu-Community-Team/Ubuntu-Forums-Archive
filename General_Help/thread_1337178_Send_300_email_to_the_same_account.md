---
title: "Send 300 email to the same account"
date: 2009-11-25
forum: General Help
---

### Post by any.linux12 on 2009-11-25
Hi!

I would like to send 300 email to the same account, but don't get me wrong because I don't want to mail bomb anyone :D I just need to overload my new zimbra server to test the backup time.

thanks

---

### Post by any.linux12 on 2009-11-26
bump

---

### Post by glepore70 on 2009-11-26
How about using the command line mail program wrapped in a shell script loop?
[http://www.simplehelp.net/2008/12/01/how-to-send-email-from-the-linux-command-line/](http://www.simplehelp.net/2008/12/01/how-to-send-email-from-the-linux-command-line/)

---

### Post by glepore70 on 2009-11-26
OK, I've worked this out, the below script will send 300 emails to the email specified.  You will have to install mail or mutt to make this work.  If it only sends one message per minute, check /var/log/syslog for messages about a fully qualified domain name. The fix for the one email per minute is to edit the /etc/hosts and add entries for your local host name (ask back for more info).
put the script in a file and chmod it to executable, then run it.  It should send the messages almost instantaneously.


[HTML]for ((i=0; i<=300; i++))
do
echo "message $i" | mutt -s "subject $i" your@email.com
done[/HTML]

---

