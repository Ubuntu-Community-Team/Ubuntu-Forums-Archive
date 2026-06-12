---
title: "Unable to send/receive mail in Evolution"
date: 2009-10-22
forum: General Help
---

### Post by john pilcher on 2009-10-22
Background details : Ubuntu on my D drive & XP on my C drive. Set up Evolution this morning (2 hours ago local time) on D drive & appeared successful. However, have been unable to send or receive mail since with an error shown "host lookup failed : PoP3 : name or service not known". This server (PoP3) is identical to that used Outlook Express which i'm guessing is what i did wrong. Have not been able to fix/reset/redo etc. Has anyone a solution at i do need Evolution for my work with Ubuntu.   

thanks
John

---

### Post by arnab_das on 2009-10-22
depends on the email service ur using. if its hotmail, it isnt as compatible with it as outlook is.

---

### Post by john pilcher on 2009-10-22
Can't see how its Hotmail as i have never used it. I'm hoping the error message can help someone sort it out for me.

---

### Post by dcstar on 2009-10-23
> **john pilcher said:**
> Background details : Ubuntu on my D drive & XP on my C drive. Set up Evolution this morning (2 hours ago local time) on D drive & appeared successful. However, have been unable to send or receive mail since with an error shown "host lookup failed : PoP3 : name or service not known". This server (PoP3) is identical to that used Outlook Express which i'm guessing is what i did wrong. Have not been able to fix/reset/redo etc. Has anyone a solution at i do need Evolution for my work with Ubuntu.   

thanks
John

"PoP3" is not a full mail server address. Put in the correct FULL address and it will work.

---

### Post by SoftPops on 2009-10-23
[FONT=Times New Roman][SIZE=3]I had similar problems when I first setup Evolution.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I am assuming you have copied the POP3 and SMTP server details from Outlook Express.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I resolved the problem by checking/modifying the authentication type in both the “receiving e-mail” and “sending e-mail” options. As per attached screenshots.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Hope this helps.[/SIZE][/FONT]

---

### Post by john pilcher on 2009-10-23
How do i get back to that stage ? Am i correct in assuming i should show PoP ?

regards
John

---

### Post by plucky on 2009-10-23
> **john pilcher said:**
> How do i get back to that stage ? Am i correct in assuming i should show PoP ?

regards
John

Within Evolution **Edit > Preferences > Mail Accounts > Select Account > Edit > Receiving email** will open those windows.

Good Luck

---

### Post by john pilcher on 2009-10-23
Ok, have accessed Account Editor & matched Server details for Receiving & Sending. But still unable to send or receive. Adding & then deleting Password didn't make any difference. Nor did a new message. This seems a silly idea but do i need a new Email address apart from the one i use for Outlook Express ? Have now found out that ISP doesn't support Evolution. Can you suggest one that does ? I only need Evolution for Email occasionally while i "test run" Ubuntu or any other Linux variation for that matter.

thanks

---

### Post by plucky on 2009-10-24
> This seems a silly idea but do i need a new Email address apart from the one i use for Outlook Express ?

Evolution is an email client the same as outlook express,so you don't need a new email address.

> Have now found out that ISP doesn't support Evolution. 

Most ISPs have probably not heard of Evolution and will not be able to support it.You just need to set up the same as Outlook Express.

Who is your email provider? 

Perhaps we can look up their requirement and tell you how to set up evolution.It is usually to do with what type of Authentication the email servers are expecting to see when Evolution connects.Perhaps you could try different Authentication settings,assuming the server information is correct.

Good Luck

---

### Post by SunfireSSR on 2009-10-31
My ISP (ATT.YAHOO) wants to set POP and SMTP locations like 877 and 325. Where do I do that in Evolution ?

---

### Post by plucky on 2009-11-01
> **SunfireSSR said:**
> My ISP (ATT.YAHOO) wants to set POP and SMTP locations like 877 and 325. Where do I do that in Evolution ?

```
pop.yahoo.co.uk:877
smtp.yahoo.co.uk:325
```


You need **:port number** after the server name.

Good Luck

---

