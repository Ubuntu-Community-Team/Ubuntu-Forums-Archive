---
title: "Fileservers"
date: 2006-02-20
forum: General Help
---

### Post by Iandefor on 2006-02-20
I've got an old computer I'd like to use as a fileserver. I've heard of samba, but would like to hear other options in terms of fileservers. Keep in mind that this would be my first venture into servers, so if, in general, there's anything it would be handy to know, feel free to share it.

So: 
1) Fileservers other users would endorse
2) Anything useful for a new user to know

Thank y'all so much!

---

### Post by uopjohnson on 2006-02-20
What systems would you be serving files too?  Samba is good if you have windows computers on the network.  In fact it is preety much it in this situation.   I primarily use ssh and sftp to move files between my backup file server and my linux systems.

---

### Post by Iandefor on 2006-02-20
[quote=uopjohnson]What systems would you be serving files too? Samba is good if you have windows computers on the network. In fact it is preety much it in this situation. I primarily use ssh and sftp to move files between my backup file server and my linux systems.[/quote] Primarily between Mac OS X and Linux. And about Samba: I'd heard that, which is why I didn't just jump to Samba, since I wouldn't be moving any files to a Windows computer.

---

### Post by Iandefor on 2006-02-21
This is partially a thought and a *bump*:

For accessing the files, I'd prefer to not need specialized client software.
Could I just use an http server for directory access via a web browser? I've looked a little bit at myServer, but I'm not at all certain how secure this would be; I'd rather not leave it wide open. Any thoughts?

---

### Post by spartas on 2006-02-21
You could use a web server for this purpose, but it would be world-accessible unless you block the port on the firewall upstream from the server or require authentication for accessing the files.

Samba would probably be easier to set up than a secure web system, but that also depends on the amount of clients you need to set up as well.

---

### Post by Iandefor on 2006-02-21
[quote=spartas]You could use a web server for this purpose, but it would be world-accessible unless you block the port on the firewall upstream from the server or require authentication for accessing the files.

Samba would probably be easier to set up than a secure web system, but that also depends on the amount of clients you need to set up as well.[/quote] Does Samba need a specialised client, though? There are computers I'd want to serve files to that I wouldn't be allowed to install software on.

---

### Post by spartas on 2006-02-21
Samba uses the Windows, and Mac standard networking protocols built-in to the operating system, so you shouldn't need a specialized client with it.  You may need a samba client for your linux machines though.

Will the clients need to upload files as well?  If this is the case, you can almost cross off any web-based system unless you want to use ftp, which may be easier for you anyway.

[100th post]

---

### Post by Iandefor on 2006-02-21
[quote=spartas]Samba uses the Windows, and Mac standard networking protocols built-in to the operating system, so you shouldn't need a specialized client with it. You may need a samba client for your linux machines though.

Will the clients need to upload files as well? If this is the case, you can almost cross off any web-based system unless you want to use ftp, which may be easier for you anyway.

[100th post][/quote] Ah, I see. Thank you! So, your recommendation is Samba? As an aside, these will be remote clients, and the clients will most likely need to upload.

EDIT: Looks like Mac OS X needs a Samba client to make it work.

---

