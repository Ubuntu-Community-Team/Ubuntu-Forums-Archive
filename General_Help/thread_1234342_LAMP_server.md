---
title: "LAMP server"
date: 2009-08-07
forum: General Help
---

### Post by sevol on 2009-08-07
Hi, I just installed lamp along with webmin on my laptop. the installations were all successful and working fine. however I want to be able to locally access the lamp server/webmin from my windows desktop. how would i be able to do this? i tried googling and and searching but just got a bigger  headache. thx for any help!!

---

### Post by blueridgedog on 2009-08-07
Assuming the two systems are on the same network, put the ip address of the lamp server in the browser address bar (followed by the path to the page you are trying to bring up).  

the webmin default is [https://localhost:10000/](https://localhost:10000/) so the the path on your network if the box had ip 192.168.1.2 would be [https://192.168.1.2:10000/](https://192.168.1.2:10000/)  (adjust for your actual IP)

---

### Post by llemm on 2009-08-07
> **blueridgedog said:**
> Assuming the two systems are on the same network, put the ip address of the lamp server in the browser address bar (followed by the path to the page you are trying to bring up).  

the webmin default is [https://localhost:10000/](https://localhost:10000/) so the the path on your network if the box had ip 192.168.1.2 would be [https://192.168.1.2:10000/](https://192.168.1.2:10000/)  (adjust for your actual IP)

if locally and terminally, you can use ssh. Install openssh-server on the LAMP and connect through it using putty or anything similar in your windows desktop.

If you want to use the internet or what I mean youre in a different site I think you should use vpn. Hamachi or openvpn can help you with that.

HTH

---

### Post by sevol on 2009-08-30
Thx for the replies and help. I have solved the problem. Sorry for the late response.. once again thanks for your help.

---

