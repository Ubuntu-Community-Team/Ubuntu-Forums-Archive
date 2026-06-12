---
title: "Postfix (Nagios) connection time out gmail"
date: 2010-03-30
forum: General Help
---

### Post by ansabhailte on 2010-03-30
Hello,

I am running Nagios3 (compiled from source) on an Ubuntu 9.10 workstation. I have installed postfix and mailx, and have created a certificate. I am trying to forward Nagios notifications to my gmail email address. however, when i run postqueue -p after encountering a situation that sends out notifications, the outcome is:

jcbcomputercare@jcbcomputercare:~$ postqueue -p
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
6B9E55900A2      545 Tue Mar 30 15:44:11  [email]nagios@smtp.gmail.com[/email]
(connect to alt4.gmail-smtp-in.l.google.com[209.85.219.50]:25: Connection timed out)
                                         [email]ansabhailte@gmail.com[/email]

261F45900B0      570 Tue Mar 30 15:49:38  [email]nagios@smtp.gmail.com[/email]
(connect to alt4.gmail-smtp-in.l.google.com[209.85.219.6]:25: Connection timed out)
                                         [email]ansabhailte@gmail.com[/email]

-- 1 Kbytes in 2 Requests.

i added the email address in my contacts.cfg file. I cant figure out why the heck they wont go through. I had set the postfix portion up using the instructions here:  [http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)

thanks in advance :)

---

