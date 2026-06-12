---
title: "Samba client annoyance"
date: 2006-04-21
forum: General Help
---

### Post by elamericano on 2006-04-21
I've connected to some Windows shares in my workplace, and I can access the files I want. I have some icons on my desktop that remember the shares I've opened. For some reason whenever I click on these I get a login screen from some random computer on the network, and if I enter a password I'll get another prompt from someone else. I get these until I cancel, whereupon my share finally opens, because the password is saved in my keychain.

The first time I tried to keep entering password, until my domain controller locked my account. Now I just cancel the first one I get, but I don't know why this happens or how to stop it. Maybe someone knows the answer  or has something I could try.

I'm finally down to the last couple of issues with my installation. :)

---

### Post by elamericano on 2006-04-21
I forgot to mention, this is a straight Breezy install. I haven't had to do any Samba configuration whatsoever.

---

### Post by Computeruser on 2006-04-21
I get the same thing. When I try to connect my Desktop Ubuntu to my Desktop Windows via the Ubuntu icon, it want to connect out to my Laptop. I never did that, so it has nothing to remember from. I did change smb.conf to use WORKGROUP instead of MSHOME, but other than that, I did not change the config file. I just cancel the login request and then login in the box that remains. Works.

---

### Post by elamericano on 2006-04-24
Is this "normal" behavior then? or are there people on a large Windows network who don't have this happen?

---

### Post by smdeep on 2006-04-24
Hi

I have ubuntu (5.04) installedo on a laptop. When I try to connect to a Fedora Core 4 server running Samba, I can connect. But when I open the files in a editor I get them as read only. The other Windoze computers connect without any problems to the Fedora Samba server.

Another thing, when I click on Network in Nautilus none of the computers in the network shows up. Do I have to install samba on the laptop to connect to a Samba server?

Thanks in advance

---

### Post by elamericano on 2006-04-25
smdeep,

I think you need to enable WINS to browse a Windows network. You can try searching for that. However, that problem is unrelated to my own. Please open a new thread for discussion, or else I am less like to get an answer to my question.

Thanks.

---

### Post by smdeep on 2006-04-25
elamericano

I apologise for posting here. I just thought since it was a related problem it would be easy for both of us.

I will open a new thread.  Once again, sorry.

---

### Post by elamericano on 2006-05-01
OK, if the answer (or the problem) is unknown. Where are your favorite places for Samba configuration discussion and support?

---

