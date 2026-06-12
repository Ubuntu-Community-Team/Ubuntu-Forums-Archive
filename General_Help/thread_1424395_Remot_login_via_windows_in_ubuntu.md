---
title: "Remot login via windows in ubuntu"
date: 2010-03-07
forum: General Help
---

### Post by suresh_vandiyur on 2010-03-07
how to remote login windows to ubuntu. what should be configure in ubuntu and what is the software used for remote login. please help me.

---

### Post by flippo on 2010-03-07
If your content with a terminal use putty ssh.

---

### Post by suresh_vandiyur on 2010-03-07
> **flippo said:**
> If your content with a terminal use putty ssh.
ya it is console mode. i need GUI mode. the GUI mode useful for me.please help me

---

### Post by flippo on 2010-03-07
Will X11 forwarding work for you, or do you need a full environment?

[http://www.linux-tip.net/cms/content/view/302/26/]("http://www.linux-tip.net/cms/content/view/302/26/")

---

### Post by suresh_vandiyur on 2010-03-07
> **flippo said:**
> Will X11 forwarding work for you, or do you need a full environment?

[http://www.linux-tip.net/cms/content/view/302/26/]("http://www.linux-tip.net/cms/content/view/302/26/")

Also, make sure that you have the following line in your /etc/ssh2/sshd2_config file: i dont i the this file. i have only the /etc/ssh/ssh_config. i edit the above mantione file forwarding x11 yes. start means it says unrecognized service. but in my ssh is working. i am connecting other linux machine thorugh ssh. please help me

---

