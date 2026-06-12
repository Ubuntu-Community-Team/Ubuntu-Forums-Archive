---
title: "SSH Can't log in on my desktop (Permission Denied)"
date: 2009-12-16
forum: General Help
---

### Post by Mimz on 2009-12-16
Okay so when I try this command

sudo ssh -D 443 username@MYIP

It connects the computer (my desktop) and it prompts me for the password. So I type in the password and it says

Permission denied please try again

but when I use my desktop computer to log in to my laptop computer it works perfectly fine! does anyone know why this does this and/or how I can/might be able to fix this

---

### Post by ibuclaw on 2009-12-16
Is ssh-server installed on the Desktop? and you aren't blooking port 443?

Regards
Iain

---

### Post by apmcd47 on 2009-12-16
Why are you doing sudo ssh? Surely only ssh is necessary. sudo ssh would surely prompt you for password twice, once for sudo, once for ssh.

Andrew

---

### Post by Mimz on 2009-12-16
well the port 443 calls for root privelages 

but yes I do have ssh installed on both computers

---

### Post by Mimz on 2009-12-16
bump

---

### Post by Mimz on 2009-12-16
c'mon anyone?

---

### Post by apmcd47 on 2009-12-17
> **Mimz said:**
> well the port 443 calls for root privelages 

but yes I do have ssh installed on both computers

and sshd?

Port 443 only calls for root privileges for setting up a server, ie for listening at the port. Using the ssh client does not require root privilege. There should be an sshd script in /etc/init.d and /etc/rc3.d, which would cause sshd to be run on startup.

Andrew

---

