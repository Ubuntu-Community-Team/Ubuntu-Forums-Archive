---
title: "Newb help with Email on Server"
date: 2010-03-27
forum: General Help
---

### Post by skeeterxb on 2010-03-27
I have two Ubuntu virtual machines, one is currently setup as the server the other as a client.  I only want to send mail between these two machines, i think i am doing something wrong.  I have installed exim4 onto both boxes for sending and recieving mail.  I am trying to use alpine to send the mail, i send locally to the box with no problems.  I have scoured the internet for any thoughts on this one, seems simple enough, both vms have static ip addressing, they can talk to each other fine.  
 
Please help. 
 
Thanks
Rob

---

### Post by skeeterxb on 2010-03-27
bump, any guidance would be helpful.

---

### Post by krismatth3 on 2010-03-27
Both VMs have to be able to find each other, either via DNS or static IP (or some other mechanism).

Email server wise: both machines have to have an MTA. See [https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer") for further guidance.

---

### Post by skeeterxb on 2010-03-27
Thanks for the quick reply, both do have static ip 
 
Server  192.168.20.2
Client    192.168.20.1
 
Both also have exim4 installed and configured as smarthost.  Is that the correct way to do it? Also not sure if i mentioned above, the machines will only be emailing each other, nothing in the outside world.  Is there anything in Alpine i need to configure on both machines in regards to settings, i am at a loss there.  Anything else you can provide would be great as i am getting my hands into this issue. 
 
Thanks

---

### Post by skeeterxb on 2010-03-28
bump please

---

