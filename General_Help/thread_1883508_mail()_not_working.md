---
title: "mail() not working"
date: 2011-11-19
forum: General Help
---

### Post by sajansen on 2011-11-19
hey
 
i have ubuntu with: apache2 php5 mysql-server phpmyadmin openssh-server postfix
installed and set: SMTP = mail.home.nl (working) SMTP_port= 25 sendmail_from <mailadres> sendmail_path = postfix
 
i use this script to test:
<?php
if(mail('<mailadres>','test subject','test message')){
echo('OK');
}
else{
echo('Not OK');
}
?>
 
In a virtual pc with ubuntu and above settings i get status "OK" but i dont get the e-mail
*edit:*
in teh logfile it says bounce(unknown user) and then example.user when the full e-mail adres is [EMAIL="example.user@example.com"]example.user@example.com[/EMAIL]... what is going whrong here?
 
and with a running surver with ( i think) the same settings i get "Not Ok"
 
anyone a idea what the problem is?
 
thanks

---

