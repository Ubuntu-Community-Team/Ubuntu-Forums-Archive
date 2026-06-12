---
title: "upgrade to 10.04 now POP3/IMAP broken"
date: 2010-05-22
forum: General Help
---

### Post by seanmccaskey on 2010-05-22
By some matter of luck and perseverance I was able to get 9.4 up and running as a server with email (pop3 and imap), web, ftp and telnet. Took me a while, but it worked.
 
Yesterday I ran the upgrade to 10.04 and now my IMAP and POP3 are not working. SMTP still works. I get connection refused from Outlook on a client machine and error 111 from Squirrelmail on the web side.
 
I really don't even know where to start. The mail is coming into the system, I just can't access it. I am able to send mail out of the server.
 
Where should I start? I noticed dovecot seems to not be running. Get errors about seive... but I can;t seem to correct that or even know if that is the real issue. 
 
Installed courier with no success... AARG!!!

---

### Post by seanmccaskey on 2010-05-22
Solved this one myself. Had to remove and reinstall dovecot and reconfigure. Life is good once again.
 
sudo apt-get autoremove --purge dovecot-common dovecot-pop3d dovecot-imapd
 
sudo apt-get update
 
sudo apt-get install dovecot-imapd dovecot-pop3d
 
 
 
-SeanM

---

### Post by dcstar on 2010-05-23
> **seanmccaskey said:**
> **Solved** this one myself.


See my sig.

---

