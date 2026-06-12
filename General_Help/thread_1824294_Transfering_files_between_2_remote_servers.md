---
title: "Transfering files between 2 remote servers?"
date: 2011-08-13
forum: General Help
---

### Post by Phixion on 2011-08-13
What can I use for this? 

I've tried FXP and rsync, none worked and I can't find much info on how to get them working, just alot of google results with people in the same situation as me!

I want to transfer files from 1 remote server to another remote server... a fairly easy task in which I'm sure there's an easy solution, I just can't find it.

Please help!

---

### Post by its_me_gb on 2011-08-13
Secure Copy (scp)

---

### Post by Phixion on 2011-08-13
Brilliant! That works, many thanks.

Do you know how it works exactly? These 2 servers are hosted in the same datacentre... would it copy via LAN or is it going over the Internet?

---

### Post by its_me_gb on 2011-08-13
that would depend on how you use it! if you supply it with the internal ip of the remote server, then it would be LAN, but if you give the wan ip of the remote server it would be over the internet.

[http://www.hypexr.org/linux_scp_help.php]("http://www.hypexr.org/linux_scp_help.php")

---

### Post by Phixion on 2011-08-13
Cool, all is working fine now thanks alot :)

---

