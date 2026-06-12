---
title: "Email forwarding and redirection question"
date: 2006-02-03
forum: General Help
---

### Post by gt9228a on 2006-02-03
I am looking for ideas to set up a mail server/daemon using ubuntu that will fetch email from hotmail/yahoo etc.. and redirect it keeping the original from: address and forward to another email address.  
   Currently, I have a program on Win XP, mailforward for windows from SSPI software, that runs in the background, periodically (Q10 minutes)  checks Hotmail/yahoo or POP sites for new mail, and will redirect them to my forwarding address for the domain address I use as my primary email address.  It maintains the original From: address and sends the mail using my ISP's SMTP server. 

Now I now that programs such as freepop's, etc can interface with hotmail and download new mail using Ubuntu, but i have not had much success finding information on setting up the mail server to redirect email keeping the original from: Address.  Has anyone used this sort of set-up or have any ideas on how to proceed?  

Thanks for any help.

---

### Post by dcstar on 2006-02-04
[QUOTE=gt9228a]I am looking for ideas to set up a mail server/daemon using ubuntu that will fetch email from hotmail/yahoo etc.. and redirect it keeping the original from: address and forward to another email address.  
   Currently, I have a program on Win XP, mailforward for windows from SSPI software, that runs in the background, periodically (Q10 minutes)  checks Hotmail/yahoo or POP sites for new mail, and will redirect them to my forwarding address for the domain address I use as my primary email address.  It maintains the original From: address and sends the mail using my ISP's SMTP server. 

Now I now that programs such as freepop's, etc can interface with hotmail and download new mail using Ubuntu, but i have not had much success finding information on setting up the mail server to redirect email keeping the original from: Address.  Has anyone used this sort of set-up or have any ideas on how to proceed?  

Thanks for any help.[/QUOTE]
This may help:

[http://ubuntuforums.org/showthread.php?t=66687](http://ubuntuforums.org/showthread.php?t=66687)
[http://ubuntuforums.org/showthread.php?t=7321](http://ubuntuforums.org/showthread.php?t=7321)

---

### Post by gt9228a on 2006-03-08
Still searching for some help with the issue I originally posted.  I am looking to somehow forward messages with the original intact headers.  Ive googled and googled with no luck on how to set this up in linux.  

The set up is this - Someone sends an email to my (for example) [email]myaccount@yahoo.com[/email].  The message is retrieved to my home unix server through the freepops(for example) interface and the server will forward the message, with original from: headers intact, to my main account, [email]myaccount@maindomain.com[/email], which is hosted on a remote computer.  Any ideas?  

Also, I did find a program called versaforward (versaforward.com) that seems to do what I need.  Has anyone tried this program on ubuntu?

---

