---
title: "how to share files/folders with Windows PCs and access their files/folders?"
date: 2009-10-17
forum: General Help
---

### Post by hotpinkflamingo on 2009-10-17
Hello,
There are a total of 4 PCs in my house.  Mine is physically connected to a wireless router/cable modem.  The other 3 PCs connect to the internet via the wireless router.  My PC is set up with dual boot-Windows XP professional and Ubuntu.  One other computer has dual boot-Windows Vista and Ubuntu. The other two PCs run XP professional.

I would like to be able to share files with, and browse files on the other computers with Ubuntu.  With Windows it's pretty simple; all we do is mark a folder as shared, and the other computers can access it.

With the default configuration of Ubuntu, I can't seem to access the other computers, nor can they access my files.  I did some searching, and anything regarding sharing files with Windows usually brings up something called "Samba".  But, it seems like it's for setting up a Ubuntu server that Windows computers can access.

Is Samba what I should use? Or is there a simpler way to do what I want to do?

Thank you.

edit= May be a stupid question, but if I install Samba, or enable file sharing between the computers somehow, do I need to worry about turning on the Ubuntu firewall or anything?  
The wireless router is set up so that only PCs with specific MAC addresses (ours) can access it.

---

### Post by swerdna on 2009-10-17
Yes, Samba is the software for sharing resources with windows machines.

UFW is the default Ubuntu firewall. You can turn it off while you set up samba with this command:```
sudo ufw disable
```and worry about it later. Here's how to fix it (after Samba is working): [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

This will assist you to fully configure sharing:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home or Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by hotpinkflamingo on 2009-10-18
thank you very much  :D

---

