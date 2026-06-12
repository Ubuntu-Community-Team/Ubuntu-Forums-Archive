---
title: "Can't send hotmail in Evolution"
date: 2009-07-12
forum: General Help
---

### Post by c0mput3r_n3rD on 2009-07-12
Hello all,
  I just set up my hotmail account in Evolution with out using the proposed solution [http://ubuntuforums.org/archive/index.php/t-886798.html](http://ubuntuforums.org/archive/index.php/t-886798.html), because I found something else that works out better and easier, which is setting the options to this:
```

Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password
 Outgoing server: smtp.live.com
Server requires authentication: yes
Security: SSL
Authentication type: plain
 
```

  Everything seemed to work out fine, except I can't send mail; receiving is fine how ever.  If any one has a solution to this it would be greatly appreciated.  I've also read about other mail clients, perhaps another would work out better?  

Thanks in advance.

---

### Post by wojox on 2009-07-12
Edit>Preferences>Mail Accounts>Add

Receiving(POP) Mail

    *

      Server Type: POP
    *

      Server: pop3.live.com (Port 995)
    *

      Username: [email]johndoe@hotmail.com[/email]
    *

      Use Secure Connection: SSL encryption
    *

      Authentication: Password Authentication 

Sending(smtp) Mail

    *

      Server: smtp.live.com (Port 25 or 587)
          o

            Note: Some ISPs block port 25, if you are having a problem sending mail, substitute smtp.live.com:587 for the server information above. 
    *

      Server requires authentication: Checked
    *

      Security: TLS encryption
    *

      Authentication: Plain or Login
    *

      Username: [email]johndoe@hotmail.com[/email]

---

### Post by c0mput3r_n3rD on 2009-07-12
Still nothing :-\

---

### Post by germanicus8 on 2009-07-27
> **wojox said:**
> Edit>Preferences>Mail Accounts>Add

Receiving(POP) Mail

    *

      Server Type: POP
    *

      Server: pop3.live.com (Port 995)
    *

      Username: [EMAIL="johndoe@hotmail.com"]johndoe@hotmail.com[/EMAIL]
    *

      Use Secure Connection: SSL encryption
    *

      Authentication: Password Authentication 

Sending(smtp) Mail

    *

      Server: smtp.live.com (Port 25 or 587)
          o

            Note: Some ISPs block port 25, if you are having a problem sending mail, substitute smtp.live.com:587 for the server information above. 
    *

      Server requires authentication: Checked
    *

      Security: TLS encryption
    *

      Authentication: Plain or Login
    *

      Username: [EMAIL="johndoe@hotmail.com"]johndoe@hotmail.com[/EMAIL]


This should work, at first I couldn't seem to get it work, but I double checked my evo settings, and walla!!!

It does work after all.

---

