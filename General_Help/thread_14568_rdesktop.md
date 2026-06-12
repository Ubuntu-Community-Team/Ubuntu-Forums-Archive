---
title: "rdesktop"
date: 2005-02-08
forum: General Help
---

### Post by anomie on 2005-02-08
Does anyone know how I can find out what level of encryption rdesktop uses by default? I have poked around on rdesktop.com, google, etc. and I am not able to find a clear answer. I would like to confirm that if I am using it I'm communicating via a *secure* pipe. 

I am using the rdesktop that is included with Warty 4.10 (which is of course what I am running). 

Thanks in advance.

---

### Post by RichardA on 2005-02-08
I think RDesktop is an RDP client? If so...

"RDP uses RSA Security's RC4 cipher"

From:
[http://msdn.microsoft.com/library/default.asp?url=/library/en-us/termserv/termserv/remote_desktop_protocol.asp](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/termserv/termserv/remote_desktop_protocol.asp)

---

### Post by anomie on 2005-02-08
Yes, it is an RDP client. 

Thanks for the URL. It appears the encryption level setting is completely on the server side. It would be nice if rdesktop could report what level of encryption it is using for any given connection.

---

