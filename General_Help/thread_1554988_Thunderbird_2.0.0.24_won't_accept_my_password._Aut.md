---
title: "Thunderbird 2.0.0.24 won't accept my password. Authentication error."
date: 2010-08-17
forum: General Help
---

### Post by anthony62490 on 2010-08-17
Thunderbird setup is as follows:
```

**Account Type:** Email
**Name:** Anthony
**Email:** anthony@#######.org
**In Server:** POP / 
**Out Server:** smtpout.secureserver.net
**Incoming user name:** anthony
**Account Name:** Main Email

```

After this setup, I click "Get Mail" and enter my password. I am greeted by a message saying
> Sending of password did not succeed. Mail server pop.secureserver.net responded: authorization failed [sic]

Did I set something up wrong? The server addresses were supplied by my email account, so there is no problem there. I have no firewall set up. Any ideas?

---

### Post by sydbat on 2010-08-17
> **anthony62490 said:**
> Thunderbird setup is as follows:
```

**Account Type:** Email
**Name:** Anthony
**Email:** anthony@#######.org
**In Server:** POP / 
**Out Server:** smtpout.secureserver.net
**Incoming user name:** anthony
**Account Name:** Main Email

```

After this setup, I click "Get Mail" and enter my password. I am greeted by a message saying


Did I set something up wrong? The server addresses were supplied by my email account, so there is no problem there. I have no firewall set up. Any ideas?Have you checked your "Security Settings" in TB? Might be they are set to none, or are on and you don't need them (happened to my wife's account).

---

### Post by anthony62490 on 2010-08-17
> **sydbat said:**
> Have you checked your "Security Settings" in TB? Might be they are set to none, or are on and you don't need them (happened to my wife's account).

Under "Account Settings"
**Security: **Security settings for Digital Signing and Encryption are blank

**Server Settings: **Port is set to 110
Never use secure connection
Secure authentication box is unchecked

---

### Post by anthony62490 on 2010-08-17
bump

---

### Post by Richshark on 2010-08-18
I had exactly the same problem with Thunderbird 3.1. Searched a bit and found  It may be that the password is actually correct, but that the "Incoming User Name" setting under Server Settings could require your whole email address, not just your name i.e. [email]anthony@.....org[/email] or whatever your POP3 server's requires. Also, should your In Server not be set to pop.secureserver.net - not POP /? Hope this helps.

---

### Post by anthony62490 on 2010-08-18
> **Richshark said:**
> I had exactly the same problem with Thunderbird 3.1. Searched a bit and found  It may be that the password is actually correct, but that the "Incoming User Name" setting under Server Settings could require your whole email address, not just your name i.e. [email]anthony@.....org[/email] or whatever your POP3 server's requires. Also, should your In Server not be set to  - not POP /? Hope this helps.

\o/ Thank you SO much. My Incoming User Name was supposed to be my email address. 

Btw, the POP / pop.secureserver.net was meant to indicate that the POP radio button was filled.

Thanks again.

---

