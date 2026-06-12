---
title: "command line ftp"
date: 2012-04-24
forum: General Help
---

### Post by conradin on 2012-04-24
Hi all
I am having problems loging into my FTP server. 
The user-name i am logging in from is not a user of the ftp server.
I tried specifying, [email]User@ftp.server.edu[/email]
and ftp.server.edu.:User
but both of those give me errors. 
using the open command prompts me to use the local user. How Can I prevent the local user from being the default login?
Or what is wrong with my syntax?

---

### Post by jonobr on 2012-04-24
if you were going from browser you would use
ftp://user@<address>

where address is 
ip address
fqdn
or hostname if on the local system.

I dont get what you mean by the user not being on the system,
There should be an ftp account on the system when you login, whether it be one set up for you or an anonymous login.

Lastly, I sure hope I am not helping you with Homework.

---

