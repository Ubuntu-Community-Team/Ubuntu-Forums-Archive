---
title: "gtalk for my domain with empathy"
date: 2009-11-02
forum: General Help
---

### Post by sharat87 on 2009-11-02
[SIZE=1]Hello all,

I have just installed ubuntu 9.10 and configured empathy to connect to my Google talk. I also want to use empathy to connect to my domain's google talk account. I found [this page]("http://www.google.com/support/a/bin/answer.py?hl=en&answer=49147") on google's help about how to do this with pidgin, but I cant seem to make out the corresponding preferences for empathy.

Please help.

Thanks[/SIZE]

---

### Post by darkstaar on 2009-11-02
In the Login ID field, enter your entire e-mail address. In the 'Advanced' section, make sure that the Encryption box is checked. The server is 'talk.google.com', use port 5223, and check 'Use old SSL'.

---

### Post by sharat87 on 2009-11-02
Thank you for your response, I gave the following options, for a new account with Google talk ( or should I choose Jabber?)
Login ID: [email]email.id@domain.com[/email]
password: ***
[checked] Encryption Required
Server: domain.com
Port: 5223
[checked] Use old SSL

I left the rest as they are.. I still get a Network error. I can see my gtalk contacts though.

---

### Post by darkstaar on 2009-11-02
> **sharat87 said:**
> Server: domain.com

No, that's wrong. Server should be **talk.google.com**

---

### Post by sharat87 on 2009-11-03
oh sweet! Thank you so much darkstar...

I did not notice that.. my bad :)

It works fine now, thanks again.

---

### Post by dy-namo on 2009-11-15
[SIZE=3]In order to get google talk working do you have to have the jabber account? [/SIZE]

---

### Post by dy-namo on 2009-11-15
I got it working. I tried this which was posted on another thread and it's working without any problems.

login id: [EMAIL="username@gmail.com"]username@gmail.com[/EMAIL]
password: password
Encryption required (unchecked)
Ignore SSL (checked)
Resource: blank
priority: 0
server: talk.google.com
port: 5223
use old ssl: checked

---

### Post by b33god on 2010-03-02
> **darkstaar said:**
> In the Login ID field, enter your entire e-mail address. In the 'Advanced' section, make sure that the Encryption box is checked. The server is 'talk.google.com', use port 5223, and check 'Use old SSL'.
Thanks that fixed it for me :)

---

