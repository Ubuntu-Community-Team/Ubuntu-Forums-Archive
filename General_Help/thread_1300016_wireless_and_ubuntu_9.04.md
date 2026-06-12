---
title: "wireless and ubuntu 9.04"
date: 2009-10-24
forum: General Help
---

### Post by mulder5_uk on 2009-10-24
I have just converted to ubuntu. When I installed ubuntu first time wireless internet worked on my laptop for few days then it stopped. I tried all sorts of codes in the help content. Nothing works. I even reinstalled ubuntu 9.04. Still didn't work. It does estabilsh the connection with the dlink router- but when I open firefox, it does't connect with the internet. Has anyone got an answer?

---

### Post by mikewhatever on 2009-10-24
Some info about your wireless hardware would have been useful. Can you post the outputs of the following from Terminal:

ifconfig

sudo lshw -C network

cat /etc/resolve.conf

What you describe seems to ba a dns problem. Have you entered anything into dns field in the network settings?

---

