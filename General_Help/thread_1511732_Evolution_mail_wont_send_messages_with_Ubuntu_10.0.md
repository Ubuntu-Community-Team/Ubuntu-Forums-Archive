---
title: "Evolution mail wont send messages with Ubuntu 10.04"
date: 2010-06-17
forum: General Help
---

### Post by Yagami_ on 2010-06-17
Hey, I'm very much new to using Ubuntu and Evolution mail. I had been using Evolution with no issues though until I installed Ubuntu 10.04 after which I could no longer send outgoing messages. I use a hotmail live account with Evolution. Does anyone have any suggestions to help? I have also just installed Evolution 2.30 from 2.28 to see if that would solve the issue, but it did not.

---

### Post by karthick87 on 2010-06-17
What error did you get while sending the message..

---

### Post by philinux on 2010-06-17
> **Yagami_ said:**
> Hey, I'm very much new to using Ubuntu and Evolution mail. I had been using Evolution with no issues though until I installed Ubuntu 10.04 after which I could no longer send outgoing messages. I use a hotmail live account with Evolution. Does anyone have any suggestions to help? I have also just installed Evolution 2.30 from 2.28 to see if that would solve the issue, but it did not.

These are my settings for hotmail. I've removed my username obviously.

---

### Post by VorDesigns on 2010-07-27
I have the same problem only I can get mail just can't send it; says relay access denied so either the authentication is failing with a bad password which I'm not being prompted for or it isn't bothering to authenticate at all.
Since there's not test setting option (a la Outlook), I'm flummoxed.

I'd like to go Win free but, it's getting hard and I'm usually pretty good a working around buggy software.

Is there a way to run Evolution in debug mode so I can watch what is going on.

---

### Post by Jonners59 on 2010-07-28
> **philinux said:**
> These are my settings for hotmail. I've removed my username obviously.

You may find it's blocked...  I had this years and years ago when I first started using clients on Windows...  I found the answer was to use my (Broadband provider) ISP server settings instead.  I currently use Be There, so the setting is smtp.beusergroup.co.uk

BUT NOT my Hotmail, or Tiscali.it or Tiscali.co.uk or googlemail or gmail SMTP....  none work

Speak to your Broadband provider and get theirs.  I can almost guarantee it will work.

Hope this helps.

---

### Post by VorDesigns on 2010-07-30
Couldn't do without mail; had to go back to WM$ for it.

---

### Post by ruger01 on 2010-07-31
Yagami,

I had issues setting Evolution up as well with Live Mail but is working great now.

This is how mine is set up and working - open evolution, under the "Edit" tab at top of page go to "Preferences" then "Mail Accounts" highlight mail account then click "Edit"

You will then have a tab called "Account Editor" open up. In the Identity tab Account Information type you name. Then in the next section under "Required Information" type your name again and also you live email address.

Go to "Receiving Email" tab - Server Type - **POP**. 
Configuration - Server:** pop3.live.com**
Username: (your Live account email address)
Security: **SSL Encryption**
Authentication Type: **Password, Check for Supported Type**
[B]Tick the remember password box.
[/B]
Got to the Tab for "Sending Email"
Server Type:** SMTP**
Server Configuration - Server: **smtp.live.com**
**Tick server requires authentication box**
Security - Use secure connection: **TLS Encryption**
**Authentication Type: Login              Check for Supported Types**
Username: Your live account email address
[B]Tick box to remember password.
[/B]
I had issues because i did not put TLS Encryption i originally had SSL Encryption which would not work, also make sure when it asks you for you password when you click send/receive mail for the first time - you put in the Live Account password correctly.

Hope this helps.

---

### Post by VorDesigns on 2010-08-02
> **ruger01 said:**
> I had issues because i did not put TLS Encryption i originally had SSL Encryption which would not work, also make sure when it asks you for you password when you click send/receive mail for the first time - you put in the Live Account password correctly.


This is where I know I'm having a problem; I need to get it to challenge credentials again.  Maybe I just need to delete the account and try again.

---

### Post by dcstar on 2010-08-02
> **VorDesigns said:**
> This is where I know I'm having a problem; I need to get it to challenge credentials again.  Maybe I just need to delete the account and try again.

Delete the password entry out of your keyring.

---

### Post by zer010 on 2010-08-07
Evolution used to work great with gmail and hotmail, but then i just did a reinstall of 10.04. Restored my evolution backup. Recieving mail is not a problem. Sending mail is. It  says SMTP connection timed out. Rechecked my settings and everything looks normal. Any Ideas?

---

### Post by HPD2 on 2010-08-07
I had the same issue with it  saying SMTP connection timed out. All my setting for Gmail were correct so I finally just installed Thunderbird, and all works fine.

---

### Post by zer010 on 2010-08-07
I want good ol' Evo back though.

---

### Post by zer010 on 2010-08-07
just got gmail working. had to add the port, duh! lol
[B]smtp.gmail.com:587

now to work on hotmail!

[/B]

---

### Post by zer010 on 2010-08-07
got live working too! hurray! 
again, port 25
and FULL email address for username
MY problem is SOLVED

---

### Post by Old Codger on 2010-08-10
> **ruger01 said:**
> Yagami,

I had issues setting Evolution up as well with Live Mail but is working great now.

This is how mine is set up and working - open evolution, under the "Edit" tab at top of page go to "Preferences" then "Mail Accounts" highlight mail account then click "Edit"

You will then have a tab called "Account Editor" open up. In the Identity tab Account Information type you name. Then in the next section under "Required Information" type your name again and also you live email address.

Go to "Receiving Email" tab - Server Type - **POP**. 
Configuration - Server:** pop3.live.com**
Username: (your Live account email address)
Security: **SSL Encryption**
Authentication Type: **Password, Check for Supported Type**
[B]Tick the remember password box.
[/B]
Got to the Tab for "Sending Email"
Server Type:** SMTP**
Server Configuration - Server: **smtp.live.com**
**Tick server requires authentication box**
Security - Use secure connection: **TLS Encryption**
**Authentication Type: Login              Check for Supported Types**
Username: Your live account email address
[B]Tick box to remember password.
[/B]
I had issues because i did not put TLS Encryption i originally had SSL Encryption which would not work, also make sure when it asks you for you password when you click send/receive mail for the first time - you put in the Live Account password correctly.

Hope this helps.

This helped a lot, but I still can't send. I've got an iMac and a MacBook running OS 10.6, but the MacBook is also running Ubuntu 10.4. Thunderbird works great on the Mac side of both, but I like others here, I can receive e-mail in both Evolution and Thunderbird on Ubuntu, but I can't send. My e-mail is a Yahoo/Verizon deal and even though the settings work fine on the Macs, I still can't send using 10.4. Where do you set up the ports in Evolution?

Thanks in advance,
OC

---

### Post by dcstar on 2010-08-11
> **Old Codger said:**
> 
........
Where do you set up the ports in Evolution?

Thanks in advance,
OC

Exactly where one of the previous posters specified.

[http://ubuntuforums.org/showpost.php?p=9691548&postcount=13](http://ubuntuforums.org/showpost.php?p=9691548&postcount=13)

---

### Post by Z06Gal on 2010-08-14
I used this link and it has worked perfectly:

[http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/)

---

### Post by SbKhaan1 on 2010-11-13
Thank you for the Pics [[COLOR=#D40000]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083"), they helped.

---

### Post by svetiev on 2010-11-20
> **zer010 said:**
> just got gmail working. had to add the port, duh! lol
[B]smtp.gmail.com:587

now to work on hotmail!

[/B]

One more thing, the secure conncetion type should be TLS because it wont work with SSL.

Once I made it TLS and than PLAIN authentication it worked fine.

---

### Post by Lloydstedman on 2011-02-10
Is there any answer to the the 'timed out' issue?

I'm a recent migrator from a mac, using a netbook Asus 1005p. I love Ubuntu but have rarely had such issues with a programme like I have had with 'evolution'.Surely it should not be this hard to get your email?

But the lack of port switching facility (and yes I have learned about the :587 trick now...) and now frustrations over being 'timed out',are quite annoying.

Any answers on 'timed out' ?

I am generally connecting to btinternet (mail.btinternet.com)

Regards

---

