---
title: "Where did this Nginx come from?"
date: 2012-06-23
forum: General Help
---

### Post by flogged_horse on 2012-06-23
I'm on a vertical rocket ride "learning all about Ubuntu and Linux", my head is spinning!

Any direction would be appreciated.

_The story_
Total beginner.
Created a home / business 64 bit server
Became a file server using Samba - serving windows 7 machines
Became a backup server to a internal separate mounted drive
Became a LAMP server - got the "It Works" page (/var/www) still there
Then we bang on a gigabit switch (power fed from the ATX)
Played and failed at turning it into a Fax server
Became a printer server - using Cups
Played and failed to print pdfs from windows (think this is a software development issue)
Played and failed to create a IMAP server (fetchmail postfix dovecot)
Got a Static IP via dyndns.org "using  inadyn"
Became a OpenERP server -  works!

BUT now I get a "Welcome to nginx!" page! when I browse to the server Ip or using the static IP link

_The Questions_
1) Does anyone know whats 'redirecting / controlling' the redirection? 
2) Where did Nginx come from? (My money is either Dovecot or Inadyn)


Many thanks

Cameron

Hoping to use the server as a PHP testing ground.
Hoping to use the File server via VPN 
Hoping to become a backup server to a windows machine
Hoping to use the server as a media streaming server
Hoping to us the server as a CCTV server
Then I'll get it to water my turnips whilst on holiday! (you laugh, but I have a plan!)

Not bad for a £50, 200 Watt, second hand PC!
It will probably end in Puff of smoke!

---

### Post by flogged_horse on 2012-06-23
Thanks for looking - have sorted the problem

It turned out I installed nginx (engine X) as part of an attempted SSL connection for OpenERP.

Have removed it and re-installed apache.

No longer get the Nginx 

Cheers

---

