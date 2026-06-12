---
title: "Mapping a Windows Share"
date: 2006-04-09
forum: General Help
---

### Post by munroe on 2006-04-09
I'm attempting to connect to a Windows Share on my College's Network. I need to be connected to their VPN(which I am), and then I have to map the drive using only \\algshare\home as a connection point. I called the IT department, but they wouldn't give me any more information about the server our drives are on.

I'll need to specify a custom username/password when I attempt to connect. Anybody have any ideas?

---

### Post by Face1 on 2006-04-09
As I understand it, the default username/password given (by windows) when you connect to a share is simply your own username password.  So, if I understand your question correctly to be that windows users can simply just connect to the share, I would think that any username and a blank password would work.

---

### Post by llib on 2006-04-19
This depends on if they are using a Windows Server to provide authentication, which, if this is a business, they probably are.  In that case you would probably need your friends ID and password to access his system and shares.  He should be able to provide you with his systems name, looking in his network settings.  The share would be available by looking at the folder properties for the directory you were accesing.
Hope that helps.

---

