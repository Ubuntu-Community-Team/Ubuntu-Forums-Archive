---
title: "Computer randomly starts refusing SSH connections"
date: 2010-07-20
forum: General Help
---

### Post by Bradj47 on 2010-07-20
The ssh server is running Xubuntu 9.04. It was working before. Then I tried SSHing today and it gave me a **connection refused**. The computers I've tried SSHing from were running Ubuntu Netbook Remix 10.04, MacOS, and Solaris 10. None of them would connect. The ssh server is running the latest version of openssh-server (according to apt-get install). I'm assuming something in /etc/ssh/ got changed but I'm not sure. I can't figure out what's wrong.

---

### Post by stlsaint on 2010-07-20
Verify that your server has not had a ip change (unless you set static). Check your /etc/ssh/sshd_config on server to ensure your using correct authentication. Are you using keys or password for authentication? Also have you been toying with any type of firewall? ie: iptables, ufw, fail2ban, etc. 
Also look in your deny(host, allow) configs to ensure nothing has changed. View your logs of immediate time before you noticed you couldnt connect. Also it couldnt hurt to do a restart of all communitcation devices involved!;)

---

