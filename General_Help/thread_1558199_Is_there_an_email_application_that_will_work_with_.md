---
title: "Is there an email application that will work with hotmail/live mail?"
date: 2010-08-21
forum: General Help
---

### Post by netsavy006 on 2010-08-21
Basically I want to know is there an email application available for Ubuntu 10.04 that supports Hotmail/Live mail?

Thanks,
Andy.

---

### Post by lisati on 2010-08-21
Yes. Evolution can. 

To use POP3, use pop3.live.com:995 as the incoming server with SSL encryption, and <hotmail_username>@hotmail.com for the username. The SMTP server is smtp.live.com:25, I find TLS encryption seems to work.

---

### Post by netsavy006 on 2010-08-22
Thanks.  Got Evolution working with my hotmail account.  Thanks.

---

### Post by Carthorse on 2010-09-03
Me too, been wondering for a while if it could do this :-) Many thanks.

---

### Post by Toke on 2010-09-03
I am trying right now. 
I have gotten it to receive and have just downloaded all from my hotmail account.

Sending seems to be a problem?

> Error while performing operation.
Failed to connect to SMTP server smtp.live.com in secure mode: STARTTLS not supported

---

### Post by Fableflame on 2010-09-03
Related question:

Can I set up more than one email account on Evolution?

---

### Post by philinux on 2010-09-03
> **Fableflame said:**
> Related question:

Can I set up more than one email account on Evolution?

I have 4. However they will by default share the inbox. This is easily fixed by creating folders and using filters.

---

### Post by Toke on 2010-09-03
> [IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] 				**[SOLVED] HOWTO: Send and Receive Hotmail through Evolution** 			
 			 			 		   		 		 		Go to Edit/Preferences and edit your email account or (Shift + Ctrl + S)

Identity tab
Full name - enter your Full Name
Email address - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
**Server: smtp.live.com:587**
Tick the box Server requires authentication
**Security: TLS encryption**
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.

Notice the port 587, it makes the difference with the TLS encryption.
Hope this helps everyone! :smile:

:guitar:

Here is a quote from another tread that worked for me.

---

