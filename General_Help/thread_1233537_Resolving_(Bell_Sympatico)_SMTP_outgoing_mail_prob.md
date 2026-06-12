---
title: "Resolving (Bell Sympatico) SMTP outgoing mail problem"
date: 2009-08-06
forum: General Help
---

### Post by knarfman on 2009-08-06
Wondering if anyone (Canadian) who uses Bell Sympatico (Quebec in particular) as their ISP and Evolution Email Client has had any success in configuring their outgoing mail. I have looked on many forums and spoken to my ISP but to no avail. They are useless as they have no techs who know Linux/Ubuntu. I know it HAS to work somehow as I am able to receive email from two other accounts. I have tried NUMEROUS configurations and nothing is working. I tried telnet smtphm.sympatico.ca 25 in the terminal window as suggest by a friend and I did get feedback that it was working however it is telling me about hotmail with a smtp in another province. The port, therefore, doesn't looked as if it is blocked. Strange.

Anyway, I **_hope_** someone can help as I have wasted hours on this and am at wit's end. Thanks in advance for any help you can give. I really need to get this working!

---

### Post by starcraft.man on 2009-08-06
Former Bell Quebec customer here, now with [Tek Savvy]("http://www.teksavvy.com/en/index.asp") (good company cross Canada, only 30 bucks for DSL + 200GBs a month, flat rate no contract). See the page for more details.

As far as I know, the outgoing SMTP for my clients was always configured to smtp1.sympatico.ca, I had it configured fine with thunderbird for many years without fail, both on Windows and later for a short while on Linux. I see no reason why it shouldn't work on Evolution, this isn't something platform specific, it's supported well. 

Try thunderbird please with that outgoing address, try Evolution as well. I personally suggest you move to an ISP neutral provider like gmail or windows mail or whatever suits your fancy. After that, consider switching dsl providers. Bell is a terrible company, I used to pay almost 70 bucks for a 90 GB cap, now I pay 40 for unlimited.

---

### Post by knarfman on 2009-08-08
starcraft.man, thanks lots for the info, i'll check into it. never heard of this company before. as for resolving the smtp issue, no luck so far, tried what you suggested and it just won't work..... will look into thunderbird also. all said, it's very aggravating! LOL.

---

### Post by brydonhunter on 2009-08-09
I had that problem as well, try port 26

---

### Post by mistermeta on 2009-09-20
to send SMTP mail to hotmail via outlook express or other SMTP clients via Sympatico's ISP use the following SMTP address:


**smtphm.sympatico.ca**

but before you do, google "SMTP servers sympatico" it should lead to a page showing the complete list) - you may be in a different zone than I am (Ontario).

---

### Post by shibainucan on 2009-09-22
I found instructions for configuring Thunderbrid with Sympatico.  It must be similar for Evolution.

How do I get Thunderbird to work with enhanced e-mail? (#15737)
In thunderbird, go: tools-> account settings
•under e-mail address "someone"@sympatico.ca
•go->server settings : at "server Name" : pophm.sympatico.ca port 995
•user name put "someone"@sympatico.ca
•server settings below, make sure use secure connection (ssl) is checked.
BUT NOT SECURE AUTHENICATION

For sending e-mail : go: tools-> account settings->outgoing server (smtp)
•server name: smtphm.sympatico.ca
•port 25 (note, if port 25 does not work, try using 587 instead)
•use name and password-> checked (authenication)
•user name "someone"@sympatico.ca
•use secure connection : TLS

It will ask you for your password the first time, you can leave it like that, or use the optional remember password.  

The password to use is the one you use to access your web (sympatico/hotmail) account.

---

### Post by shibainucan on 2009-09-22
I notice that there is no place in the Evolution wizard to set the port.  I found out how to set the port from another thread:  

 Re: Evolution: How to Change Email Port Address
Click on Edit -> Preferences -> Double click on your mail account -> Click on Sending Email tab -> Then for your host: all you need to do is add the port number to the end like this my.server.com:3535

---

### Post by Gore33 on 2009-11-01
Go to _edit_ then _preferences_

Click on edit (by default this should be on the right page once you open preferences if not then make sure your in **Mail Accounts** and your default email account is highlighted then click edit)

Click on **Receiving Email **tab and make sure under_ Server_: you have **pophm.sympatico.ca**

Under _Username:_ make sure you have your **_email address_** typed here

Under **Security** select SSL encryption

Under **Authentication Type** select _Password_ and check on _remember password_

Ok now click on** Sending Email** tab

Make sure **Server**: smtphm.sympatico.ca looks like this

Then Check on _Server requires authentication_
Under** Security** _Use Secure Connection_ select [SIZE=4]**TLS encryption**[/SIZE]

Under **Authentication**

_Type_ should be **PLAIN**

_Username_: should be your _**email address**_

NO CHECK MARK FOR_ Remember password_

That should do it good luck

---

### Post by Steve Redmond on 2010-01-13
Hi! I just want to confirm the settings for both Evolution and Thunderbird that were stated recently in this forum, and are working for me now.  I am a Bell Sympatico user located in Ontario, Canada.
 
For receiving email I use: 
    server type: **POP**
    server: **pophm.sympatico.ca**, 
    username: **my email address**,
    port **995** (Thunderbird) or unspecified default (Evolution),
    secure connection: **SSL** encryption,
    authentication type: **Password**,
        check off **remember password** (password is requested the first time)
 
For sending (outgoing server) email I use:
    server type: **SMTP**
    server: **smtphm.sympatico.ca**
    port: **25** (Thunderbird) or unspecified default (Evolution)
    check off **server requires authentication** (Evolution), 
        or use name and password (Thunderbird)
    secure connection: **TLS** encryption  (** see **notes**)
    authentication type: **login** (Evolution)
        username: **my email address**
        check off **remember password** (password is requested the first time)
 
**Notes:  For me, the critical breakthrough was using **TLS** security for outgoing email, instead of **SSL**.  See Bell Sympatico online recommendations for mail server settings:([http://internet.bell.ca/index.cfm?method=content.view&content_id=1067](http://internet.bell.ca/index.cfm?method=content.view&content_id=1067)).  Bell Sympatico specifies **SSL** for both incoming and outgoing email.  Bell Sympatico specifies incoming port 995, and outgoing port 25 or port 587 in case port 25 gives problems.  On my WinXp computers (3), I use both Office Outlook 2000 or 2003, and Outlook Express 6.  They all use **SSL** secure connections for both incoming and outgoing email quite successfully.  On one of my computers (a bit older, slower and more bloated) I had to switch to port 587 to get outgoing email to work.  I do not know what subtle variations occur between these three computers, and between **SSL** and **TLS**.  It is good to find combinations that work, but worrisome that they might not always work.  The reality is that the Bell Sympatico recommended settings are only working in about 2/3 cases, regardless of which mail program and operating system is used.  It is apparent also that we (Ubuntu users and the like) are on our own, as Bell Sympatico assumes the world runs on Windows with Outlook.  We must hack away to find solutions.
 
Getting email to work reliably is crucial to my ultimate conversion to Linux/Ubuntu/Evolution/etc.  Today I am one step closer. :)
 
I appreciate the information and help I have received from the Ubuntu community.  
 
Steve

---

### Post by mulder_25 on 2010-02-15
I have managed to successfully connect my evolution mail client to sympatico , here are my settings if anybody need them:
 in account editor - recieving email 
server type - pop
server - pophm.sympatico.ca or pophm.sympatico.ca:995
user-name -youremailadress  eq. [email]someone@sympatico.ca[/email]
use secure connection - SSL encryption
authentication 
 password   
 check -remember password

for sending email

server type - SMTP
server smtphm.sympatico.ca:587
check -server requires authentication
use secure connection TLS encryption
authentication 
type - login
user-name - youremailaddress eq. [email]someone@sympatico.ca[/email]
leave remember password unchecked 


i hope it helps

---

### Post by 99_rover on 2010-10-29
Having the same problems with Bell Ontario

incoming is fine but outgoing failed two days ago

tried all of the above

outgoing

[email]smtphm@sympatico.ca[/email]
port tried 25, 465, 587 
security have options of SSL/TLS or STARTTLS tried both

tried use secure with email as user - no luck - did not ask for password just timed out 

no luck

---

### Post by 99_rover on 2010-10-29
sorry should have read smtphm.sympatico.ca

---

### Post by dcstar on 2010-10-29
> **99_rover said:**
> sorry should have read smtphm.sympatico.ca

```
telnet smtphm.sympatico.ca 25
telnet smtphm.sympatico.ca 587
```

If you cannot connect then **you** have a network problem. If you can connect then it is an authentication/setup issue.

---

### Post by 99_rover on 2010-10-30
connection works on 25 and 587 using telnet

now what

the ISP was no help - the best suggestion was install windows !!!!!!!!!!!!

---

### Post by 99_rover on 2010-10-30
Tried all the suggestions on the Thunderbird support site - no help - but it seems a lot of people have the problem

heeeeeeeeeeeeelllllllllllllllppppppppp

---

