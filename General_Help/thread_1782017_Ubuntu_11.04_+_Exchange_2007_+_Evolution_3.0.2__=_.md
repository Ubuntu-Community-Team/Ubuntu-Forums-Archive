---
title: "Ubuntu 11.04 + Exchange 2007 + Evolution 3.0.2  = No email"
date: 2011-06-14
forum: General Help
---

### Post by tommytookamoto on 2011-06-14
Hello all,

Running exchange 2007, Evolution 3.0.2 and Ubuntu Natty - 11.04.
Evolution wont accept passwords when configured to use IMAP.
I have also tried install Evolution-MAPI but it throws out the below error.

apt-get install evolution-MAPI
The following packages have unmet dependencies:
 evolution-mapi : Depends: evolution (< 2.33) but 3.0.2-0ubuntu1~natty1 is to be installed
E: Broken packages

Really want to move to Linux apps only currently running outlook via WINE, I want to make the jump to Evolution, but keep failing no matter what I try.

Any ideas?

Thanks in advance.

---

### Post by mastablasta on 2011-06-14
what about Thunderbird?
 
what about using LTS?

---

### Post by collisionystm on 2011-06-14
I had the same problems with Evolution and Exchange 2007. I dont believe evolution is entirely exchange compatible. I would suggest using Zimbra. It is the closest thing to outlook that I can find for linux.

---

### Post by dandnsmith on 2011-06-14
If you get a password failure, it could well be an encryption algorithm error - so you're passing the word either plaintext or default encrypted, and the other end expects something different.

I remember that, in the days of Win95, Win98 and comparable releases of linux, there used to be a fair bit of knowledge about how to set each end. I know that is out-of-date stuff now (default encryption changed, certainly at the Windows end), but don't know how to get it right now. Possibly Google might be your friend here.

---

### Post by Ender985 on 2011-06-14
I'm running Lucid and Evolution 2.28.3 , and I made it work with an Office Exchange 2003. My versions are different form yours, but maybe my configuration can help you out on this anyway.

In Edit -> Preferences -> Mail Account -> Edit -> Receiving Email tab:

Server Type: Microsoft Exchange (not IMAP)
OWA URL: [http://internal.server.address/exchange/](http://internal.server.address/exchange/)
Authentication Type: Plaintext Password

I know it is not secure to send the passwords in plain text, but the server would refuse any kind of encryption so there is not much I can do. This is all part of an internal LAN with a monstrous firewall separating it from the internet, so it should be less dangerous than just sending the password through the wild internet.

Hope that helps somewhat.

---

