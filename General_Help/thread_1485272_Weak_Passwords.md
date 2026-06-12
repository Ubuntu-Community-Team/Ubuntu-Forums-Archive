---
title: "Weak Passwords"
date: 2010-05-16
forum: General Help
---

### Post by Ron O on 2010-05-16
The more I look into security, the more complicated it gets, and I'd like to be reasonably secure until I can study this. 

What are the real world implications of running a weak password on a single home system connected to the internet via DSL? 

Am I getting any protection from the iptables firewall out of the box with no further configuration?

How good are strong passwords anyway, when a brute force program like DVD decrypter can crack a protection scheme in a matter of milliseconds?

---

### Post by mikewhatever on 2010-05-16
Weak passwords are just easier to guess or crack, so that, for example, if you have Remote Desktop enabled, a cracker could use it to get unauthorized access to your computer. Same goes for other password protected services, such as ssh, samba, or services not running locally, like an email or an online storage account. It should be noted that none of the services are enabled in Ubuntu by default, and also, I don't think that cracking a password and decrypting commercial DVDs is the same thing. 
Last but not least, iptables. It's there by default, but isn't engaged, so that it does not protect you. As said, by default, there is nothing there to protect, as no services are enabled.

---

### Post by quadproc on 2010-05-16
> **Ron O said:**
> The more I look into security, the more complicated it gets, and I'd like to be reasonably secure until I can study this. 

What are the real world implications of running a weak password on a single home system connected to the internet via DSL? 

Does your DSL modem include a firewall?

> Am I getting any protection from the iptables firewall out of the box with no further configuration?

How good are strong passwords anyway, when a brute force program like DVD decrypter can crack a protection scheme in a matter of milliseconds?

If your system is not a server and you have not enabled any of the services then your system will not be seen by the outside world.

Just for your information, you might be interested in reading about PGP and GPG.  Here is one place that I found interesting:[http://www.pgpi.org/doc/whypgp/en/](http://www.pgpi.org/doc/whypgp/en/)

Copy protection encryption is very different from robust encryption.

quadproc

---

### Post by -humanaut- on 2010-05-16
Just some advice on password creation take two license plate numbers you know and combined them with some Upper-case letters and you'll have a pretty decent easy to remember password for home use.

---

### Post by techunit on 2010-05-16
The best thing I have done for passwords it to use the serial code from a 5 dollar bill. I am sure that any bill will do but I find fives plenty ubiquitous and unlikely for it to be breached. That is what I believe is the easiest way to get easy to remember passwords. pass-phrases work well to if you are encrypting a volume and it requires you to have a ridiculously long password because of this I was able to remember a 64 character long password,

---

### Post by Ron O on 2010-05-16
Thanks all. Your responses were extremely helpful. My DSL goes through a local router which I guess is considered a firewall of sorts.

None of the services you listed are enabled on my system yet, as long as they were disabled by default. I DO plan to use a stronger password, but in a fresh install where I need root access so often to add packages etc., typing a long password over and over is tedious. Later, it will not be a problem.

---

### Post by techunit on 2010-05-16
Ubuntu is more secure because instead of saying 'yes' or 'no' to a question of root privileges you actually have to make an input making the process much more secure.

---

### Post by Oasu4g on 2010-05-16
apg and pwgen are two nice programs for creating secure passwords for you.

---

