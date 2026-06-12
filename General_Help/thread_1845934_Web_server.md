---
title: "Web server"
date: 2011-09-18
forum: General Help
---

### Post by yushisune511 on 2011-09-18
1.I forward port 80(my web onserver) to port 8080(map out to on-ip) 
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://image.ohozaa.com/view/2kbpj%22%20target=%22_blank%22%3E%3Cimg%20border=%220%22%20src=%22http://image.ohozaa.com/i/670/dVERF.JPG%22%20/%3E%3C/a%3E[/IMG]
[IMG]http://image.ohozaa.com/view/2kbr7[/IMG][IMG]http://image.ohozaa.com/i/670/dVERF.JPG[/IMG]
[IMG]http://image.ohozaa.com/i/768/eEigz.JPG[/IMG]
2.I do iptable
sudo iptables -A OUTPUT -p udp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 80 -j ACCEPT
sudo iptables -A FORWARD -p udp --dport 80 -j ACCEPT

sudo iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A FORWARD -p tcp --dport 80 -j ACCEPT

but cann't see in the internet.

Thank you,Ake

---

