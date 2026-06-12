---
title: "Get external emails from another server via postfix"
date: 2009-11-30
forum: General Help
---

### Post by snake_eyes on 2009-11-30
Hello,

let's say I have a postfix server installed at my office and I have the user [email]testmail@mydomain.com[/email], the mydomain.com is hosted at USA, I wanna any message sent to [email]testmail@mydomain.com[/email] to be received to the main hosting company which is in USA, and I wanna get my email via the postfix that is exist in the office, by setting up the postfix to connect to the mydomain.com at USA automatically and check if there is an emails in the mailbox to get them and download in the testmail account which is the postfix server at my office.

In this case I will get my email from the server that it's in my office instead of the connection to the main server

Any help about this matter please???

Cheers,

---

### Post by snake_eyes on 2009-11-30
please note that my office is outside USA, so much better to get the emails from the local server instead all the users make connections to the main server

---

### Post by mihamil on 2009-11-30
You can use fetchmail to download the mail from the main server at your hosting company and forward it to a mailbox on your postfix server.  It can be set up to run as daemon and update at defined time intervals.  I do it to get my school email and forward it to my email server every 120 seconds.

---

### Post by snake_eyes on 2009-12-01
> **mihamil said:**
> You can use fetchmail to download the mail from the main server at your hosting company and forward it to a mailbox on your postfix server.  It can be set up to run as daemon and update at defined time intervals.  I do it to get my school email and forward it to my email server every 120 seconds.

great, this what I need, Is there a small document step by step to do this? or is there any commands can I start with them?

Cheers,

---

### Post by snake_eyes on 2009-12-01
I wanna ask also if I setup the fetchmail to retrieving mails from another server and forward them to the postfix, when I get the email from the postfix server instead of the main server it will save all the variable such as sender name, sender email, CC: and TO address...

Cheers,

---

### Post by mihamil on 2009-12-02
It will save all information for the email.  

I will outline how mine is configured and hopefully that will help you.

In my home folder on the postfix server I have a file called .fetchmailrc

Here are the contents

###################################
poll school.mail.server
	with proto IMAP
	username MyUserName pass MyPassword is [email]theaccount@mymailserver.com[/email]
;
###################################

This basically starts by telling fetchmail what server and what protocol to use.  Then gives the username, password, and the local account to forward it to.

Then I start fetchmail as a daemon to poll the server every 120 seconds with this command

fetchmail -d 120


This just tell fetchmail daemon to start and poll every 120 seconds.  By default this command will check the users home folder for a .fetchmailrc file and use it to define the polls.  You could set this as a startup job in your crontab.  

Note:  You can set up multiple email accounts using this in the same .fetchmailrc file so you could have several email accounts set up.  Also this WILL remove email from the server you are downloading it from.

---

### Post by mihamil on 2009-12-02
Forgot to mention.  Install fetchmail using
sudo apt-get install fetchmail

then run

man fetchmail

This will give you a rundown of how to use it.

---

