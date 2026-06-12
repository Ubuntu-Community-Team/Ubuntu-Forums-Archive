---
title: "Connecting to a remote computer Linux to Windows"
date: 2006-05-24
forum: General Help
---

### Post by cobbweb on 2006-05-24
Hey, 
  I wanted to connect from my schools computer to my computer at home using what I believe is called ssh? Not sure how it works all that much but I saw the leader of my Ubuntu Community do it and though it was pretty neat. Anyway, If I am on a Linux Box and am trying to connect to a windows box, how would  I go about doing this? Plus I kind of wanna freak my mom out...hehe... 

 Cobbweb

---

### Post by cskeide on 2006-05-25
You would have to install an ssh server on the windows computer. Check out this website: [http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

The command to connect from linux is: ssh username@hostname/ipaddress. So for example if I want to connect as user ubuntu to a computer with ip 192.168.0.123, use the following command:
```
ssh ubuntu@192.168.0.123
```

---

### Post by nanotube on 2006-05-25
but... note that with ssh on win, you wont be able to remotely control the comp or anything. for that, you need either vnc, or freenx.

---

