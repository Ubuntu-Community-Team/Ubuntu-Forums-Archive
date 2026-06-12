---
title: "Not sure what I'm logging into"
date: 2009-09-20
forum: General Help
---

### Post by RFXCasey on 2009-09-20
OK, so now I have vsftpd installed on my server. I also installed SSH on my son's Ubunutu desktop box and successfully logged in using WinSCP though his machine doesn't have vsftpd installed or any other FTP that I know of. So back to my server which has both SSH and vsftp. When I log into that I don't see the custom server message I put in vsftpd.conf. It kinda seems like when I log into it it's exactly the same as logging into my son's machine. If you have SSH installed can you simple connect via WinSCP to SSH? Or do you have to have an FTP server running? It seems like on my son's machine I only have to have SSH and I can WinSCP into it. How can I tell if the same thing is happening on my server or do I even need vsftpd installed at all? As I say I don't see the logging welcome message for vsftpd so I think I am only logging into SSH, would that be right? If so what would you need vsftpd for?

---

### Post by RFXCasey on 2009-09-21
Anyone?
:confused:

---

### Post by Iowan on 2009-09-21
I just tried it on my SSH-enabled server.  **scp** works without logging onto SSH. But you were talking about WinSCP.  I fired up my XP box, downloaded/installed WinSCP (although I already have PuTTY), and tried it - It, too, will connect. (My server does not have **vsftp**)

---

### Post by RFXCasey on 2009-09-21
So what does that mean? How is that happening? WinSCP must be acting as a gui for the shell login. I guess this is nothing new to most people and I am just an FTP newb. So what would you need an FTP server program for? I am assuming you can just set the rights of the user to restrict them to whatever you want. But you can do that with the shell account too can you?

---

