---
title: "gnump3d access problems"
date: 2006-05-22
forum: General Help
---

### Post by sgusev on 2006-05-22
I am having issues getting gnump3d to work with my router. I've set the config file to allow access to all with no password, I've also forwarded the port on my router in the same way that I did for VNC and SSH, both of which work fine. I can access gnump3d no problem on my local network, even using the external IP address, but I cannot access it from outside. The apache logs are showing access attempts but the gnump3d log is not, however, the gnump3d error.log is showing this:

Caught a SIGTERM at /usr/lib/perl/5.8/IO/Socket.pm line 183

but i'm not sure if its the problem. The only other thing I could think of is that I have to set some time of permissions either in apache, or on the folder directly. Any help would be really appreciated.

---

### Post by mohnkern on 2007-04-30
I'm seeing exactly the same error.  I did a fresh install of gnump3d on  new box.  Before I had a box with Edgy upgraded to Feisty, and wasn't seeing the error.

---

### Post by mohnkern on 2007-04-30
When I try to access from the outside, all I get is a blank page.  

Here's the error.log 

No mime type found for /usr/share/gnump3d//Tabular/
Header: HTTP/1.0 200 OK
Connection: close
Server: GNUMP3d 2.9.9.1
Content-type: text/html
Content-Range: bytes 0-4096/4096
Content-length: 4096
Last-Modified: Mon, 30 Apr 2007 15:48:30 GMT
Set-Cookie: theme=Tabular;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;

---

