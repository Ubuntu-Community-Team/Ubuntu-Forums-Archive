---
title: "SSH into Guest OS if Virtualbox"
date: 2012-09-10
forum: General Help
---

### Post by jkossis on 2012-09-10
I have Ubuntu 12.04 running Oracle's VirtualBox 4.1.12. The guest OS is Minix3. openSSH has been installed on minix3, but I am having a hard time trying to ssh into Minix's file system. I want to be able to use Eclipse's remote system explorer and therefore need to figure out this communication issue. I appreciate any help!

---

### Post by Cheesemill on 2012-09-10
How did you set up networking for the Guest OS?

If you set it to bridged mode then you can just SSH using the guests IP address.

---

### Post by mevun on 2012-09-10
I think if you are not using bridged mode, then you have to map port numbers in the virtual box configuration.  I can't remember if the server in the guest OS had to use that map number or if it is just the client.

---

### Post by jkossis on 2012-09-10
I am not sure how to forward the ports. Any idea of how to do this within Virtualbox? Things like which ports to use. Thanks for the help!

---

