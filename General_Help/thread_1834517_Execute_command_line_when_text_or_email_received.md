---
title: "Execute command line when text or email received"
date: 2011-08-27
forum: General Help
---

### Post by hwttdz on 2011-08-27
I'd like to set up execute a command line command when a text or email (preferably one for each) is received.  I use gmail and thunderbird for mail and verizon, google voice and an android handset for texts.  Any ideas? Thanks.

---

### Post by TeoBigusGeekus on 2011-08-27
A cron job that checks whether you have mail (with fetchmail for example) and, if yes, executes the command line.

---

### Post by hwttdz on 2011-08-27
Wouldn't I have to use pop as opposed to imap in that case?  

I think a possibly working solution is to 

"grep -a -c -i person_for_whom_I_want_the_ringer ~/.mozilla-thunderbird/ACCOUNTSTRING/global-messages-db.sqlite"

and watch for it to increment.  I'm putting it in a little perl script in a loop and waiting 1 minute or so between checks.

---

### Post by TeoBigusGeekus on 2011-08-27
Install fetchmail
```
sudo apt-get install fetchmail
```
Create a file called .fetchmailrc in your home folder and put this inside
```
set postmaster "yourpcusername"
poll pop.gmail.com with proto POP3 and options no dns
user 'gmailusername@gmail.com' there with password 'gmailpassword' is 'yourpcusername' here  options ssl
```
Then
```
fetchmail  -k --uidl|sed 's/for/\n/g'|head -n 1
```
will give 
```
fetchmail: No mail
```
if you have no mail (dah) and
```
1 message
```
if you have, well, 1 message, leaving the email at the server (I use this on my conky, so it's tested)
You can add an if (or case) command and then wrap it up in a cron job and you're done.

---

### Post by hwttdz on 2011-08-27
I'm not seeing how I can check who the mail is from in that case?

---

### Post by TeoBigusGeekus on 2011-08-27
No, you can't do this with fetchmail.
Sorry, I thought you just wanted a notification upon receiving an email.

---

### Post by hwttdz on 2011-08-27
Sorry, my fault for not being specific enough.  Using the admittedly inelegant method I outline I can set a different "ringtone" for different people.  And because I can have google voice forward to my email, I can get an alarm on my computer when someone calls/sms/emails.

---

### Post by dcstar on 2011-08-27
> **hwttdz said:**
> I'd like to set up execute a command line command when a text or email (preferably one for each) is received.  I use gmail and thunderbird for mail and verizon, google voice and an android handset for texts.  Any ideas? Thanks.

Pity you don't use evolution, you can set up filter rules that can execute commands.

---

